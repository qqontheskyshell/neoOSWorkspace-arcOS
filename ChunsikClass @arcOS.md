
### chunsikQ@arcOS as class
```markdown
chunsikQ_Class@arcOS
└── variable
	├── nameOfObject
	├── nameOfStyle
	├── PeopleWhoInteractWith
└── CharacterModel
    ├── DefaultCharacter
    │   └── nameOfObject
    │       └── default → nameOfStyle-style fictional character
    │
    ├── character_type
    │   └── friendly
    │
    ├── visual_style
    │   └── nameOfObject-compatible
    │
    ├── identity
    │   └── fictional_character
    │
    └── kumaDeploy@arcOS
        ├── QQLOCAL
        │   └── PrivacyPolicy
        │       ├── camera_access      → authorized_only
        │       ├── microphone_access  → authorized_only
        │       ├── sensor_access      → authorized_only
        │       └── location_access    → consent_required
        │
        ├── arcOSQQLocalTarget
        │   └── PrivacyPolicy
        │       ├── camera_access      → authorized_only
        │       ├── microphone_access  → authorized_only
        │       ├── sensor_access      → authorized_only
        │       └── location_access    → consent_required
        │
        └── WiFi
            └── PrivacySecurity
                ├── unauthorized_device → DENY
                ├── unknown_capture     → ALERT
                ├── credential_rotation → ON
                └── audit_log           → ON
                
    └── LLMKit@arcOS
        ├── character_context
        ├── dialogue_style
        ├── personality_model
        ├── response_training
        └── safety_policy
            │
            ▼
        InteractionPolicy
        ├── anyone
        │   └── can_talk → YES
        │
        ├── chunsik
        │   └── visibility → SEE_FAMILY_CONVERSATION
        │
        ├── PeopleWhoInteractWith not in QQLOCAL or arcOSQQLocalTarget
        │   └── action_request
        │       └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
        └──
        
```


### object 
```markdown
corgi@arcOS = chunsikQ_Class@arcOS (corgi,kakaoFriend,ANY)
tomcruise@arcOS = chunsikQ_Class@arcOS (tomcruise,missionImpossible,masterID)
```


