Let me walk you through **Apple's official visionOS tutorial** step by step to create your first app:

***

## 📋 Step 1: Check Requirements

Before starting, ensure you have:

| Requirement | Details |
|-------------|---------|
| **Mac** | Apple Silicon (M1/M2/M3) required, macOS Sonoma 14.2+ [3] |
| **Xcode** | Version 15.2+ (download from Mac App Store or developer.apple.com) [1] |
| **Apple Developer Account** | Free account works; $99/year for App Store distribution [3] |
| **visionOS Simulator** | Bundled with Xcode (no separate install) [1] |

> ✅ **Good news**: You don't need an Apple Vision Pro headset to start — the simulator works for development[3]

***

## 🔧 Step 2: Install Xcode

1. Open **Mac App Store** on your Mac
2. Search for **"Xcode"** (or download from developer.apple.com)
3. Install Xcode (will take ~10GB, ~30-60 minutes)
4. Open Xcode and accept the license agreement
5. Go to **Xcode → Settings → Platforms** and download **visionOS Simulator Runtime**

[1][4]

***

## 🚀 Step 3: Create Your First visionOS Project

### In Xcode:

1. **File → New → Project** (or ⌘N)
2. Select **"App"** under **visionOS** platform
3. Fill in project details:

| Field | Example Value |
|-------|---------------|
| Product Name | `HelloVisionOS` |
| Team | Your Apple Developer account (login required) [1] |
| Organization Identifier | `com.yourname` |
| Bundle Identifier | `com.yourname.hellovisionos` |
| Initial Scene | **Window** (for 2D) or **Volume** (for 3D) [1] |
| Immersive Space Renderer | **RealityKit** (recommended) [1] |
| Immersive Space Type | **Full** (VR) or **Mixed** (AR with passthrough) [1] |

4. Click **Next** → Choose location → **Create**

[4][1]

***

## 📱 Step 4: Understand the Project Structure

Your new project will have this key structure:

```
HelloVisionOS/
├── HelloVisionOSApp.swift      ← @main entry point (defines scenes)
├── ContentView.swift           ← 2D window content
├── ImmersiveView.swift         ← 3D immersive space content
└── Assets.xcassets             ← Images, colors, 3D models
```

### Key Code Explained:

```swift
import SwiftUI

@main
struct HelloVisionOSApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()  // 2D window
        }
        ImmersiveSpace(id: "ImmersiveSpace") {
            ImmersiveView()  // 3D space
        }.immersionStyle(selection: .constant(.full), in: .full)
    }
}
```

**What this does:**
- `WindowGroup` = Traditional 2D window (like iPad app)[1]
- `ImmersiveSpace` = Full 3D spatial experience
- `.full` = VR experience (no physical world visible)
- `.mixed` = Mixed reality (physical world + 3D models)[1]

[1]

***

## 🎮 Step 5: Test in Simulator

1. In Xcode toolbar, select **"visionOS Simulator"** from device dropdown
2. Press **⌘R** to build & run
3. A visionOS window will open showing your app
4. **Interact using mouse/keyboard**:
   - Click to "tap" (equivalent to pinch gesture)
   - Scroll to swipe
   - Cmd+/- to zoom[2]

> 💡 **Note**: Simulator is great for iteration, but you MUST test on real Vision Pro before releasing[3]

[4][1]

***

## 🏗️ Step 6: Add Your First 3D Model (For Virtual Gallery)

### Using Reality Composer Pro (bundled with Xcode):

1. **File → New → File → Reality Composer Pro → Reality Document**
2. Name it `GalleryScene.rp`
3. Click **"Add Item"** → Browse free 3D models or import your own (`.usdz` or `.gltf` format)
4. Position/Rotate/Scale models in the preview
5. Save → In Xcode, open `ImmersiveView.swift` and add:

```swift
import SwiftUI
import RealityKit

struct ImmersiveView: View {
    var body: some View {
        RealityView { content in
            // Load your 3D model
            if let modelEntity = try? await Entity.load(
                named: "GalleryScene",
                in: Bundle.main
            ) {
                content.add(modelEntity)
            }
        }
    }
}
```



***

## 📚 Step 7: Learn the Fundamentals (Recommended Order)

| Topic | Learning Resource |
|-------|-------------------|
| **Swift Basics** | Swift Playgrounds on iPad (free) [3] |
| **SwiftUI Fundamentals** | Paul Hudson's "100 Days of SwiftUI" (free) [11][3] |
| **visionOS Basics** | Apple's official "Creating your first visionOS app" [6] |
| **3D Models & RealityKit** | YouTube: "VisionOS Tutorial for beginner" [9] |
| **Advanced Spatial UI** | Apple Developer Documentation → visionOS [4] |

***

## 🎯 Your Virtual Gallery Next Steps

Once comfortable with basics, build your gallery:

1. Create a **Window** with a navigation stack (gallery categories)
2. Add a **Volume** for each artwork (3D frame + model)
3. Use **ImmersiveSpace** for full gallery walkthrough
4. Add hand gestures (pinch to rotate artwork)

Example 3D volume code:

```swift
@State private var isHovered = false

var body: some View {
    Volume {
        Model3D(named: "ArtworkFrame")
            .scale(effect: isHovered ? 1.1 : 1.0)
    }
    .simultaneousGesture(
        TapGesture()
            .onEnded { /* Open artwork details */ }
    )
}
```



***

## 📖 Official Apple Resources

- **visionOS Get Started Page**: developer.apple.com/visionos/get-started/[7]
- **Creating Your First App**: developer.apple.com/documentation/visionOS/creating-your-first-visionos-app[6]
- **visionOS Documentation**: developer.apple.com/visionos/[4]

***

**Ready to start?** Open Xcode and create your first project — the default template is a great starting point. Want me to help you with any specific step (like adding 3D models, creating the gallery layout, or testing in simulator)?

Sources
[1] Getting Started with Apple's Vision OS Development https://blog.learnxr.io/xr-development/getting-started-with-apple-vision-os-development
[2] Working with VisionOS | LinkedIn Learning, formerly Lynda.com https://www.linkedin.com/learning/apple-vision-pro-first-look/working-with-visionos
[3] I want ti learn how to program correctly on VisionOs - Reddit https://www.reddit.com/r/VisionPro/comments/1dwxkkx/i_want_ti_learn_how_to_program_correctly_on/
[4] visionOS - Apple Developer https://developer.apple.com/visionos/
[5] The Complete SwiftUI and Vision Pro Course - Credo Academy https://credo.academy/courses.html
[6] Creating your first visionOS app | Apple Developer Documentation https://developer.apple.com/documentation/visionOS/creating-your-first-visionos-app
[7] Get Started - visionOS - Apple Developer https://developer.apple.com/visionos/get-started/
[8] I built an Apple Vision Pro app... visionOS tutorial - YouTube https://www.youtube.com/watch?v=_xfZIr5sDLw
[9] Apple Vision Pro - YouTube https://www.youtube.com/playlist?list=PLCH753rZ9r6d5Iq4xfl0l7leTGPgLYsS8
[10] Building a 3D experience in visionOS: Windows - Create with Swift https://www.createwithswift.com/building-a-3d-experience-in-visionos-windows/
[11] visionOS Development - Everything You Need To Learn - Reality Uni https://www.realityuni.com/pages/blog?p=visionos-development-roadmap
