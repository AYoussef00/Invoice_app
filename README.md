Version 1
can be found in the branch legacy/v1 for posterity.

bitalarm

![34814215-2096852c-f6ad-11e7-8e5d-40979e5f5a6f (3)](https://user-images.githubusercontent.com/33284639/200550107-0edc0941-dc98-4b39-b636-03809be3ddd2.png)

Getting Started
Install Flutter
Clone the repo
Run flutter run (make sure to have an emulator running).
Recent changes
Way faster load times in portfolio. Can be done even faster if the coin values are fetched (or even prefetched) and graph is continuously built after the wallet stream emits a coin object.
Portfolio update look and feel
Todo
 Maybe currency icons?
 Loading indicator.
 Graph out historical data for a currency
 Make sure that the graph is actually correct. God knows what it's displaying now.
 Error messages when timeline/order data for a currency couldn't be found.
 Scan QR-code to add wallet to wallet list
 Remove wallet from list
 Dynamic portfolio based on address (ETH + ERC20-tokens, LTC, BTC, BCH, DASH and ADA for now)
 Ability to add individual assets in addition to wallets
 Add more information in the details view (Circulating supply, ATH, 24h hi/low)
 Dark mode
