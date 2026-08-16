`plutil -lint` tells you whether a plist-style file is syntactically valid and parsable, and it returns a non‑zero exit code if there is an error.[1][2]

## What `plutil -lint` does

- `plutil` is the Property List Utility on macOS for reading, converting, and validating plist and related files like `.plist`, `.strings`, and `.mobileconfig`.[2][1]
- The `-lint` operation “verifies the plist can be parsed,” i.e., it checks the file’s syntax and structure and then exits with status `0` for OK, `1` on failure.[3][1]

Example:

```markdown
plutil -lint wifi-profile.mobileconfig
```

- If the file is valid, it prints something like `wifi-profile.mobileconfig: OK` and exits `0`, which is perfect for use in scripts (`if plutil -lint file; then ...`).[4][2]
- If there is a syntax error (unbalanced tags, bad XML, invalid plist structure), it prints an error message pointing at the problem and exits with non‑zero, so your markdown script can fail fast.[1][4]

In the context of the `.mobileconfig` generator, it’s just a quick sanity check that the XML your markdown script emitted is a valid property list that Configurator and iOS/macOS will accept.[5][6]

Do you want a version of the generator script that treats `plutil -lint` failure as a hard error and logs a more detailed message for CI/CD?

Sources
[1] PLUTIL(1) https://keith.github.io/xcode-man-pages/plutil.1.html
[2] plutil - LOOBins https://www.loobins.io/binaries/plutil/
[3] plutil(1) - Arch manual pages https://man.archlinux.org/man/extra/gnustep-base/plutil.1.en
[4] Check if Localizable.strings file is valid https://stackoverflow.com/questions/32134870/check-if-localizable-strings-file-is-valid/32135046
[5] Configuration Profiles https://support.apple.com/guide/deployment/intro-to-device-management-profiles-depc0aadd3fe/web
[6] Mobile Device Configuration Profiles - Jamf https://learn.jamf.com/r/en-US/jamf-pro-documentation-current/Mobile_Device_Configuration_Profiles
[7] Plutil – apfelwiki.de http://www.apfelwiki.de/Main/Plutil
[8] Editing Property Lists with plutil - Scripting OS X https://scriptingosx.com/2016/11/editing-property-lists/
