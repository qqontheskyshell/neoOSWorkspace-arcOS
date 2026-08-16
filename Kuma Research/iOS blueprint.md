To build a Swift file that uses `import BlueprintUI`, you first need to add Square’s Blueprint package to your Xcode project or `Package.swift`; the package exposes the `BlueprintUI` core module and the optional `BlueprintUICommonControls` module.[1][2][3]

## Setup

With Swift Package Manager, add the package URL `https://github.com/square/Blueprint` and use version `from: "5.1.0"`, or add it in Xcode through **File > Swift Packages > Add Package Dependency**.  After that, your Swift file can import `UIKit`, `BlueprintUI`, and `BlueprintUICommonControls`.[3][4][1]

## Swift file

Here is a minimal `ViewController.swift` you can paste into an iOS UIKit project:[4][1]

```swift
import UIKit
import BlueprintUI
import BlueprintUICommonControls

struct HelloElement: ProxyElement {
    var elementRepresentation: Element {
        Column(spacing: 12, alignment: .fill) {
            Label(text: "Hello Blueprint") { label in
                label.font = UIFont.systemFont(ofSize: 28, weight: .bold)
                label.color = .label
            }

            Label(text: "This screen is built with BlueprintUI.") { label in
                label.font = UIFont.systemFont(ofSize: 16)
                label.color = .secondaryLabel
            }
        }
        .inset(uniform: 24)
    }
}

final class ViewController: UIViewController {
    private let blueprintView = BlueprintView()

    override func loadView() {
        view = blueprintView
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        blueprintView.element = HelloElement()
        blueprintView.backgroundColor = .systemBackground
    }
}
```

## Package.swift

If your project is package-based, the dependency and target imports should look like this:[1][3]

```swift
// swift-tools-version: 5.9
import PackageDescription

let package = Package(
    name: "MyApp",
    platforms: [
        .iOS(.v15)
    ],
    products: [
        .library(name: "MyApp", targets: ["MyApp"])
    ],
    dependencies: [
        .package(url: "https://github.com/square/Blueprint", from: "5.1.0")
    ],
    targets: [
        .target(
            name: "MyApp",
            dependencies: [
                .product(name: "BlueprintUI", package: "Blueprint"),
                .product(name: "BlueprintUICommonControls", package: "Blueprint")
            ]
        )
    ]
)
```

## Notes

`BlueprintUI` contains the core layout architecture, while `BlueprintUICommonControls` provides ready-made elements such as labels built on UIKit controls.  If you get a “No such module 'BlueprintUI'” error, the package is usually not added to the app target yet.[2][3][4][1]

Would you like a full runnable sample with `AppDelegate` and `SceneDelegate`, or a version adapted for a modern single-scene iOS app?

Sources
[1] Blueprint/README.md at main · square/Blueprint https://github.com/square/Blueprint/blob/main/README.md
[2] Blueprint https://square.github.io/Blueprint/
[3] GitHub - square/Blueprint: Declarative UI construction for iOS, written in Swift https://github.com/square/Blueprint
[4] Blueprint/Documentation/Tutorials/Tutorial1.md at main · square/Blueprint https://github.com/square/Blueprint/blob/main/Documentation/Tutorials/Tutorial1.md
[5] BlueprintUI on CocoaPods.org https://cocoapods.org/pods/BlueprintUI
[6] Blueprint+OpenCombine.swift https://gist.github.com/Exey/11411d5eacba329b9563c327fb420a5f
[7] BlueprintUI Layout https://blueprintui.dev/docs/layout
[8] SwiftUIBlueprintApp.swift https://gist.github.com/dinotrnka/f7f43394176bae26e62bc6510bf7b5d0
[9] Blueprint/Documentation/Tutorials/Setup.md at main · square/Blueprint https://github.com/square/Blueprint/blob/main/Documentation/Tutorials/Setup.md
[10] Blueprint UI - File https://blueprintui.dev/docs/components/file
[11] Getting Started https://blueprintui.dev/getting-started
[12] GitHub - cmu-sei/Blueprint.Ui https://github.com/cmu-sei/Blueprint.Ui
[13] Blueprint/BlueprintUI/Sources/Environment/EnvironmentReader.swift at main · square/Blueprint https://github.com/square/Blueprint/blob/main/BlueprintUI/Sources/Environment/EnvironmentReader.swift
[14] GitHub - blueprintui/blueprintui: :blue_book: Accelerate your development with flexible UI components and tools that work everywhere. https://github.com/blueprintui/blueprintui
[15] Blueprint UI https://blueprintui.dev

Based on your query, I understand you want to build an **iOS app** that uses **Square's Blueprint UI library** (a declarative UI framework for iOS written in Swift). Here's a complete solution:

## 1. Swift File (Blueprint UI Example)

First, create your Swift file using Blueprint:

