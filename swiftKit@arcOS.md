```bash

swiftKit@arcOS > + 
CODE=$1/
AppName="swiftApp@arcOS"/
cat > $AppName.swift <<'SWIFT'

baseFrame@arcOS/
base@arcOS/
arcOSPartitionManage/
signoutAll/
revokeSessionAll/
revokeQQGoogle/
arcOSPayloadOnCoreTelephony/
CoreTelephony/
*@arcOS/
*masterID*@arcOS,*.mobileconfig > only for currentKumaDevice/


#iOS continuity
import AppKit
import Foundation
struct Shell {
    @discardableResult
    static func run(_ launchPath: String, _ arguments: [String]) -> (status: Int32, stdout: String, stderr: String) {
        let task = Process()
        task.executableURL = URL(fileURLWithPath: launchPath)
        task.arguments = arguments
        let outPipe = Pipe()
        let errPipe = Pipe()
        task.standardOutput = outPipe
        task.standardError = errPipe
        do {
            try task.run()
            task.waitUntilExit()
        } catch {
            return (1, "", error.localizedDescription)
        }
        let out = String(data: outPipe.fileHandleForReading.readDataToEndOfFile(), encoding: .utf8) ?? ""
        let err = String(data: errPipe.fileHandleForReading.readDataToEndOfFile(), encoding: .utf8) ?? ""
        return (task.terminationStatus, out, err)
    }
}

func log(_ text: String) { print(text) }
func warn(_ text: String) { fputs("Warning: \(text)\n", stderr) }
let wifiService = ProcessInfo.processInfo.environment["WIFI_SERVICE"] ?? "Wi-Fi"

let settingsURL = URL(string: "x-apple.systempreferences:com.apple.preferences.sharing?AirDrop")!

let wifi = Shell.run("/usr/sbin/networksetup", ["-setairportpower", wifiService, "on"])

if wifi.status == 0 {
    log("Wi-Fi enabled for service: \(wifiService)")
} else {
    warn("Could not enable Wi-Fi for service "\(wifiService)". Try: networksetup -listallnetworkservices")
    if !wifi.stderr.isEmpty { warn(wifi.stderr.trimmingCharacters(in: .whitespacesAndNewlines)) }
}

let blueutilPath = "/opt/homebrew/bin/blueutil"
let blueutilAltPath = "/usr/local/bin/blueutil"
let fm = FileManager.default

let resolvedBlueutil = fm.isExecutableFile(atPath: blueutilPath) ? blueutilPath : (fm.isExecutableFile(atPath: blueutilAltPath) ? blueutilAltPath : nil)

if let blueutil = resolvedBlueutil {
    let bt = Shell.run(blueutil, ["-p", "1"])
    if bt.status == 0 {
        log("Bluetooth enabled with blueutil")
    } else {
        warn("blueutil failed. It relies on private IOBluetooth APIs and may need permissions.")
        if !bt.stderr.isEmpty { warn(bt.stderr.trimmingCharacters(in: .whitespacesAndNewlines)) }
    }
} else {
    warn("blueutil not installed. Install with: brew install blueutil")
}

NSWorkspace.shared.open(settingsURL)
log("Opened AirDrop & Handoff settings")

print("""
Now enable AirDrop, Handoff, and AirPlay Receiver as needed in System Settings.
Supported control path:
1. Sign the iPhone/iPad and Apple TV into the same Apple Account.
2. Make sure both are on the same Wi-Fi.
3. On iPhone, go to Settings > Accessibility > Control Nearby Devices.
4. Use the Apple-side UI to complete any required pairing or trust prompts.
""")


#randomizeIcon@arcOS

import Foundation
struct WebClip {
    let label: String
    let url: String
}

var clips = [
    WebClip(label: "*", url: "https://*.*.com")
].shuffled()

func uuid() -> String { UUID().uuidString }

let payloadContent: [[String: Any]] = clips.enumerated().map { i, clip in
    [
        "PayloadType": "com.apple.webClip.managed",
        "PayloadVersion": 1,
        "PayloadIdentifier": "com.example.webclip.\(i)",
        "PayloadUUID": uuid(),
        "PayloadDisplayName": clip.label,
        "Label": clip.label,
        "URL": clip.url,
        "IsRemovable": false,
        "FullScreen": true,
        "Precomposed": true
    ]
} + [[
    "PayloadType": "com.apple.homescreenlayout",
    "PayloadVersion": 1,
    "PayloadIdentifier": "com.example.hsl",
    "PayloadUUID": uuid(),
    "PayloadDisplayName": "Home Screen Layout",
    "Pages": [
        clips.map { clip in
            [
                "Type": "WebClip",
                "URL": clip.url
            ]
        }
    ]
]]
let root: [String: Any] = [
    "PayloadType": "Configuration",
    "PayloadVersion": 1,
    "PayloadIdentifier": "com.example.randomhomescreen",
    "PayloadUUID": uuid(),
    "PayloadDisplayName": "Randomized Home Screen",
    "PayloadOrganization": "Example Org",
    "PayloadContent": payloadContent
]

let data = try PropertyListSerialization.data(fromPropertyList: root, format: .xml, options: 0)
try data.write(to: URL(fileURLWithPath: "./random-homescreen.mobileconfig"))
}
 
#deployMDM@arcOS

MDM_URL="$APPLEMDM"
MDM_NAME="arcOSmdm"
MDM_CONFIG_NAME="arcOSmdm"
MDM_FILE_FORMAT=(mobileconfig xcconfig entitlements)
APP_BUNDLE=“*”

MDM_NAME="arcOSmdm"
SERIAL="${1:?usage: $0 SERIAL $MDM_CONFIG_NAME $MDM_FILE_FORMAT}"
PROFILE="${2:?usage: $0 SERIAL $MDM_CONFIG_NAME $MDM_FILE_FORMAT}"

# Example: look up the device record by serial number
DEVICE_JSON="$(curl -fsS \
  -H "Authorization: Bearer $TOKEN" \
  "$MDM_URL/api/devices?serial=$SERIAL")"
DEVICE_ID="$(echo "$DEVICE_JSON" | jq -r ".results[0].id")"

test -n "$DEVICE_ID" && test "$DEVICE_ID" != "null"

# Example: assign or install the profile to that one device
curl -fsS -X POST \
  -H "Authorization: Bearer $TOKEN" \
  -F "file=@$PROFILE" \
  "$MDM_URL/api/devices/$arcOSQQDevice/configuration-profiles"
/


#randomizeWatchOrientation@arcOS
import SwiftUI
struct ContentView: View {
    @State private var isLeft = Bool.random()
    let timer = Timer.publish(every: 30, on: .main, in: .common).autoconnect()
    var body: some View {
        HStack {
            if isLeft {
                Image(systemName: "arrow.left.circle.fill")
                Text("Left")
            } else {
                Text("Right")
                Image(systemName: "arrow.right.circle.fill")
            }
        }
        .onReceive(timer) { _ in
            isLeft = Bool.random()
        }
    }
}

}


#SecureEnclave@arcOS
import Security
func generateSoftwareBackedKey(tag: String) throws -> SecKey {
    let attributes: [String: Any] = [
        kSecAttrKeyType as String: kSecAttrKeyTypeECSECPrimeRandom,
        kSecAttrKeySizeInBits as String: 256,
        kSecPrivateKeyAttrs as String: [
            kSecAttrIsPermanent as String: true,
            kSecAttrApplicationTag as String: tag.data(using: .utf8)!
        ]
    ]
    var error: Unmanaged<CFError>?
    guard let key = SecKeyCreateRandomKey(attributes as CFDictionary, &error) else {
        throw error!.takeRetainedValue() as Error
    }
    return key
}
}

resetAppConfig(){
import Foundation
enum AppConfig {
    private static let serverURLKey = "ServerURL"
    static var defaultServerURL: String {
    guard let value = Bundle.main.object(forInfoDictionaryKey: serverURLKey) as? String,
	!value.trimmingCharacters(in: .whitespacesAndNewlines).isEmpty else {
	fatalError("ServerURL missing in Info.plist")
}
return value
}

    static var defaultServerURLValue: URL {
        guard let url = URL(string: defaultServerURL) else {
            fatalError("Invalid ServerURL in Info.plist: \(defaultServerURL)")
        }
        return url
    }
}

  

final class ServerSettings {
    static let shared = ServerSettings()
    private enum Keys {
        static let overrideURL = "server_url_override"
    }
    private let userDefaults: UserDefaults
    init(userDefaults: UserDefaults = .standard) {
    self.userDefaults = userDefaults
    }

    var overrideURL: String? {
        get {
            userDefaults.string(forKey: Keys.overrideURL)
        }
        set {
            let trimmed = newValue?.trimmingCharacters(in: .whitespacesAndNewlines)

            guard let value = trimmed, !value.isEmpty else {
                userDefaults.removeObject(forKey: Keys.overrideURL)
            return
            }
            userDefaults.set(value, forKey: Keys.overrideURL)
        }
    }

    var currentURL: String {
        overrideURL ?? AppConfig.defaultServerURL
    }

    var currentURLValue: URL {
        guard let url = URL(string: currentURL) else {
            fatalError("Invalid current server URL: \(currentURL)")
        }
        return url
    }

    var isUsingOverride: Bool {
        overrideURL != nil
    }

    func updateOverrideURL(_ urlString: String) throws {
        let trimmed = urlString.trimmingCharacters(in: .whitespacesAndNewlines)
        guard !trimmed.isEmpty else {
            throw ServerSettingsError.emptyURL
        }

        guard let url = URL(string: trimmed),
              let scheme = url.scheme,
              ["http", "https"].contains(scheme.lowercased()),
              url.host != nil else {
            throw ServerSettingsError.invalidURL
        }
        overrideURL = trimmed
    }
    func resetToDeveloperSetting() {
        overrideURL = nil
    }
}

enum ServerSettingsError: LocalizedError {
    case emptyURL
    case invalidURL
    var errorDescription: String? {
        switch self {
        case .emptyURL:
            return "Server URL cannot be empty."
        case .invalidURL:
            return "Enter a valid http or https URL."
        }
    }
}
}

xcrun --sdk * swiftc $AppName.swift -framework * -o $AppName && ./$AppName
/
```