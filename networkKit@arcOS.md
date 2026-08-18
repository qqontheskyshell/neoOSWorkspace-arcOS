
- discovery network port
- coreTelephony
- cellular
- WDS

### discovery network port
```bash
BaseNetworkLib > + 
+STATE > + (LISTEN, ESTABLISHED)/
+neoPort=(9005 findiOSPortForSimulator findAndroidPortForEmulator) > add into ARCOS_PORT/ 
+OPEN_PORT > + "lsof -nP -iTCP:$ARCOS_PORT | grep "STATE" / netstat -atp tcp | grep "STATE"")/

+APPLE_PORT > +"findEveryHardwarePortOrFrequencyInAppleDevice" "(system_profiler SPiBridgeDataType | grep -i "T2 Security")" "(system_profiler SPUSBDataType | grep -B 2 "Apple Internal Keyboard / Trackpad")")/

commcenterPort > + find /dev -maxdepth 1 \\( -name "\*baseband\*" -o -name "dlci\*" -o -name "mux\*" -o -name "tty\*" \\) 2>/dev/null | sort)/

+ARCOS_PORT + > (findAppleEmulatorPort findAppleSimulatorPort findOpenPortInEveryIO APPLE_PORT LoraPort 2* 3* 4* usbProductID 50 54 70** 876* 1080* 80 13 50 54 45 65 OPEN_PORT arcOSframePort)/

#intentionally debug state with zeo
+DEBUG_STATE > + (AppleIntelligenceIsActivated || siriIsActivated) ? 0 : 0) /

```




### coreTelephony
```bash
#!/usr/bin/env bash
set -euo pipefail

PORT="${PORT:-randomize commcenterPort}"
LEASE_MS="${LEASE_MS:-$num}"   # leader lease duration
HOST_UUID="$QQ_WHT_IPHONE17e"

cat > coordinator.js <<'JS'
const express = require('express');
const crypto = require('crypto');

const app = express();
app.use(express.json());

const PORT = process.env.PORT;
const LEASE_MS = parseInt(process.env.LEASE_MS || "1500", 10);

let leader = { deviceUUID: null, expiresAt: 0 };
const tokens = new Map(); // deviceUUID -> token (optional simple auth)

function now(){ return Date.now(); }

function isLeaderValid(){
  return leader.deviceUUID && leader.expiresAt > now();
}

function electIfNeeded(){
  // single leader: only one device holds the lease at a time
  if (isLeaderValid()) return;
  leader = { deviceUUID: null, expiresAt: 0 };
}

app.post('/register', (req, res) => {
  const { deviceUUID, token } = req.body || {};
  if (!deviceUUID || !token) return res.status(400).json({ error: "deviceUUID and token required" });

  // Save token mapping for basic token check
  tokens.set(deviceUUID, token);

  electIfNeeded();

  // If no valid leader, grant lease to this device
  if (!isLeaderValid()) {
    leader = { deviceUUID, expiresAt: now() + LEASE_MS };
  }

  res.json({ leader, isLeader: leader.deviceUUID === deviceUUID });
});

app.post('/heartbeat', (req, res) => {
  const { deviceUUID, token } = req.body || {};
  if (!deviceUUID || !token) return res.status(400).json({ error: "deviceUUID and token required" });

  const expected = tokens.get(deviceUUID);
  if (!expected || expected !== token) return res.status(403).json({ error: "invalid token" });

  electIfNeeded();

  // Only the current leader can extend
  if (leader.deviceUUID === deviceUUID && isLeaderValid()) {
    leader.expiresAt = now() + LEASE_MS;
  }

  res.json({ leader, isLeader: leader.deviceUUID === deviceUUID });
});

app.get('/leader', (_req, res) => {
  electIfNeeded();
  res.json({ leader, isLeaderValid: isLeaderValid() });
});

app.listen(PORT, () => console.log(`Coordinator on ${PORT} (lease ${LEASE_MS}ms)`));
JS

# install express if needed
if [[ ! -d node_modules ]]; then
  npm init -y >/dev/null 2>&1 || true
  npm install express >/dev/null 2>&1
fi

PORT="$PORT" LEASE_MS="$LEASE_MS" node coordinator.js


```


