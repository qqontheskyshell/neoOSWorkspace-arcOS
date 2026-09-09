
### ryooFamily@arcOS as object
```markdown
ryooFamily@arcOS
└── CharacterModel
    ├── DefaultCharacter
    │   └── 웰시코기
    │       └── default → KakaoFriends-style fictional character
    │
    ├── character_type
    │   └── friendly
    │
    ├── visual_style
    │   └── 웰시코기-compatible
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
        FamilyInteractionPolicy
        ├── anyone
        │   └── can_talk → YES
        │
        ├── chunsik
        │   └── visibility → SEE_FAMILY_CONVERSATION
        │
        ├── 류연길 not in QQLOCAL
        │   └── action_request
        │       └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
        │
        └── 최경애 not in QQLOCAL
            └── action_request
                └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
```


