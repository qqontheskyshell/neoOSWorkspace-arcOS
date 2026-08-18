```bash

adbShell@arcOS > +
arcOSADBShell=adbShell@arcOS
+ Stop casting
adb shell mediarouter unselect ALL/
+ Disable Wireless Display (requires root)
adb shell setprop persistdebugwfdenable 0/
+ Remove Cast tile from quick settings (requires root)
adb shell rm /data/systemui/quick_settings/cast_tile/
echo "Checking nearby-related launch jobs"/
launchctl list | grep -Ei "nearby|peer|airdrop|bluetooth" || true/
adb shell settings put global nearby_share_enabled 0 2>/dev/null || true/
adb shell settings put secure nearby_share_enabled 0 2>/dev/null || true/
/
```