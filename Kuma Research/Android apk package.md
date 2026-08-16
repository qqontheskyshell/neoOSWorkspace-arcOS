## `assembleRelease` - What it means

**`assembleRelease`** is a **Gradle task** that builds a **release version** of your Android APK:

| Aspect | Release APK (`assembleRelease`) | Debug APK (`assembleDebug`) |
|--------|-------------------------------|---------------------------|
| **Purpose** | For production/play store [3] | For development/testing |
| **Optimization** | Optimized (ProGuard/R8) [3] | Not optimized |
| **Debug symbols** | ❌ Removed [3] | ✅ Included |
| **Signing** | Requires release signing key [7] | Auto-signed with debug key |
| **APK location** | `app/build/outputs/apk/release/app-release.apk` [7] | `app/build/outputs/apk/debug/app-debug.apk` |

If you don't sign the APK, output will be named `app-release-unsigned.apk`.[7]

***

## `gradlew` - What it is

**`gradlew`** = **Gradle Wrapper** (the `w` stands for "wrapper")[2][4]

### Key differences: `gradle` vs `gradlew`

| Feature | `gradle` | `gradlew` |
|---------|----------|-----------|
| **Installation** | You must manually install Gradle [6] | No local Gradle needed [2][4] |
| **Version** | Uses whatever version is installed | Uses **project's specific version** [2][4] |
| **Auto-download** | ❌ No | ✅ Downloads Gradle from internet if missing [2] |
| **Consistency** | ❌ Different machines may use different versions | ✅ Everyone uses same version [2] |
| **Files** | System command | `gradlew` (Linux) + `gradlew.bat` (Windows) [4][8] |

### How `gradlew` works under the hood:
1. Downloads correct Gradle version (if not cached)[6]
2. Parses your arguments[6]
3. Calls Gradle task[6]

### Usage:
```markdown
# Linux/Mac
./gradlew assembleRelease

# Windows
gradlew.bat assembleRelease
```

**Best practice:** Always use `gradlew` inside a project. If you don't have it, run `gradle wrapper` to create it.[2][6]

***

### Full command explained:
```markdown
./gradlew assembleRelease
```
- `./gradlew` → Run Gradle Wrapper (Linux)
- `assembleRelease` → Build release APK task

This builds your **production-ready, signed, optimized APK**.[3]

Sources
[1] Difference between :app:assembleRelease and assembleRelease https://stackoverflow.com/questions/60990805/difference-between-appassemblerelease-and-assemblerelease
[2] gradle vs. gradlew - what's the difference? - Tom Gregory https://tomgregory.com/gradle-vs-gradlew-difference
[3] Android Studio 中 build、assemble、assembleDebug 和 assembleRelease 构建 aar 的区别 https://blog.csdn.net/weixin_40323532/article/details/147903993
[4] What's the Gradle Wrapper and Why Use it? - Tom Gregory https://tomgregory.com/what-is-the-gradle-wrapper-and-why-should-you-use-it
[5] Difference between assemble vs assembleDebug vs assembleRelease https://stackoverflow.com/questions/43951806/difference-between-assemble-vs-assembledebug-vs-assemblerelease
[6] Difference between using gradlew and gradle https://stackoverflow.com/questions/39627231/difference-between-using-gradlew-and-gradle
[7] gradlew assembleRelease not updating APK output file · Issue #6745 https://github.com/facebook/react-native/issues/6745
[8] Guide to the Gradle Wrapper | Baeldung https://www.baeldung.com/gradle-wrapper
[9] gradlew assembleRelease vs react-native run-android - Reddit https://www.reddit.com/r/reactnative/comments/ctk2rk/gradlew_assemblerelease_vs_reactnative_runandroid/
[10] What is gradle wrapper and the gradlew.bat file? - Stack Overflow https://stackoverflow.com/questions/44860306/what-is-gradle-wrapper-and-the-gradlew-bat-file
