```markdown

APILib@arcOS=(mangrove.city,dowhat.co.kr)
chunsikQ@arcOS
└── APILib@arcOS
    └── APILib@arcOS
        ├── domain_scope
        │   └── *.APILib@arcOS
        │
        ├── API_DISCOVERY
        │   ├── public_endpoints → DISCOVER
        │   ├── documentation → INDEX
        │   └── version → TRACK
        │
        ├── AUTH
        │   ├── documented_auth → USE
        │   ├── credential_scope → MINIMUM
        │   └── undocumented_access → BLOCK
        │
        ├── DATA_POLICY
        │   ├── authorized_data → ALLOW
        │   ├── personal_data → MINIMIZE
        │   └── unauthorized_collection → BLOCK
        │
        └── SECURITY_BOUNDARY
            ├── public_API → ALLOW
            ├── authenticated_API → AUTH_REQUIRED
            ├── endpoint_scanning → BLOCK
            └── exploit_attempt → BLOCK
```