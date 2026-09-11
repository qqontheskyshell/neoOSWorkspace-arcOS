### @kumaPGCrawler
```bash
@kumaPGCrawler
    │
    ├── PGInventory
    │   ├── KG이니시스
    │   ├── NHN KCP
    │   ├── 토스페이먼츠
    │   ├── NICE
    │   ├── KICC
    │   ├── 카카오페이
    │   ├── 네이버페이
    │   ├── 다날
    │   ├── 헥토파이낸셜
    │   ├── KSNET
    │   ├── 스마트로
    │   ├── 웰컴페이먼츠
    │   ├── PAYCO
    │   └── 기타 국내 PG
    │
    ├── OfficialAPI
    │   ├── documentation
    │   ├── endpoints
    │   ├── authentication
    │   ├── SDK
    │   ├── webhook
    │   ├── sandbox
    │   └── rate_limits
    │
    ├── APIClassification
    │   ├── payment
    │   ├── refund/cancel
    │   ├── billing
    │   ├── virtual_account
    │   ├── identity
    │   ├── escrow
    │   └── cash_receipt
    │
    ├── AuthorizedCrawler
    │   ├── official_docs_only
    │   ├── robots/terms_check
    │   ├── rate_limit
    │   ├── provenance
    │   └── schema_normalization
    │
    └── SecurityBoundary
        ├── no_credential_bypass
        ├── no_private_endpoint_probe
        ├── no_hidden_API_exploitation
        └── least_privilege
```

### @openBanking
```markdown
@openBanking
    └── KFTC_OPENBANKING
        ├── AUTH
        │   └── OAuth2 + USER_CONSENT
        ├── ACCOUNT
        │   ├── authorized_account_list
        │   ├── balance
        │   └── transaction_history
        ├── ANALYSIS
        │   ├── cash_flow
        │   ├── unusual_transaction
        │   ├── recurring_payment
        │   └── anomaly_detection
        ├── TARGET
        │   └── USER_OWNED_OR_EXPLICITLY_AUTHORIZED_ACCOUNTS
        └── PRIVACY
            ├── third_party_account_search → BLOCK
            ├── hidden_asset_discovery → BLOCK
            └── unauthorized_access → BLOCK
```

### black money in Kuma Bank
```markdown
arcOSLnotes
└── FINANCIAL_CONNECTION_RESEARCH
    ├── entities
    │   ├── HSBC
    │   ├── USDC
    │   ├── Li_Ka-shing
    │   ├── Warren_Buffett
    │   ├── Morris_Chang_장중모
    │   └── 시도회장
    │
    ├── VERIFIED_FACTS
    │   ├── HSBC_AML_HISTORY
    │   ├── HSBC_STABLECOIN_ACTIVITY
    │   ├── Li_Ka-shing_BUSINESS_NETWORK
    │   ├── Buffett_BERKSHIRE_NETWORK
    │   └── Morris_Chang_TSMC_NETWORK
    │
    ├── HYPOTHESES
    │   └── "any connection among these stake holders"
    │
    ├── NOT_ESTABLISHED
    │   ├── USDC_money_laundering
    │   ├── Li_Ka-shing_money_laundering
    │   ├── Buffett_money_laundering
    │   ├── Morris_Chang_money_laundering
    │   └── 시도회장_connection
    │
    └── EVIDENCE_REQUIRED
        ├── court_records
        ├── regulatory_filings
        ├── corporate_filings
        ├── blockchain_transaction_ids
        ├── beneficial_ownership_records
        └── documented_financial_transactions

ai진상++
└── FINANCIAL_CONNECTION_REVIEW
    ├── evidence_only: ON
    ├── timeline_analysis: ON
    ├── entity_resolution: ON
    ├── transaction_graph: ON
    ├── contradiction_check: ON
    ├── rumor_as_fact: BLOCK
    ├── unsupported_accusation: BLOCK
    └── conclusion
        └── VERIFIED / UNVERIFIED / DISPROVEN
```

```markdown
@kumaBankMonitoring
└── masterID
└── FINANCE_FRAUD_RESPONSE
    ├── Shinhan
    ├── Hana
    └── KakaoBank
└── Action
        │
        ├── 1. 본인인증
        ├── 2. 연결 계좌/가상계좌 조회
        ├── 3. 미승인 연결 발견
        │      └── 은행 공식 채널에서 해지
        │
        ├── 4. 카드 거래내역 확인
        │      └── 본인이 하지 않은 거래만 이의제기
        │
        ├── 5. 복제/도용 의심 카드
        │      └── 즉시 사용정지 → 재발급/해지
        │
        └── 6. 지속 모니터링
               ├── 신규 거래 알림
               ├── 신규 카드 발급 알림
               ├── 계좌 연결 변경 알림
               └── 이상거래 발생 시 본인 확인
```               