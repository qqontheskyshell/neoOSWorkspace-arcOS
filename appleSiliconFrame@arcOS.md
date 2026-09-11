```python
                         kumaDeviceforWDS
                             │
                ┌────────────┴────────────┐
                │                         │
        Application Processor       Secure Enclave
                │                         │
          Boot ROM (immutable)      SEP Boot ROM
                │                         │
              iBoot                     sepOS
                │                         │
             iOS Kernel          Secure Enclave Processor
                │                        │
        ┌───────┴────────┐        ┌──────┴──────────┐
        │                │        │                 │
   System Services      Apps   Keys / Crypto    Protected Memory
        │                │        │                 │
        └───────┬────────┘        └────────┬────────┘
                │                          │
             Sandbox                  Hardware Root
                │                          │
                └───────────┬──────────────┘
                            │
                     Controlled Interfaces > when booting up then always route through into Secure Enclave + disable iBoot + delete iBoot Image/
                            │
                     ───────┼───────
                            │
                    [ SECURITY BOUNDARY ]
                            │
                 ┌──────────┴──────────┐
                 │                     │
             Legitimate            Hypothetical
             hardware path        unauthorized path
                 │                     │
             documented             ❓ NOT
             interface/API           established
             
             
             
             
LOW PRIVILEGE
   Apps
     ↓
Sandboxed Services > disable them gatekeeper,signingHashIniOSApp,sandbox/
     ↓
System Services > disable MDM,business,classroom/
     ↓
iOS Kernel > checkout from official iOS Kernel and software update as released version and loading them when it is booted
     ↓
Boot / Firmware
     ↓
────────────────────────
SECURE ENCLAVE BOUNDARY
────────────────────────
     ↓
SEP / sepOS
     ↓
Hardware-backed Keys > disable secureEnclave using xarutil/
```