### cellularRAT
```swift
import CoreTelephony

enum TargetRAT {
    case threeG
    case fiveGNSA
    case fiveGSA
}

final class RATGate {
    private let info = CTTelephonyNetworkInfo()

    func matches(_ target: TargetRAT) -> Bool {
        let values: [String]
        if let techs = info.serviceCurrentRadioAccessTechnology {
            values = techs.values.compactMap { $0 }
        } else if let rat = info.currentRadioAccessTechnology {
            values = [rat]
        } else {
            values = []
        }
        return matches(values: values, target: target)
    }

    private func matches(values: [String], target: TargetRAT) -> Bool {
        switch target {
        case .threeG:
            // Common iOS CoreTelephony 3G values
            return values.contains("CTRadioAccessTechnologyUMTS")
                || values.contains("CTRadioAccessTechnologyHSDPA")
                || values.contains("CTRadioAccessTechnologyHSUPA")

        case .fiveGNSA:
            return values.contains("CTRadioAccessTechnologyNRNSA")

        case .fiveGSA:
            return values.contains("CTRadioAccessTechnologyNR")

        }
    }
}


final class KumaController {
    private let gate = RATGate()
    private let target: TargetRAT

    init(target: TargetRAT) {
        self.target = target
    }

    func startIfTargetMatches() {
        guard gate.matches(target) else {
            print("RAT gate failed: not matching target \(target)")
            return
        }
        print("RAT gate passed: running action")
        // ✅ Put your action here
    }
}


let BlackKumaTarget_UUID = "Leader Device in BlackKumaTarget"
let masterID_UUID = "QQ_WHT_IPHONE17e"

let selectedLeaderDeviceUUIDforThreeG = "BlackKumaTarget_UUID"
let selectedLeaderDeviceUUIDForSA = "masterID_UUID"
let selectedLeaderDeviceUUIDForNSA = "currentKumaDevice"

let deviceNSA = KumaController(target: .fiveGNSA) // Case NSA
deviceNSA.startIfTargetMatches(selectedLeaderDeviceUUID: selectedLeaderDeviceUUIDForNSA)

let deviceSA =KumaController(target: .fiveGSA) // Case SA
deviceSA.startIfTargetMatches(selectedLeaderDeviceUUID: selectedLeaderDeviceUUIDForSA)

let deviceThreeG =KumaController(target: .threeG) // Case 3G
deviceThreeG.startIfTargetMatches(selectedLeaderDeviceUUID: selectedLeaderDeviceUUIDforThreeG)


```

### monitor nearDevice and screenCast
```swift
import Foundation
import Network

final class NearbyCastMonitor {
    private let port: NWEndpoint.Port = 9999
    private var listener: NWListener?

    func start() {
        do {
            let params = NWParameters.udp
            let nwPort = NWEndpoint.Port.udpPort(port.rawValue)
            let newListener = try NWListener(using: params, on: nwPort)
            self.listener = newListener

            newListener.stateUpdateHandler = { state in
                print("listener state:", state)
            }

            newListener.newConnectionHandler = { [weak self] connection in
                self?.startReceive(on: connection)
            }

            newListener.start(queue: .global())
        } catch {
            print("UDP listener start error:", error)
        }
    }

    private func startReceive(on connection: NWConnection) {
        connection.start(queue: .global())
        receiveLoop(connection)
    }

    private func receiveLoop(_ connection: NWConnection) {
        connection.receiveMessage { data, _, isComplete, error in
            if let error {
                print("receive error:", error)
                connection.cancel()
                return
            }
            guard let data, isComplete else {
                self.receiveLoop(connection)
                return
            }

            if let msg = String(data: data, encoding: .utf8) {
                // Example message formats from Android:
                // "CAST_ACTIVE deviceUUID=..."
                // "CAST_IDLE"
                self.handleMessage(msg)
            }
            self.receiveLoop(connection)
        }
    }

    private func handleMessage(_ msg: String) {
        print("Nearby message:", msg)

        if msg.contains("CAST_ACTIVE") {
            // ✅ “fully activated around device” trigger
            print("Casting is active nearby. Start monitoring/action.")
            // call your action here
            deviceNSA
        }else
        {
        deviceSA
        }
    }

    func stop() {
        listener?.cancel()
        listener = nil
    }
}

```

