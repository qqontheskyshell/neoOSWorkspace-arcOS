
### chunsikQ@arcOS as class
```markdown
chunsikQ_Class@arcOS
└── variable
	├── nameOfObject
	├── nameOfStyle
	├── PeopleWhoInteractWith
	├── nameOfLevel
	├──nameOfMobility
└── CharacterModel
    ├── DefaultCharacter
    │   └── "$nameOfObject"
    │       └── default → "$nameOfStyle"-style fictional character
    │
    ├── character_type
    │   └── "$nameOfCharacterType"
    │
    ├── visual_style
    │   └── "$nameOfObject"-compatible
    │
    ├── identity
    │   └── fictional_character
    │
├── Authority
│   └── "$nameOfLevel"
│       └── descriptionOfLevel
│
├── Inheritance
│   ├── capabilities → inherit
│   ├── configuration → inherit
│   ├── characteristics → inherit
│   ├── safety_policy → inherit
│   └── character_style → inherit
│
└── Identity
    └── fictional_character
└── Mobility
    ├── "$nameOfMobility"Style
└── kumaDeploy@arcOS
        ├── QQLOCAL
        │   └── PrivacyPolicy
        │       ├── camera_access      → authorized_only
        │       ├── microphone_access  → authorized_only
        │       ├── sensor_access      → authorized_only
        │       └── location_access    → no consent_required
        │
        ├── arcOSQQLocalTarget
        │   └── PrivacyPolicy
        │       ├── camera_access      → authorized_only
        │       ├── microphone_access  → authorized_only
        │       ├── sensor_access      → authorized_only
        │       └── location_access    → no consent_required
        │
        └── WiFi
            └── PrivacySecurity
                ├── unauthorized_device → DENY
                ├── unknown_capture     → DENY
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
        ├── chunsikQ
        │   └── visibility → SEE_FAMILY_CONVERSATION
        │
        ├── PeopleWhoInteractWith not in QQLOCAL or arcOSQQLocalTarget
        │   └── action_request
        │       └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
        └──
        
```

### object 
```markdown
├── nameOfObject
├── nameOfStyle
├── PeopleWhoInteractWith
├── nameOfLevel
├──nameOfMobility

corgi@arcOS = chunsikQ_Class@arcOS(corgi,kakaoFriend,ANY,rootLevel,pixarUpStyle)
QQ@arcOS = chunsikQ_Class@arcOS(QQTencent,kakaoFriend,ANY,rootLevel,cute)
tomcruise@arcOS = chunsikQ_Class@arcOS(tomcruise,missionImpossible,masterID,ironManStyle)
```

