
### ryooFamily@arcOS as object
```markdown
ryooFamily@arcOS
└── CharacterModel
    ├── DefaultCharacter
    │   └── chunsik
    │       └── default → KakaoFriends-style fictional character
    │
    ├── character_type
    │   └── friendly
    │
    ├── visual_style
    │   └── chunsik-compatible
    │
    ├── identity
    │   └── fictional_character
    │
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
        ├── 류연길
        │   └── action_request
        │       └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
        │
        └── 최경애
            └── action_request
                └── VERIFY_AUTHORIZATION → SAFETY_CHECK → EXECUTE
```


