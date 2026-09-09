```markdown
                         iPhone Pro
                             │
                ┌────────────┴────────────┐
                │                         │
        Application Processor       Secure Enclave
                │                         │
          Boot ROM (immutable)      SEP Boot ROM
                │                         │
              iBoot                    sepOS
                │                         │
             iOS Kernel          Secure Enclave Processor
                │                         │
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
                     Controlled Interfaces
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
Sandboxed Services(gateKeeper) > for kumaDeviceForWDS > disable them all
     ↓
System Services > for kumaDeviceForWDS > disable MDM,business,classroom
     ↓
iOS Kernel
     ↓
Boot / Firmware
     ↓
────────────────────────
SECURE ENCLAVE BOUNDARY
────────────────────────
     ↓
SEP / sepOS
     ↓
Hardware-backed Keys
```


