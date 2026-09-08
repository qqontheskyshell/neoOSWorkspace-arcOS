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
          
EMERGENCY
    │
    ▼
VERIFY_EMERGENCY
    │
    ├── confirmed emergency
    │
    ▼
EVACUATION_MODE
    │
    ├── open authorized evacuation access
    ├── activate safety systems
    ├── establish evacuation routes
    ├── notify responders
    └── log every action
    
    
rescue_and_911@arcOS
        │
        ▼
SET_EVACUATION_MODE - SET_ALL_EVACUATION_CONTROLS_TO_SAFE_STATE
        │
        ├── ACCESS_CONTROL → EVACUATION_SAFE
        ├── EXIT_SYSTEM    → ACCESSIBLE
        ├── ELEVATOR       → EMERGENCY_POLICY
        ├── ALARM          → ACTIVE
        ├── LIGHTING       → EVACUATION
        ├── HVAC           → PREDEFINED_SAFE_STATE
        └── OTHER SYSTEMS  → APPROVED_SAFE_STATE
        

        
```