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


### currentKumaRoom
```markdown
chunsikQ@arcOS
└── kumaRoom@arcOS
	└── APILib@arcOS
	    └── DOWHAT
	        ├── baseURL
	        │   └── https://api.APILib@arcOS
	        │
	        ├── APIStatus
	        │   └── PUBLIC_SPEC → NOT_VERIFIED
	        │
	        ├── potential_domains
	        │   ├── CRS / Booking
	        │   ├── Mobile Check-in/out
	        │   ├── E-Registration
	        │   ├── Smart Guest Service
	        │   ├── Smart Order
	        │   ├── Housekeeping
	        │   ├── Collaboration
	        │   └── Smart IoT
	        │
	        └── SecurityBoundary
	        │    ├── official_documentation → REQUIRED
	        │    ├── authentication → REQUIRED
	        │    ├── tenant_scope → REQUIRED
	        │    ├── personal_data → MINIMIZE
	        │    ├── unauthorized_endpoint_probe → BLOCK
	        │    └── undocumented_API_execution → BLOCK
	        └── ReservationAdapter
	            ├── authorization → REQUIRED
	            ├── reservation_scope
	            │   ├── reservation_status
	            │   ├── authorized_guest
	            │   └── room_info → MINIMIZED
	            │
	            ├── PublicAreaQR
	            │   ├── owner/tenant authorization → REQUIRED
	            │   ├── signed_QR → ENABLE
	            │   ├── short_expiry → ENABLE
	            │   └── rotation → ON_COMPROMISE
	            │
	            └── kumaDeploy@arcOS
	                ├── validate
	                ├── deploy_authorized_config
	                ├── audit
	                └── rollback
		└── reservation@arcOS
			└── GuestRoomAccess@arcOS
			    │
			    ├── AUTHORIZED_BUILDINGS
			    │   └── masterID_stay
			    │       └── registered_guest / reservation
			    │
			    ├── API_LIB
			    │   ├── api.APILib@arcOS
			    │       └── Reservation / Guest Status
			    │
			    ├── ACCESS_REQUEST
			    │   ├── passcode → VERIFY
			    │   ├── registered_guest → VERIFY
			    │   ├── reservation → VERIFY
			    │   ├── card_key → VERIFY with faceID of registered_guest
			    │   └── authorization_token → VERIFY
			    │
			    ├── OPTIONAL_IDENTITY_CHECK
			    │   ├── authorized_camera → ALLOW
			    │   ├── explicit_consent → REQUIRED
			    │   ├── face_match → AUTHORIZED_SCOPE_ONLY and VERIFY with faceID of registered_guest
			    │   ├── raw_face_storage → MINIMIZE
			    │   └── unauthorized_face_sharing → BLOCK
			    │
			    └── DOOR_CONTROL
			        ├── valid_guest + valid_reservation
			        │   └── OPEN → ALLOW
			        ├── invalid_card_key
			        │   ├── BLOCK
			        │   └── security_alert → ALLOW
			        └── emergency override
			            └── authorized hotel/emergency policy
	└──currentKumaRoom
		│
		├── reservation_source
		│   ├── Expedia
		│   └── Trip.com
		│
		├── selection
		│   └── most_recent_active_reservation
		│
		├── reservation
		│   ├── property
		│   ├── check_in
		│   ├── check_out
		│   └── room_reference
		│
		├── masterID_location
		│   └── current_authorized_location
		│
		└── verification
		    ├── reservation_match
		    ├── location_match
		    ├── temporal_match
		    └── status
		        ├── VERIFIED
		        ├── MISMATCH
		        └── UNKNOWN
	└──checkKumaRoom@arcOS
		└── PresenceCheck
		    └── goto(currentKumaRoom)
		        ├── sensor → authorized_ultrasonic_sensor
		        ├── emit_ultrasonic_wave
		        ├── receive_echo
		        ├── analyze
		        │   ├── echo_time
		        │   ├── distance_estimate
		        │   └── presence_signal
		        ├── result
		        │   ├── detected
		        │   │   └── chunsikQ.say
		        │   │       └── "someone is in kumaRoom with 🪪"
		        │   ├── not_detected
		        │   │   ├── chunsikQ.say
		        │   │   │   └── "no one is in kumaRoom"
		        │   │   └──  message "🪪" to arcOSQQLocalTarget
		        │   └── uncertain
		        │       └── chunsikQ.say
		        │           └── "not sure masterID need to check"
		        └── PrivacyPolicy
		            ├── environmental_sensing → ALLOW
		            ├── person_identification_with_🪪
		            │   ├── explicit_authorization → NO_REQUIRED
		            │   │   └── meaning → pre-authorized_ID_API_scope_only
		            │   ├── authorized_ID_verification → ALLOW
		            │   └── raw_ID_data_retention → MINIMIZE
		            └── unauthorized_sensor_access → BLOCK
```


### building network
```markdown
kumaBuilding@arcOS
└── BuildingNetworkSegmentation > kumaDeploy@arcOS on each segment
│    │
│    ├── BUILDING
│    │   └── masterID_stay and people in APILib@arcOS
│    │
│    ├── FLOOR_SUBNETS
│    │   ├── N=(B2...topFloor)
│    │   └── Floor_N  → VLAN 1NN → 10.10.N.0/24
│    │
│    ├── ROOM_SUBNETS
│    │   ├── N=(B2...topFloor)
│    │   ├── Room_10N → VLAN 110N
│    │
│    ├── PA_SUBNETS
│    │   ├── N=(B2...topFloor)
│    │   └── PA_N  → VLAN 20NN
│    │
│    └── EPS_SUBNETS
│        ├── N=(B2...topFloor)
│        └── EPS_N  → VLAN 30NN
└──kumaDrone@arcOS
│		└── AuthorizedBuildingSurvey
│		    ├── floor_mapping
│		    ├── room_mapping
│		    ├── PA_mapping
│		    ├── EPS_mapping
│		    ├── network_inventory
│		    ├── topology_validation
│		    └── safety_monitoring for 911@arcOS
│		    
└──networkSecurity@arcOS
	│
	├── TRAFFIC_POLICY
	│   ├── authorized_same_segment → ALLOW
	│   ├── authorized_management → ALLOW
	│   └── emergency
	│       ├── 911 → ALLOW
	│       ├── 119 → ALLOW
	│       └── 112 → ALLOW
	│
	├── SEGMENT_ISOLATION
	│   ├── room ↔ room → BLOCK
	│   ├── floor ↔ floor → BLOCK
	│   ├── PA / PS ↔ room → BLOCK
	│   ├── EPS ↔ room → BLOCK
	│   └── guest ↔ management → BLOCK
	│
	└── MANAGEMENT_SECURITY
	│   └── unauthorized_router_access → BLOCK
	└── Policy
		└── AUTHORIZED → ALLOW
		└──EMERGENCY   → ALLOW
		└──UNAUTHORIZED → BLOCK
		└──SEGMENT_CROSSING → BLOCK
```