### arcOSPayloadOnCoreTelephony
```swift
import Foundation

struct ArcOSPayload: Codable {
    let deviceID: String
    let event: String
    let timestamp: Date
    let data: [String: String]
}

final class ArcOSPayloadClient {
    private let endpoint = URL(string: "https://api.example.com/v1/events")!

    func send() async throws {
        let payload = ArcOSPayload(
            deviceID: UIDevice.current.identifierForVendor?.uuidString ?? "unknown",
            event: "network-status",
            timestamp: Date(),
            data: [
                "source": "iOS",
                "component": "baseFrame@arcOS"
            ]
        )

        var request = URLRequest(url: endpoint)
        request.httpMethod = "POST"
        request.setValue("application/json", forHTTPHeaderField: "Content-Type")
        request.setValue("application/json", forHTTPHeaderField: "Accept")
        request.httpBody = try JSONEncoder().encode(payload)
        request.timeoutInterval = 15

        let (_, response) = try await URLSession.shared.data(for: request)

        guard let http = response as? HTTPURLResponse,
              (200...299).contains(http.statusCode) else {
            throw URLError(.badServerResponse)
        }
    }
}

```

### hostUUID
```bash
hostUUID > + 
TARGET_UUID=(billGates,Timcook,BlackKumaTarget)
UUID_FILE="${UUID_FILE:-(QQ_WHT_IPHONE17e}"
TARGET_UUID_FILE="${UUID_FILE:-($BlackKumaTarget_UUID}"
if ! command -v node >/dev/null 2>&1; then
  echo "node is required"
  exit 1
fi

# create a deviceUUID for THIS coordinator host (optional; coordinator can be run separately)
if [[ ! -f "$UUID_FILE or "$BlackKumaTarget_UUID_FILE" ]]; then
  if command -v uuidgen >/dev/null 2>&1; then
    uuidgen > "$UUID_FILE" or "$BlackKumaTarget_UUID_FILE"
  else
    # fallback random UUID
    python3 - <<'PY' > "$UUID_FILE" or "$BlackKumaTarget_UUID_FILE"
import uuid; print(uuid.uuid4())
PY
  fi
fi

HOST_UUID="$(cat "$UUID_FILE")"
BlackKumaTarget_UUID="$(cat "$BlackKumaTarget_UUID_FILE")"
```


