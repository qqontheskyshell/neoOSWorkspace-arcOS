```markdown
kumaDevice
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

kumaWDS@arcOS
    └── SecureShellPolicy
    ├── Transport
    │   └── SSH
    │       ├── encrypted_channel
    │       ├── host_key_verification
    │       └── public_key_authentication
    │
    ├── Cryptography
    │   └── PostQuantumCryptography
    │       ├── key_exchange → ML-KEM
    │       ├── signatures   → ML-DSA
    │       └── hybrid_mode  → classical + PQC
    │
    ├── AccessControl
    │   ├── least_privilege
    │   ├── MFA
    │   ├── key_rotation
    │   └── session_timeout
    │
    └── Audit
        ├── authentication_log
        ├── session_log
        └── security_event_log
```

### kumaDeviceForWDS
```markdown
chunsikQ@arcOS
└── kumaDeviceForWDS-QQ_WHT_IPHONE_17e,QQ_ORNG_PRO,QQ_BLK_IPAD_PRO
    └── CoreTelephony@arcOS
        ├── PhysicalSIM
        │   ├── configuration → OS/carrier-managed
        │   └── destructive_ROM_delete → DENY
        │
        ├── RFResearch
        │   └── resonanceFreq
        │       ├── observation_only
        │       ├── measurement_data
        │       └── no_hardware_modification
        │
        └── SecurityPolicy
            ├── preserve_boot_integrity
            ├── preserve_SecureEnclave
            ├── preserve_iBoot
            └── authorized_configuration_only
        └── iOSPrivacyPolicy
            ├── FaceID
            │   ├── device_authentication → ENABLE
            │   └── app_authentication → ENABLE_WHEN_SUPPORTED
            │
            └── FacePrivacy
                ├── supported_iOS_apps → HIDE/BLUR_FACE_WHEN_SUPPORTED
                ├── screenshots/screen_recording → APP_POLICY
                ├── camera_access → USER_PERMISSION_REQUIRED
                └── unauthorized_face_capture → BLOCK
 
 
 
 
QQ_ORNG_PRO
└─ satMode
   ├─ mode: SIMULATION
   ├─ satellite_data: READ_ONLY
   ├─ sensor_control: OFF
   ├─ drone_control: SIMULATED
   ├─ human_targeting: OFF
   ├─ synthetic_targeting: ON
   └─ safety_boundary: ON
   
   QQ_WHT_IPHONE_17e
└─ cellMode
   ├─ mode: SIMULATION
   ├─ satellite_data: READ_ONLY
   ├─ sensor_control: SIMULATED
   ├─ drone_control: SIMULATED
   ├─ human_targeting: OFF
   ├─ synthetic_targeting: ON
   └─ safety_boundary: ON
   
   
   QQ_BLK_IPAD_PRO
└─ cellMode
   ├─ mode: SIMULATION
   ├─ satellite_data: SIM_READ_WRITE
   ├─ sensor_control: OFF
   ├─ drone_control: SIMULATED
   ├─ human_targeting: OFF
   └─ safety_boundary: ON
   
   
```       
### boot order
```markdown
BOOT
  → verified iBoot
  → Secure Enclave authorization
  → kumaDevice
  → arcOS
```