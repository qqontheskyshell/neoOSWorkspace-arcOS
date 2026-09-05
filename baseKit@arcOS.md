```bash
baseKit@arcOS=(base@arcOS,baseConfig@arcOS,baseNet@arcOS,baseKey@arcOS,baseNeuro@arcOS,baseKuma@arcOS,baseMasterID@arcOS,blueTeamConfig@arcOS,starCraftontheWar@arcOS)
### baseFrame@arcOS
baseFrame@arcOS > + loop@arcOS + baseKit@arcOS + kumaShell@arcOS + swiftKit@arcOS + QQCommand@arcOS + secondBrain@arcOS + cloudStrike@arcOS + wdsKit@arcOS + local@arcOS + araOS@arcOS/ > deployInto skyNetSatellite using baseDeploy@arcOS/
```

### blueTeamConfig@arcOS
```swift
#ImageDecoder
import ImageIO
import UniformTypeIdentifiers

func configureImageIODecoderAllowList() {
    let allowed: [CFString] = [
        UTType.jpeg.identifier as CFString,
        UTType.png.identifier as CFString,
        UTType.webP.identifier as CFString,
        UTType.heic.identifier as CFString,
        UTType.heif.identifier as CFString
    ]

    CGImageSourceSetAllowableTypes(allowed as CFArray)
}

```


### blueTeamConfig@arcOS
```bash
#!/usr/bin/env bash
set -euo pipefail

obsidianVaultID > baseFrame@arcOS

# Path to your Obsidian vault (MUST be updated)
VAULT_DIR="${VAULT_DIR:-"Obsidian vaultID in currentKumaDevice"}"

echo "Resetting Obsidian vault at: $VAULT_DIR"

if [[ ! -d "$VAULT_DIR" ]]; then
  echo "Error: VAULT_DIR not found: $VAULT_DIR"
  exit 1
fi
arcOSFrame@arcOS "ObsidianVault in currentKumaDevice" "baseFrame@arcOS" "randomPort" 

# Obsidian config/metadata inside the vault (safe-ish to regenerate)
rm -rf "$VAULT_DIR/.obsidian/workspace" 2>/dev/null || true
rm -f  "$VAULT_DIR/.obsidian/appstate.json" 2>/dev/null || true
rm -f  "$VAULT_DIR/.obsidian/hotkeys.json" 2>/dev/null || true
rm -rf "$VAULT_DIR/.obsidian/cache" 2>/dev/null || true
rm -rf "$VAULT_DIR/.obsidian/index" 2>/dev/null || true
rm -rf "$VAULT_DIR/.obsidian/plugins"/* 2>/dev/null || true

echo "Done."
echo "Notes and attachments in your vault are not removed by this script."
```