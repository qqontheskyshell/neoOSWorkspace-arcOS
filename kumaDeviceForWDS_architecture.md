```markdown
kumaDeviceForWDS
	└── BootPolicy@arcOS
	    │
	    ├── PowerOn
	    │    ↓
	    │  Boot ROM
	    │    ↓
	    │  iBoot
	    │    ├── VERIFY
	    │    ├── AUTHENTICATE
	    │    └── HANDOFF
	    │
	    ├── Secure Enclave
	    │    ├── secure_identity
	    │    ├── key_protection
	    │    └── authorization
	    │
	    └── arcOS
	         └── Controlled Interfaces
	              ├── ALLOW → authenticated path
	              └── DENY  → unauthorized path
	              
	└──RF Security 
			└──	iPhone Pro RF Security Research > randomizeRFAlgorithm@arcOS
				│
				├── Hardware
				│   ├── antenna path
				│   ├── RF front-end
				│   ├── filters
				│   ├── oscillator / clock
				│   └── resonant behavior
				│
				├── Wireless
				│   ├── cellular
				│   ├── Wi-Fi
				│   ├── Bluetooth
				│   └── UWB
				│
				├── Measurement
				│   ├── spectrum observation
				│   ├── frequency response
				│   ├── amplitude response
				│   ├── bandwidth
				│   └── repeatability
				│
				└── Security conclusion
				    ├── expected RF behavior
				    ├── anomalous behavior
				    ├── reproducible vulnerability
				    └── evidence required
		    └── PacketCaptureDefense
		        ├── detect
		        │   ├── authorized_capture
		        │   ├── unknown_capture
		        │   └── suspicious_capture
		        │
		        ├── identify
		        │   ├── device_id
		        │   ├── source_ip
		        │   └── capture_interface
		        │
		        ├── protect
		        │   ├── revoke_unauthorized_access
		        │   ├── rotate_credentials
		        │   ├── isolate_authorized_network_segment
		        │   └── preserve_evidence
		        │
		        └── audit
		            └── immutable_local_log
```