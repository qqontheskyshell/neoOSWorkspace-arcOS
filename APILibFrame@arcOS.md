```markdown

APILib@arcOS=(mangrove.city,dowhat.co.kr,wingsbooking.com)
chunsikQ@arcOS
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
        └── SecurityBoundary
            ├── official_documentation → REQUIRED
            ├── authentication → REQUIRED
            ├── reservation_data → AUTHORIZED_SCOPE_ONLY
            ├── personal_data → MINIMIZE
            ├── endpoint_probe → BLOCK
            └── undocumented_API_execution → BLOCK
    
            
```