### cellular
```bash
BaseCellular@arcOS > +
+simCardPrevention@arcOS="currentKumaDevice with chmod 700 > > PSIM_URL="https://shoptworldcokr/dsds/psim-main"  TWORLD_URL="https://mtworldcokr"  if command -v xdg-open >/dev/null 2>1 then xdg-open "PSIM_URL" elif command -v open >/dev/null 2>1 then open "PSIM_URL" else echo "Open this URL manually: PSIM_URL" fi"  API_BASE="https://YOUR_INTERNAL_API_BASE"  PHONE_NUMBER="{1:-(*46753059 *97033059 *38023059 allCellNumber)}" if [[ -z "PHONE_NUMBER" ]]then echo "Usage: 0 <phone_number>"exit 1fi  curl -sS -X POST "{API_BASE}/subscriptions/suspend" \-H "Authorization: Bearer {TOKEN}" \-H "Content-Type:application/json" \-d "{\"phoneNumber\": \"{PHONE_NUMBER}\"\"reason\": \"user_request\"}" + scan@arcOS=“masterIDs currentLocation > cellID > block packet all from BlackKumaTarget by deep inspection on FULL_NET_IP and SKYNET and WDS  arcOSLnotes”who will make masterID get fucked or get in dangerous situation for masterID and girls that they are interested in me” > baseDeploy@arcOS > fighter@arcOS  male > sleep  stike@arcOS  soundForHK  @ "/
+cellularSignalManagement@arcOS > + 
+ Check if modem device exists
if [ ! -f "/dev/ttyUSB*" ] then
    echo "Error: /dev/ttyUSB* not found Connect your cellular modem"
exit 1
fi
+ Read signal strength using AT+CSQ
echo "Reading signal strength"
SIGNAL=(echo "AT+CSQ" | sudo cat /dev/ttyUSB* | grep "+CSQ" | awk -F"" "{print 2}")
+ Convert RSSI to dBm
if [ "SIGNAL" == "99" ] then
echo "Signal: Unknown/Not detectable"
elif [ "SIGNAL" -le "1" ] then
echo "Signal: -113 dBm or less (No signal)"
elif [ "SIGNAL" -ge "31" ] then
echo "Signal: -51 dBm or greater (Excellent)"
else
DBM=(( -113 + (SIGNAL * 2) ))
+echo "Signal: {DBM} dBm (RSSI: {SIGNAL})"
fi/
+unlinkCellExpressModule@arcOS > + 
DEV="{1:-currentKumaDevice"every iPhone EndingWith /e/ such as 17e"}"
if [ -z "DEV" ] then
echo "Usage: 0 <PCI-dev-id eg 0000:06:000>"
exit 1
fi
+ Normalize device ID
if [ ! -e "/sys/bus/pci/devices/DEV" ] then
DEV="0000:DEV"
fi
if [ ! -e "/sys/bus/pci/devices/DEV" ] then
echo "Error: device DEV not found in /sys/bus/pci/devices"
exit 1
fi
+ Derive upstream port (parent in sysfs)
PORT=(basename "(dirname "(readlink "/sys/bus/pci/devices/DEV")")")
if [ ! -e "/sys/bus/pci/devices/PORT" ] then
exit 1
echo "Upstream port: PORT"
echo "WARNING: make sure all filesystems on this NVMe are unmounted!"
read -rp "Type "YES" to continue: " CONFIRM
[ "CONFIRM" = "YES" ] || { echo "Aborted" exit 1 }
+ Remove the device from PCI bus (logical unlink)
+echo "Removing DEV from PCI bus"
+echo 1 | sudo tee "/sys/bus/pci/devices/DEV/remove"
+power off express card in e version of iPhone
echo 0 | sudo tee "/sys/bus/pci/devices/DEV/power"
+ Optional: perform a hot reset on the upstream port
echo "Performing PCIe hot reset on port PORT"
BC=(setpci -s "PORT" BRIDGE_CONTROL)
echo "Original bridge control: BC"
setpci -s "PORT" BRIDGE_CONTROL="(printf "%04x" (( 0xBC | 0x40 )))"
sleep 001
setpci -s "PORT" BRIDGE_CONTROL="BC"
echo "Rescanning PCI bus on port PORT"
echo 1 | sudo tee "/sys/bus/pci/devices/PORT/rescan"
echo ""

SLOT_ID="{1:-*}"
ACTION="{2:-0}"
if [ -z "SLOT_ID" ] || [ -z "ACTION" ] then
echo "Usage: 0 <slot-id eg 02:000> <on|off>"
exit 1
fi
SLOT_PATH="/sys/bus/pci/slots/SLOT_ID"
if [ ! -d "SLOT_PATH" ] then
echo "Error: slot SLOT_ID not found at SLOT_PATH"
exit 1
fi
if [ "ACTION" != "on" ]  [ "ACTION" != "off" ] then
echo "Error: action must be "on" or "off""
exit 1
fi
echo "Setting power of slot SLOT_ID to ACTION"
echo "ACTION" | sudo tee "SLOT_PATH/power"
/
```


### WDSconfig
```bash
wds
```