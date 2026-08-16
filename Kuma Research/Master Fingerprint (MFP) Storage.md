**Master Fingerprint (MFP) Storage**

  

In Keystone hardware wallets like the Keystone 3 Pro, the Master Fingerprint (MFP) is derived from the wallet's master seed (your 24-word recovery phrase). It is not stored separately but computed on-the-fly by the device's secure chips—specifically, the Microchip ATECC608B and Maxim DS28S60, which handle seed storage with hardware-level encryption.[4][5]

  

## Decryption and Seed Requirement

No decryption of the MFP itself is needed or possible, as it's a unique public identifier (like a wallet fingerprint) for verifying authenticity across devices or passphrase modes. To regenerate the exact MFP, you must use the original seed phrase on a Keystone device; without it, the MFP cannot be recreated or accessed.[5]

  

## Security Implications

The seed remains encrypted in the secure elements at all times. Passphrase wallets generate a distinct MFP from the base seed + passphrase combo, requiring re-entry each session (not stored on-device). Cloning attempts would mismatch MFPs, preventing unauthorized use.[4][5]

  

Sources

[1] Keystone Pro Hardware Wallet Setup (Quick Tutorial) https://www.youtube.com/watch?v=dAFd5GEQ8N0

[2] How to Set Up & Use the Keystone Pro Air Gapped Cryptocurrency Hardware Wallet https://www.youtube.com/watch?v=1WKdXudSmz0

[3] Fingerprint Settings https://guide.keyst.one/docs/fingerprint-settings

[4] Keystone 3 Pro Setup & Overview https://www.youtube.com/watch?v=Dgcd7fx62xs

[5] Passphrase Wallet - Keystone 3 Pro https://guide.keyst.one/docs/passphrase-wallet

[6] Keystone Hardware Wallet Feature Highlights https://keystonewallet.crisp.help/en/article/keystone-hardware-wallet-feature-highlights-t7z66y/

[7] Xverse with Keystone Hardware Wallet Support https://www.xverse.app/keystone-cold-wallet-support

[8] Understanding Crypto Wallets: A Guide for Beginners https://blog.keyst.one/understanding-crypto-wallets-a-guide-for-beginners

[9] A few questions about using a passphrase with a Keystone wallet https://www.reddit.com/r/KeystoneWallet/comments/13mjzhs/a_few_questions_about_using_a_passphrase_with_a/

[10] What is the Keystone Hardware Wallet? - Backpack Learn https://learn.backpack.exchange/articles/what-is-the-keystone-hardware-wallet