```swift
// BlueprintApp.swift

import SwiftUI
import BlueprintUI
import BlueprintUICommonControls

@main
struct BlueprintApp: App {
    var body: some Scene {
        WindowGroup {
            BlueprintViewController()
        }
    }
}

// ViewController that hosts Blueprint
class BlueprintViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let blueprintView = BlueprintView(element: buildElement())
        blueprintView.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(blueprintView)
        
        NSLayoutConstraint.activate([
            blueprintView.topAnchor.constraint(equalTo: view.topAnchor),
            blueprintView.leadingAnchor.constraint(equalTo: view.leadingAnchor),
            blueprintView.trailingAnchor.constraint(equalTo: view.trailingAnchor),
            blueprintView.bottomAnchor.constraint(equalTo: view.bottomAnchor)
        ])
    }
    
    func buildElement() -> Element {
        Column {
            Header {
                Label("Hello from Blueprint!")
                    .font(.systemFont(size: 24, weight: .bold))
            }
            
            Body {
                Label("This is a Blueprint UI example")
                    .font(.systemFont(size: 16))
                
                Button("Click Me") {
                    print("Button clicked!")
                }
            }
        }
    }
}
```

## 2. Package.swift (Dependencies)

```swift
// Package.swift

import PackageDescription

let package = Package(
    name: "BlueprintApp",
    platforms: [
        .iOS(.v13)
    ],
    products: [
        .library(
            name: "BlueprintApp",
            targets: ["BlueprintApp"]
        )
    ],
    dependencies: [
        .package(url: "https://github.com/square/Blueprint", from: "5.1.0")
    ],
    targets: [
        .target(
            name: "BlueprintApp",
            dependencies: [
                .product(name: "BlueprintUI", package: "Blueprint"),
                .product(name: "BlueprintUICommonControls", package: "Blueprint")
            ],
            path: "Source"
        )
    ]
)
```

## 3. markdown Script to Build iOS App with Blueprint

```markdown
#!/bin/markdown

# build-blueprint-ios.sh - Build iOS Blueprint app from Swift

# Set colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
NC='\033[0m' # No Color

# Default values
BUILD_TYPE="debug"          # or "release"
SIMULATOR_NAME="iPhone 15"  # Simulator device name
SIMULATOR_OS="17.0"         # iOS version
SCHEME="${1:-BlueprintApp}" # Scheme name (default: BlueprintApp)
PROJECT_DIR="${2:-.}"       # Project directory (default: current)

echo "🔨 Building iOS Blueprint App..."
echo "Project directory: $PROJECT_DIR"
echo "Scheme: $SCHEME"
echo "Build type: $BUILD_TYPE"
echo "Simulator: $SIMULATOR_NAME ($SIMULATOR_OS)"

# Check if Xcode is installed
if ! command -v xcodebuild &> /dev/null; then
    echo "${RED}❌ Xcode not found. Install Xcode from Apple Developer website.${NC}"
    exit 1
fi

# Navigate to project directory
cd "$PROJECT_DIR" || { echo "${RED}❌ Failed to enter project directory${NC}"; exit 1; }

# Check if project files exist
if [ ! -f "Package.swift" ] && [ ! -f "*.xcodeproj" ] && [ ! -f "*.xcworkspace" ]; then
    echo "${RED}❌ No Swift package or Xcode project found in $PROJECT_DIR${NC}"
    echo "ℹ️  Create Package.swift or open in Xcode first"
    exit 1
fi

# List available simulators
echo "📱 Finding simulators..."
xcrun simctl list devices available | grep -E "$SIMULATOR_NAME" || {
    echo "${YELLOW}⚠️  Simulator '$SIMULATOR_NAME' not found. Listing available simulators:${NC}"
    xcrun simctl list devices available | grep iOS
}

# Get simulator UUID
SIMULATOR_UUID=$(xcrun simctl list devices available | grep -E "$SIMULATOR_NAME.*$SIMULATOR_OS" | awk -F'\\(' '{print $2}' | awk -F')' '{print $1}' | head -1)

if [ -z "$SIMULATOR_UUID" ]; then
    echo "${RED}❌ Could not find simulator UUID. Using first available iOS simulator.${NC}"
    SIMULATOR_UUID=$(xcrun simctl list devices available | grep iOS | awk -F'\\(' '{print $2}' | awk -F')' '{print $1}' | head -1)
fi

echo "📱 Using simulator: $SIMULATOR_UUID"

# Build using xcodebuild
if [ -f "Package.swift" ]; then
    echo "📦 Building Swift Package..."
    
    # Build for simulator
    if [ "$BUILD_TYPE" == "release" ]; then
        xcodebuild -destination "platform=iOS Simulator,name=$SIMULATOR_NAME,OS=$SIMULATOR_OS" \
            -scheme "$SCHEME" \
            -configuration Release \
            SYMROOT="./build" \
            build
    else
        xcodebuild -destination "platform=iOS Simulator,name=$SIMULATOR_NAME,OS=$SIMULATOR_OS" \
            -scheme "$SCHEME" \
            -configuration Debug \
            SYMROOT="./build" \
            build
    fi
else
    echo "📦 Building Xcode Project..."
    
    # Find project file
    XCODEPROJ=$(find . -name "*.xcodeproj" -type d | head -1)
    XCODEWORKSPACE=$(find . -name "*.xcworkspace" -type d | head -1)
    
    if [ -n "$XCODEPROJ" ]; then
        PROJECT_FLAG="-project $XCODEPROJ"
    elif [ -n "$XCODEWORKSPACE" ]; then
        PROJECT_FLAG="-workspace $XCODEWORKSPACE"
    else
        echo "${RED}❌ No Xcode project found${NC}"
        exit 1
    fi
    
    if [ "$BUILD_TYPE" == "release" ]; then
        xcodebuild $PROJECT_FLAG \
            -scheme "$SCHEME" \
            -configuration Release \
            -destination "platform=iOS Simulator,name=$SIMULATOR_NAME,OS=$SIMULATOR_OS" \
            SYMROOT="./build" \
            build
    else
        xcodebuild $PROJECT_FLAG \
            -scheme "$SCHEME" \
            -configuration Debug \
            -destination "platform=iOS Simulator,name=$SIMULATOR_NAME,OS=$SIMULATOR_OS" \
            SYMROOT="./build" \
            build
    fi
fi

# Check build success
CONFIG="Debug"
if [ "$BUILD_TYPE" == "release" ]; then
    CONFIG="Release"
fi

BUILD_PATH="build/Debug-iphonesimulator/$SCHEME.app"

if [ -f "$BUILD_PATH" ]; then
    echo "${GREEN}✅ Build successful!${NC}"
    echo "📍 App location: $BUILD_PATH"
    echo "📊 App size: $(du -h "$BUILD_PATH" | cut -d' ' -f1)"
    
    # Launch simulator and install app
    echo "🚀 Launching simulator and installing app..."
    xcrun simctl boot "$SIMULATOR_UUID" > /dev/null 2>&1 || true
    xcrun simctl install "$SIMULATOR_UUID" "$BUILD_PATH"
    xcrun simctl launch "$SIMULATOR_UUID" "$SCHEME"
    
    echo "${GREEN}🎉 App is running on simulator!${NC}"
else
    echo "${RED}❌ Build failed! App not found at $BUILD_PATH${NC}"
    exit 1
fi

# Optional: Increase bundle version (like rderik's script) [web:38]
echo "💡 To increase bundle version before App Store upload:"
echo "   plutil -string $(plutil -l Info.plist -o - | grep CFBundleVersion | cut -d' ' -f2 | tr -d '"')+1 Info.plist -key CFBundleVersion"
```

