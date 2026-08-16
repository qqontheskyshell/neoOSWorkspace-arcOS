## iOS Provisioning (What it is)

**Provisioning** is **Apple's mandatory security process** that lets iOS apps run on devices. Without it, your app simply won't launch.[1]

### What provisioning includes:

| Component | Purpose |
|-----------|---------|
| **Device ID (UDID)** | Unique identifier for each iOS device [1] |
| **App ID** | Unique bundle identifier for your app [1] |
| **Certificate** | Development or distribution cert in your keychain [1] |
| **Provisioning Profile** | Ties device ID + App ID + certificate together [1] |

### How it works:
1. Provisioning profile is installed in **Xcode** before building[1]
2. Same profile is installed on the **device** when you install the app[1]
3. iOS verifies: certificate matches, App ID matches, device is authorized[2][3]
4. If any component is missing or mismatched → **app cannot run**[1]

### Types of provisioning profiles:

| Type | Use Case | Device Limit |
|------|----------|--------------|
| **Development** | Test/debug on real devices | Your registered devices only [3] |
| **App Store** | Publish to App Store | None (no devices) [5] |
| **Ad Hoc** | Distribute to up to 100 users | Up to 100 devices [5] |
| **In-House** | Enterprise internal distribution | Unlimited (enterprise only) [5] |

Provisioning profiles are valid for **1 year**.[5]

***

## iOS Blueprint (What it is)

**Blueprint** is **not an Apple concept** — it's a feature from **third-party device management platforms** (like Blue Cedar, Esper, or enterprise MDM solutions).[6]

### What Blueprint does:

| Function | Purpose |
|----------|---------|
| **Device configuration** | Manage iOS devices after provisioning [6] |
| **Settings management** | Apply policies/configurations to devices [6] |
| **Group management** | Organize devices by blueprint or settings [6] |

### Key difference:

| Aspect | Provisioning | Blueprint |
|--------|--------------|-----------|
| **Who requires it** | **Apple** (mandatory) [1] | **Third-party MDM** (optional) [6] |
| **Purpose** | Let apps **run** on devices [1] | Manage devices **after** they're provisioned [6] |
| **When** | Before building/installing app [1] | After device is already provisioned [6] |
| **What it contains** | Certificates + device IDs + App ID [1] | Settings + policies + configurations [6] |

***

## Summary

- **Provisioning** = Apple's security requirement (certificate + profile + device ID) to run apps[1]
- **Blueprint** = Third-party MDM tool to manage/configure devices after provisioning[6]

You **must** have provisioning. Blueprint is optional and only used in enterprise device management scenarios.

Sources
[1] About iOS Provisioning and Blue Cedar https://apollo.bluecedar.com/platform-onprem-doc/about-ios-provisioning-and-blue-cedar
[2] Device provisioning for iOS - .NET MAUI - Microsoft Learn https://learn.microsoft.com/en-us/dotnet/maui/ios/device-provisioning/?view=net-maui-10.0
[3] What is a provisioning profile used for when developing iPhone applications? https://stackoverflow.com/questions/3362652/what-is-a-provisioning-profile-used-for-when-developing-iphone-applications
[4] 3. iOS Devices and Provisioning Profiles - Essential iOS Build ... https://www.oreilly.com/library/view/essential-ios-build/9781449314781/ch03.html
[5] Creating and Downloading a Distribution Provisioning Profile https://developer.apple.com/library/archive/documentation/ToolsLanguages/Conceptual/DevPortalGuide/CreatingandDownloadingaDistributionProvisioningProfile/CreatingandDownloadingaDistributionProvisioningProfile.html
[6] Managing iOS Devices through Blueprints and Settings https://help.esper.io/hc/en-us/articles/20518226918289-Managing-iOS-Devices-through-Blueprints-and-Settings
[7] Understanding provisioning for iOS applications https://bitrise.io/blog/post/understanding-provisioning-for-ios-applications
[8] Demystifying the iOS App Provisioning Process - Bounteous https://www.bounteous.com/insights/2018/08/08/demystifying-ios-app-provisioning-process/
[9] What exactly is a provisioning profile? - Apple Developer https://developer.apple.com/forums/thread/685723
[10] Launch Your App On The... https://developer.apple.com/library/archive/documentation/ToolsLanguages/Conceptual/YourFirstAppStoreSubmission/ProvisionYourDevicesforDevelopment/ProvisionYourDevicesforDevelopment.html
