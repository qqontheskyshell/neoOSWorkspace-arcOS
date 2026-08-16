On iOS there isn’t a single “app config file” for a locally installed app; instead, configuration lives across several mechanisms: managed app configuration (MDM), Info.plist and build configs, Settings.bundle, in‑app settings screens, and local storage (UserDefaults, Keychain, files, databases).[1][2][3][4]

Here’s a concise breakdown of each major app‑config layer you’ll see on a local install.

***

## 1. Managed App Configuration (MDM “App Config”)

When an iOS app is **managed** by MDM, the server can push a configuration plist to the app so the user doesn’t have to manually configure it.[2][5][1]

- Mechanism: MDM sends a key–value dictionary (often XML plist based on the app’s schema) down to the device, and iOS delivers it to the app as managed app config.[5][1][2]
- Access in app: The app reads these values using `UserDefaults` / `NSUserDefaults`, usually via a specific suite or keys the developer documents.[2][5]
- Use cases: Server base URLs, feature flags, tenant IDs, SSO endpoints, logging levels, etc., controlled per deployment.[1][5]

From the device’s point of view, these configurations are part of the app’s sandboxed data, not a user-editable file, but they constitute a key piece of “app config” in managed environments.[1][2]

***

## 2. Info.plist and build‑time configuration (xcconfig)

Apps embed static configuration in their **Info.plist**, often parameterized by xcconfig files for different environments.[3]

- Info.plist: Contains static keys like bundle ID, display name, URL schemes, entitlement-related settings, App Transport Security rules, and SDK config keys.[3]
- xcconfig: You can define macros like `API_BASE_URL=https://prod.example.com` in environment-specific `.xcconfig` files, then reference them in Info.plist as `$(API_BASE_URL)`.[6][3]
- Security: A common pattern is to keep secrets in a git‑ignored `secrets.xcconfig` and inject them into Info.plist at build time, so the source repo doesn’t contain raw secrets.[3]

These configs are baked into the binary and plist; on a local install they’re not dynamically editable by the end user, but they govern core behavior.[6][3]

***

## 3. iOS Settings app side: Settings.bundle

If an app exposes options in the **Settings** app, it uses a Settings.bundle.[7]

- Purpose: Provide infrequently changed configuration options in the Settings app, separate from the main UI.[7]
- Implementation: A `Settings.bundle` contains plist files describing toggles, text fields, etc.; iOS renders these as a Settings page for the app.[7]
- Storage: Values are stored in `UserDefaults`, keyed as specified in the bundle. The app reads them at runtime.[2][7]

So for a locally installed app, Settings.bundle plus UserDefaults is a common “user config” store.

***

## 4. In‑app configuration screens

Most modern apps surface configuration **inside the app UI** rather than only through Settings.[7]

- Design guidance: Apple recommends putting frequently changed options in the app itself and only rare options in Settings.[7]
- Storage: These screens typically back onto `UserDefaults`, local files, Core Data, or remote config consumed and cached locally.[4][2]
- Examples: Notification preferences, theme, account linking, feature switches.

From the system perspective, this is still just app data in its sandbox; conceptually, it’s a core part of “local app config” controlled by the user.

***

## 5. Local data stores used as configuration

Several local storage mechanisms in iOS are often used to hold configuration/state:[4]

- **UserDefaults**: Key–value store for lightweight preferences and flags (e.g., seen onboarding, chosen language).[4][2]
- **Keychain**: Secure storage for secrets – tokens, passwords, keys – part of the app’s config in security‑sensitive contexts.[4]
- **Files / plists / JSON in app container**: Apps might persist structured config in their `Documents` or `Library/Application Support` folders.[4]
- **Core Data / SQLite**: Heavier configuration/state such as feature metadata or user profile settings.[4]

For a locally installed app, all of these live in its sandbox, not system‑wide.

***

## 6. Local network & privacy related config

With iOS 14+, apps must request **Local Network** access to talk to LAN devices; the user’s choice becomes part of the app’s effective config.[8][9]

- First use: iOS shows `[AppName] would like to find and connect to devices on your local network` and the user chooses Allow/Don’t Allow.[9][8]
- Management: The user can later toggle per‑app Local Network access under `Settings > Privacy & Security > Local Network`.[8][9]

Similar privacy toggles (Location, Camera, Microphone, etc.) are not “app config files,” but they strongly affect app behavior and are managed per app.[8][7]

***

## 7. MDM app management vs local install

On supervised/managed devices, the MDM can additionally:

- Install/uninstall apps remotely and pair the install command with **Managed App Config** payloads.[5][1]
- Apply profiles that constrain or preconfigure app behavior beyond what local users can change.[1][2]

Locally, the app still sees these as config via `UserDefaults` or special config APIs; the distinction is that the source is MDM rather than the user or Info.plist.[5][2][1]

***

If you’d like, I can map this onto a concrete example: for instance, a managed browser app on iOS with MDM app config, Info.plist keys, Settings.bundle, local preferences, and Keychain, showing exactly which pieces you’d introspect or manipulate from your own code or MDM tooling.

Sources
[1] iOS App Configurations | macOS, tvOS, & iPadOS ... https://www.manageengine.com/mobile-device-management/help/app_management/ios_app_configurations.html
[2] iOS app: Managed App Config https://developer.apple.com/forums/thread/672938
[3] Secure (xc)config for iOS apps - DEV Community https://dev.to/donniejp/secure-xc-config-for-ios-apps-115b
[4] Local Data Storage on iOS – What Do You Need to Know? https://www.holdapp.com/blog/local-data-storage-ios-keychain-core-data
[5] iOS managed app configuration https://help.ivanti.com/mi/help/en_us/CORE/11.4.0.0/appwk/AppsAtWork/iOS_managed_app_configur.htm
[6] Switching between local and production environment settings https://stackoverflow.com/questions/2063922/iphone-switching-between-local-and-production-environment-settings
[7] Settings - Interaction - iOS Human Interface Guidelines - CodersHigh https://codershigh.github.io/guidelines/ios/human-interface-guidelines/interaction/settings/index.html
[8] If an app would like to connect to devices on your local ... https://support.apple.com/en-us/102229
[9] Enabling Applications to Communicate Over the Local Network on ... https://kb.audiomodeling.com/support/solutions/articles/206000041700-enabling-applications-to-communicate-over-the-local-network-on-ios-15-16-17-18-26-
[10] アプリ内課金に使うStoreKit configuration fileのLocal/Syncedのあれこれ - Qiita https://qiita.com/samekard_dev/items/472118904351912f1a8f
