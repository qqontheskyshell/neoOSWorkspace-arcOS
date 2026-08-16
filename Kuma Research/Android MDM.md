Here’s a clear overview of **Android device management features** and **the conditions for installing/using device management on Android**.

***

## What Android device management covers

Android Enterprise (the enterprise/MDM framework) uses a **Device Policy Controller (DPC)** app to enforce policies. A DPC can run in:

- **Device owner mode** → manages the entire device  
- **Profile owner mode** → manages only the work profile[1]

### Core management modes

| Mode | Name | Scope | Device ownership | When you can provision |
|------|------|-------|------------------|------------------------|
| Fully managed device | Device owner mode | Entire device (all apps, settings, data) | **Organization-owned only** | Only during **out-of-box setup** or after a **factory reset** [1] |
| Work profile | Managed profile mode | Work profile only (personal profile unchanged) | Personal **or** organization-owned | During OOB (for org devices) **or** after OOB (for BYOD) [1] |

Fully managed devices give you **device-level policies** that are not available to work profiles, such as:
- Full device control (no personal apps)
- Kiosk / single-app mode
- Signage / dedicated-device use cases[1]

***

## Key device management features

Android provides a broad set of management capabilities for many use cases (employees, factories, kiosks, signage). Common features include:

- **App management**: install, block, update, pin apps; allowlist/denylist[2][3]
- **Passcode/security**: enforce password complexity, lock screen, wipe after failed attempts[2]
- **Restrictions**: disable camera, NFC, Bluetooth, USB, screenshots, etc.[2]
- **Wi‑Fi & VPN**: configure Wi‑Fi, proxies, and VPN profiles[2]
- **Certificates**: push CA certificates for secure traffic[2]
- **Workspace security**: proactive security rules for work profile data[2]
- **Device policies**: remote lock, remote wipe, device visibility to org, compliance checks[4][5]
- **Kiosk / single-app mode**: lock device to specific apps for dedicated use[1]

The exact set of policies available depends on the **management mode** (device owner vs profile owner) and the **Android version**.[1]

***

## Conditions for device management to work on Android

### 1. Minimum Android version

- Devices must run **Android 5.0 (Lollipop, API 21) or higher** to support device management modes.[1]
- For some MDM solutions (e.g., ManageEngine Android Device Policy), the **practical minimum is Android 6.0+**.[2]

### 2. Required OS features (for device manufacturers / custom builds)

To enable device management on an Android device, the system must expose these features:

```markdown
android.software.device_admin
android.software.managed_users
```

Check them with:

```markdown
adb shell pm list features
```

You should see both features listed.[6]

Additional requirements:
- The **Launcher** must support **badging** apps with work icon badges (to show managed apps).[6]
- The system UI (notifications, etc.) must use **work-badged assets** for managed apps.[6]

### 3. Enrollment / provisioning requirements

For **fully managed device (device owner)**:
- Must be **organization-owned**.
- Must be provisioned **during out-of-box setup** or after a **factory reset**.[1]
- Enrollment methods include:
  - QR code
  - NFC
  - Corporate accounts
  - Cloud-based enrollment[1]

For **work profile (profile owner)**:
- Can be on **personal or org-owned** devices.
- Can be set up:
  - During OOB (for org devices)
  - After OOB (for BYOD)[1]
- Enrollment methods similar: QR, NFC, accounts, cloud.[1]

The device must show **appropriate disclosures** to users during setup (OOB or work profile setup) explaining what device owner / managed profile means.[6]

### 4. DPC app requirements

- A **Device Policy Controller (DPC)** app must be installed and set as:
  - **device owner** for fully managed devices
  - **profile owner** for work profiles[1]
- The DPC:
  - Adds user accounts
  - Enforces policy compliance
  - Enables system apps as needed[6]

For Android 14+ with **headless system user** mode:
- A DPC can be set as device owner only if it supports **affiliated mode** (`HEADLESS_DEVICE_OWNER_MODE_AFFILIATED`).[6]

***

## How to check if your Android device supports device management

On a running device:

```markdown
adb shell pm list features
```

You should see:

```text
android.software.device_admin
android.software.managed_users
```

If both are present, the OS supports device management features.[6]

Then confirm:
- You can go to **Settings → Security → Device administrators** (or similar) and see options to enable a DPC as device administrator.[7]
- You can create/manage **multiple users / work profiles** (Settings → System → Multiple users).[8]

***

If you want, I can:
- Map these features to **specific ADB commands or APIs** (e.g., `DevicePolicyManager` methods), or  
- Show a **step-by-step example** of enrolling a device as a fully managed device vs. work profile using QR code enrollment.

Sources
[1] Device management overview https://source.android.com/docs/devices/admin
[2] Managing Android Devices using Android Device Policy app https://www.manageengine.com/mobile-device-management/help/enrollment/mdm_android_device_policy_app.html
[3] Mobile device management solutions – Android Enterprise https://www.android.com/intl/en_ie/enterprise/management/
[4] Full device management - Android Enterprise Help https://support.google.com/work/android/answer/9562029?hl=en
[5] How do you guys debug network issues? : r/androiddev - Reddit https://www.reddit.com/r/androiddev/comments/14cswg8/how_do_you_guys_debug_network_issues/
[6] डिवाइस मैनेजमेंट की सुविधा लागू करना | Android Open Source Project https://source.android.com/docs/devices/admin/implement?hl=hi
[7] How do you enable the Android Device Manager Guide? https://forums.androidcentral.com/threads/how-do-you-enable-the-android-device-manager-guide.372087/
[8] Delete, switch, or add users - Android Help https://support.google.com/android/answer/2865483?hl=en
[9] What Is Android Device Management? - IBM https://www.ibm.com/think/topics/android-device-management
[10] Provisioning methods https://developers.google.com/android/management/provision-device
[11] 2. App Management &... https://www.miniorange.com/blog/what-is-android-device-management/
[12] Manage Android devices in Microsoft Intune https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/deployment-guide-platform-android
