---
layout: post
title:  "Samourai Wallet collects more sensitive infomation than  Wasabi Wallet"
date:   2023-04-03 18:30:38 +0000
categories: bitcoin privacy
---
Bellow I'll argue that, assuming surveillance from the central coordinators of the coinjoin protocols provided by the developers of these two wallets and possible collusion with chain surveillance coporations, **Samourai Wallet collects way more sensitive information about their users than ZkSnacks from users of the Wasabi Wallet**.

-----

<br>

Let's take two average bitcoin spenders, Alice and Bob, and compare the information leakage the two suffer by using Samourai Wallet and Wasabi Wallet.

They both intially bought bitcoin on a centralised exchange and after listening to [Citadel Dispath with Odell and BitcoinQ_A](https://citadeldispatch.com/cd43), they want to take steps towards a more private use of their bitcoin.

## How the apps are distrubted
Samourai Wallet is a mobile app exclusively on Android. Its Google Play Store page counts at least 100k downloads.

Alice goes the Google Play Store and downloads the Samourai Wallet app. She doesn't have the know-how to verify whether the binary that she will be running is the result from the open source code displayed on [Gitlab](https://code.samourai.io/wallet/samourai-wallet-android/-/tree/develop). And even if she, she couldn't verify it because the Samourai Wallet binary on the Play Store [isn't reproduceble](https://walletscrutiny.com/android/com.samourai.wallet/). Meaning that we all have to trust the person publishing the binary on the Google Play Store that said binary is the result of the open source code available and that it doesn't have any malicious code.

Alice has to trust the Samourai Wallet developers that the Google Play Store binary doesn't have any hidden features that can be detrimental to her privacy.

Now let's say Bob is in a similar position as Alice but chose Wasabi Wallet by ZkSnacks.

He also can't verify the integrity of the binary he downloads from the Wasabi Wallet website but he knows that the code is open source and that the are users besides the Wasabi Wallet developers that[ have verified the binaries](https://bitcoinbinary.org/) available on the website.

## What information the clients communicate to the developers
Once the app is installed, Alice runs the app and because she doesn't run a node of her own to verify her bitcoin transfers, she chooses to querie Samourai Wallet's servers for her balance. In doing this she will be trusting them with the information regarding all the future utxos in her wallet. The app sends all of Alice's Xpubs (master key to derive all possible addresses from a wallet) to Samourai's servers.

From now on Samourai can analyze the provenance Alice's utxos. Whenever she uses the Whirlpool protocol to coinjoin on her phone, no matter how many remixes she wants, Samourai Wallet still will be able to link her unmixed outputs to the mixed ones as they are the ones she queries for balance.

On the other side, Bob installs the wallet and opens it. Without Bob needing to understand, the wallet runs over TOR and makes use of [Compact Block Filters (BIP 157-158)](https://docs.wasabiwallet.io/FAQ/FAQ-UseWasabi.html#what-are-bip-158-block-filters) to serve him information regarding his balance. This means that ZkSnacks servers don't get any privileged access to any sensitive information regarding Bob's utxos.

However, once Bob starts using Wasabi's coinjoin protocol, [ZkSnacks will check if any of Bob's utxos registered for coinjoin is on the blacklist they need to heed to](https://blog.wasabiwallet.io/zksnacks-blacklisting-update/). 

## Conclusion
The way the Samourai Wallet is distributed and the way the app contacts its developer's servers for balance make Samourai Wallet a bigger honey pot than ZkSnacks.

Now there are alot of nuance to be added downstream from this fact - you can run your own node, you can use the Whirlpool protocol with Sparrow Wallet, you are subject to sybil attacks from both coordinators , etc - but the fact remains, at present, **Samourai Wallet collects way more sensitive information from their clients than ZkSnacks can**.