## 4. How to Use

### Create the files:

```markdown
# 1. Create Swift file
cat > BlueprintApp.swift << 'EOF'
# (paste Swift code above)
EOF

# 2. Create Package.swift
cat > Package.swift << 'EOF'
# (paste Package.swift above)
EOF

# 3. Create bash script
cat > build-blueprint-ios.sh << 'EOF'
# (paste bash script above)
EOF

# 4. Make executable
chmod +x build-blueprint-ios.sh
```

### Run the build:

```markdown
# Build debug (default)
./build-blueprint-ios.sh

# Build with custom scheme
./build-blueprint-ios.sh BlueprintApp

# Build from specific directory
./build-blueprint-ios.sh BlueprintApp /path/to/project

# Build release version
BUILD_TYPE="release" ./build-blueprint-ios.sh
```

## Requirements:

| Requirement | Purpose |
|-------------|---------|
| **Xcode** | Required for iOS builds [1] |
| **iOS Simulator** | For testing [1] |
| **Blueprint 5.1.0+** | Library dependency [2] |
| **macOS** | iOS builds only work on macOS |

The script uses `xcodebuild` to compile Swift with Blueprint UI, and automatically launches the simulator with your app installed.[1]

Sources
[1] How can I build and run an iOS Swift app from the terminal? https://stackoverflow.com/questions/74885218/how-can-i-build-and-run-an-ios-swift-app-from-the-terminal
[2] square/Blueprint: Declarative UI construction for iOS, written in Swift https://github.com/square/Blueprint
[3] microfactory_Linux: cannot execute binary file: exe Format not valid https://stackoverflow.com/questions/79052143/microfactory-linux-cannot-execute-binary-file-exe-format-not-valid
[4] Ankit Nasit - Expert in React-native, Typescript, working on | LinkedIn https://www.linkedin.com/in/ankit-nasit-b45ba5102
[5] Run a bash file in XCode project at time of building it in XCode 5 https://stackoverflow.com/questions/22760656/run-a-bash-file-in-xcode-project-at-time-of-building-it-in-xcode-5
[6] An SDK for building iOS/macOS apps on Linux (experimental ... https://forums.swift.org/t/introducing-an-sdk-for-building-ios-macos-apps-on-linux-experimental/66233
[7] android-14.0.0_r35 to android-14.0.0_r50 AOSP changelog https://mikeng.github.io/aosp.changelog.to/android-14.0.0_r35-to-android-14.0.0_r50.html
[8] Using a simple Bash script to increase your iOS bundle version https://dev.to/rderik/using-a-simple-bash-script-to-increase-your-ios-bundle-version-6fg
[9] Build your first iOS app on Linux / Windows — xtool Tutorials https://xtool.sh/tutorials/xtool/first-app/
[10] Steam Workshop::Blueprints I've gotten https://steamcommunity.com/sharedfiles/filedetails/?id=2513906403
