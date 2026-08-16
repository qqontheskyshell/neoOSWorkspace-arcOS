The iPad Boot ROM (also called SecureROM) is the ==immutable, read-only memory on the processor chip==. It runs the very first code when your device turns on, handling initial hardware setup and verifying the integrity of the iOS/iPadOS bootloader before handing control over to the OS. [[1](https://support.apple.com/guide/security/boot-process-for-ipad-and-iphone-devices-secb3000f149/web), [2](https://www.theiphonewiki.com/wiki/bootrom), [3](https://www.l9group.com/research/bootrom-versus-bootloader/), [4](https://support.apple.com/ja-jp/guide/security/secb3000f149/web), [5](https://support.apple.com/en-gb/guide/security/secb3000f149/web)]

Key Functions

- **Chain of Trust:** It validates the cryptographic signature of the iBoot bootloader using Apple's Root certificate, ensuring the device only loads authentic Apple software. [[1](https://support.apple.com/guide/security/boot-process-for-ipad-and-iphone-devices-secb3000f149/web)]
- **DFU Mode Access:** If the standard boot fails or is interrupted, the Boot ROM forces the iPad into **Device Firmware Upgrade (DFU) mode**, which bypasses the operating system to allow for restoration via a computer. [[1](https://support.apple.com/en-in/guide/security/secb3000f149/web), [2](https://support.apple.com/en-au/guide/security/secb3000f149/web), [3](https://www.businessinsider.com/reference/dfu-mode)]

The Boot ROM Exploits

Because Boot ROM code is permanently burned into the processor during manufacturing, it cannot be patched via software updates. [[1](https://wired.jp/2019/09/29/ios-exploit-jailbreak-iphone-ipad/), [2](https://www.reddit.com/r/jailbreak/comments/d9zudc/discussion_the_bootrom_exploit_in_laymans_terms/), [3](https://www.l9group.com/research/bootrom-versus-bootloader/)]

- **Checkm8:** Hardware exploits like _checkm8_ take advantage of unpatchable vulnerabilities in older processor Boot ROMs (ranging from the Apple A5 to A11 chips). [[1](https://blog.elcomsoft.com/2025/11/exploring-ipados-tvos-and-audioos-17-and-18-devices-file-system-and-keychain-extraction/), [2](https://zenn.dev/su8/articles/d7f8947cbbef39?locale=en), [3](https://www.reddit.com/r/jailbreak/comments/d9zudc/discussion_the_bootrom_exploit_in_laymans_terms/)]
- **Jailbreaking:** This allows researchers and tinkerers to gain deep-level hardware control, permanently bypassing restrictions, dual-booting alternative software, or bypassing activation locks on compatible, older-generation iPads. [[1](https://www.youtube.com/watch?v=KOTof8WwFbE)]

For more technical details about the iPad's boot process and the Chain of Trust:

- Read the [Apple Support Guide](https://support.apple.com/guide/security/boot-process-for-ipad-and-iphone-devices-secb3000f149/web) for the full breakdown.
- Visit [The iPhone Wiki](https://www.theiphonewiki.com/wiki/bootrom) for historical data on Apple's bootroms and specific hardware exploits.

If you are trying to recover a frozen or unresponsive iPad, let me know the **exact iPad model** you are using. I can provide the specific button combinations to safely trigger **Recovery Mode** so you can restore the device.