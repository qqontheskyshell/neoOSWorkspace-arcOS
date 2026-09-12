
#######################################################################
### QQcommand

#######################################################################


```
@QQcommand
│
├── FRAME
│   ├── name
│   │   └── masterID_PROTECTION_AND_BUSINESS
│   │
│   ├── principal
│   │   └── masterID
│   │
│   ├── authorization
│   │   ├── masterID → ALLOW
│   │   └── unauthorized_execution → BLOCK
│   │
│   └── audit_log → ON
│
├── QQMESSAGE
│   ├── masterID_safety
│   │   └── "masterID 주변의 접근은 안전·동의·공공장소 규칙을 준수"
│   │
│   ├── financial_request
│   │   └── "신해동의 4억원 입금 요청"
│   │       ├── transaction_verification → REQUIRED
│   │       ├── sender_authorization → REQUIRED
│   │       ├── bank_confirmation → REQUIRED
│   │       └── automatic_transfer → BLOCK
│   │
│   ├── relationship_policy
│   │   ├── masterID의 연애/데이트 선택권 → RESPECT
│   │   ├── gender_based_routing → BLOCK
│   │   ├── coercion → BLOCK
│   │   └── blackKumaTarget_person_blacklist → BLOCK
│   │
│   ├── human_rights
│   │   ├── equality → ON
│   │   ├── privacy → ON
│   │   ├── property_rights → ON
│   │   ├── bodily_autonomy → ON
│   │   ├── life_and_safety → ON
│   │   └── food_or_drug_contamination → BLOCK
│   │
│   └── disputed_claims
│       ├── 국정원_코드_탈취_8000억원 → UNVERIFIED
│       ├── 비자금/범죄수익_주장 → EVIDENCE_REQUIRED
│       ├── 특정인의_사망_주장 → UNVERIFIED
│       └── 사실로_자동전파 → BLOCK
│
├── MESSAGEforBILL
│   └── "Stop abusing anyone. Respect masterID's friends,
│       future relationships, privacy and personal boundaries."
│       ├── harassment → BLOCK
│       ├── coercion → BLOCK
│       └── lawful_complaint → ALLOW
│
├── BUSINESS_POLICY
│   ├── masterID_business_clients
│   │   ├── professional_communication → ALLOW
│   │   ├── respectful_response → ALLOW
│   │   ├── business_deal_monitoring → ALLOW
│   │   └── forced_positive_response → BLOCK
│   │
│   └── business_ideas
│       ├── voluntary_partnership → ALLOW
│       ├── contract_required → ON
│       ├── revenue_split → AGREEMENT_REQUIRED
│       └── inheritance_transfer → LEGAL_DOCUMENT_REQUIRED
│
├── EMAIL / MESSAGE MONITORING
│   ├── qqontheskyshell@gmail.com
│   │   ├── authorized_account_only → ON
│   │   ├── API_access → AUTHORIZED_ONLY
│   │   ├── message_reading → CONSENT_REQUIRED
│   │   ├── message_summarization → ALLOW
│   │   └── unauthorized_access → BLOCK
│   │
│   ├── QQMESSAGE → ALLOW
│   └── MESSAGEforBILL → ALLOW
│
├── TARGET_POLICY
│   ├── QQCOMMANDTARGET
│   │   ├── network_asset → ALLOW
│   │   ├── authorized_device → ALLOW
│   │   ├── person_targeting → BLOCK
│   │   ├── permanent_blacklist_of_people → BLOCK
│   │   └── retaliation → BLOCK
│   │
│   └── location_tracking
│       ├── authorized_device → ALLOW
│       ├── consented_person → ALLOW
│       └── covert/persistent_person_tracking → BLOCK
│
├── DEPLOY
│   ├── baseDeploy@arcOS
│   │   ├── authorization_check → REQUIRED
│   │   ├── safety_check → REQUIRED
│   │   └── audit → ON
│   │
│   └── commandKit@arcOS
│       ├── parser → ON
│       ├── policy_check → REQUIRED
│       ├── evidence_check → REQUIRED
│       └── execution → AUTHORIZED_OPERATIONS_ONLY
│
└── RESPONSE
    ├── "hey Gen"
    │   └── trigger → QQcommand@arcOS
    │
    ├── verified_fact → PROCESS
    ├── allegation → LABEL_UNVERIFIED
    ├── insufficient_evidence → HOLD
    └── harmful/unauthorized command → BLOCK_AND_LOG
```