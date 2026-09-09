```markdown
kumaDeviceForWDS
│
├── BootPolicy@arcOS
│   │
│   ├── PowerOn
│   │    ↓
│   │  Boot ROM
│   │    ↓
│   │  iBoot
│   │    ├── VERIFY
│   │    ├── AUTHENTICATE
│   │    │      └── arcOSID="masterID"
│   │    └── HANDOFF
│   │
│   ├── Secure Enclave
│   │    ├── secure_identity
│   │    ├── key_protection
│   │    └── authorization
│   │
│   └── arcOS
│       └── Controlled Interfaces
│           ├── ALLOW → authenticated_path
│           └── DENY  → unauthorized_path
│
├── RF Security
│   └── iPhone Pro RF Security Research
│       └── randomizeRFAlgorithm@arcOS
│           │
│           ├── Hardware
│           │   ├── antenna_path
│           │   ├── RF_front_end
│           │   ├── filters
│           │   ├── oscillator_clock
│           │   └── resonant_behavior
│           │
│           ├── Wireless
│           │   ├── cellular
│           │   ├── Wi-Fi
│           │   ├── Bluetooth
│           │   └── UWB
│           │
│           ├── Measurement
│           │   ├── spectrum_observation
│           │   ├── frequency_response
│           │   ├── amplitude_response
│           │   ├── bandwidth
│           │   └── repeatability
│           │
│           └── SecurityConclusion
│               ├── expected_RF_behavior
│               ├── anomalous_behavior
│               ├── reproducible_vulnerability
│               └── evidence_required
│
└── PacketCaptureDefense
    │
    ├── Detect
    │   ├── authorized_capture
    │   ├── unknown_capture
    │   └── suspicious_capture
    │
    ├── Identify
    │   ├── device_id
    │   ├── source_ip
    │   └── capture_interface
    │
    ├── Protect
    │   ├── revoke_unauthorized_access
    │   ├── rotate_credentials
    │   ├── isolate_authorized_network_segment
    │   └── preserve_evidence
    │
    └── Audit
        └── immutable_local_log
```


### boot order
```markdown
BOOT
  → verified iBoot
  → Secure Enclave authorization
  → kumaDeviceForWDS
  → arcOS
```