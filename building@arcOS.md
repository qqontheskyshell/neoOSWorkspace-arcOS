```markdown

chunsikQ@arcOS
      │
      ▼
┌──────────────────────────────┐
│     VERIFY_AUTHORIZATION     │
│     Identity + Permission    │
└──────────────┬───────────────┘
               │
       ┌───────┼──────────────────────────────────────┐
       │       │          │          │                │
       ▼       ▼          ▼          ▼                ▼
 Building   Elevator    Alarm     CCTV /          Emergency
 Access     Safety API   API       Safety Feed     Response
   API                              │                │
       │                            ▼                ├── Security Center
       │                     PrivacyFilter@arcOS     ├── Building Manager
       │                                             └── Emergency Services
       │
       ├── doors
       ├── elevators
       ├── windows
       └── emergency doors
                        

                 RESCUE / 911@arcOS
                         │
                         ▼
                ┌─────────────────┐
                │ EVACUATION MODE │
                └────────┬────────┘
                         │
          ┌──────────────┼─────────────────┐
          │              │                 │
          ▼              ▼                 ▼
   BUILDING ACCESS   SAFETY SYSTEMS    EMERGENCY ALERT
          │              │                 │
          ├── unlock     ├── evacuation   ├── Security Center
          │   authorized │   lighting      ├── Building Manager
          │   egress     ├── exit routes  └── 911 / Emergency
          │              ├── fire/safety       Services
          │              │   interfaces
          │              └── designated
          │                  evacuation
          │                  switches
          │
          ▼
   EVACUATION-SAFE STATE
          │
          ├── Emergency exits → ACCESSIBLE
          ├── Egress doors    → UNLOCK / SAFE MODE
          ├── Elevators       → EMERGENCY POLICY
          ├── Windows         → AUTHORIZED SAFE STATE
          └── Other switches  → PREDEFINED SAFE STATE
        
```