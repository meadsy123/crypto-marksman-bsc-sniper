# Crypto Marksman BSC Sniper - Pancakeswap V2
A Pancakeswap V2 listing sniper bot on the bincance smart chain, includes a simple GUI and much more.

If you have any questions or inquiries, you can contact me via telegram: <b>@meadzy</b>

<H2>Prerequisites</H2>

- A Hot wallet address (not attached to closed exchange) and private key. Metamask is the best option as trust wallet doesn't provide private key.
- A Windows machine x64

<H2>How to create an account on Metamask</H2>

You will need to setup your wallet and connect to the binance smart chain... Follow this guide for metamask.

https://medium.com/stakingbits/setting-up-metamask-for-binance-smart-chain-bsc-921d9a2625fd

<br> </br>
<H2>Getting started</H2>

0. Read prerequisites

1. Download the source code from the latest release.


2. Open "configfile.py" (with notepad for instance) and add your bsc wallet address and private key at the bottom of the file between the quotation marks('').

<pre>...
my_address = ''
my_pk = ''
</pre>

3. Run "main.exe"

- Make sure the three files are in the same folder otherwise this program will not run.

4. Edit settings accordingly using the user interface or configfile.

<br> </br>
<H2>Functions</H2>

<b>Get Total Wallet Balance</b>: A list of tokens that are listed in the tokens.json are used to retrieve the token balance from your wallet and the token price to calculate your total price from pancakswap. 

<b>Check Latency</b>: This function will ping the blockchain and provide the latency in ms. The less time it takes to talk to the blockchain the quicker you can complete transaction and possibly be able to get a better entry price point.

<b>Selected token price/balance</b>: This function starts automatically when the program starts running, it continually retrieves the price and balance of the selected token and BNB price which is then displayed at the bottom of the interface. The percentage increase is also calculated using the field "tokenstartprice" compared to the current price.

<b>Start/Snipe</b>: If the liquidty check toggle is set to true, a concurrent thread is created...Firstly, the bot will check if the selected pair contract is avaiable on the pancakeswap factory (for example SAFEMOON/WBNB), and then start continuosloy checking if liquidity is available on the panacakeswap router. Once liquidity is available the trade function is called. If the liquity check toggle is set to false, the trade function will start right away.

<b>Stop</b>: This will stop all threads currently running, for example when you start the program and you are waiting for liquidity. If you click stop the thread will be killed. This also includes the price/balance thread which runs in the background. (restart program to begin price/balance thread again)

<H2>Fields</H2>

<b>Selected Token</b>: The dropdwon will be populated from the tokens list set in tokens.json, once selected the token fields will be automatically populated. Make sure you have the correct token decimals otherwise this can affect the price/balances and your trades. You can find the decimals by going to https://bscscan.com/ and looking up the token address.

<b>Trade Action</b>: There are 3 trade actions you need to be aware of
1. BUY - a buy transaction will be created, using the token selected. The trade will consist of trading BNB for the selected token.
2. SELL - a sell transaction will be created, the trade consist of the selected token for BNB.
3. BUY/SELL - A buy transaction will be created, then the fields/settings will depend on what instance a sell transaction will be created.

<b>BNB to trade</b>: How many BNB do you wish to use for the transaction.

<b>Token start price</b>: The price used to get the price percentage increase in the price thread which populates the prices/balances at the bottom of the program.

<b>Tokens to trade</b>: The exact amount of tokens you wish to buy.

<b>Token to buy</b>: Instead of using the "BNB to trade" which will get as many tokens as possible, this field will use the exact output and calculate the amount of BNB that will be used in the trade at that given time

<b>Max overall slippage</b>
The max slippage you want the bot to handle. Can be set from 1 to 100%. 100%= the bot only will
accept a trade if the minimal amount of tokens it gets is 0 (=always accepting).
Slippage is the expected % difference between these quoted and executed prices. Low liquidity can
also cause increased slippage, which is why larger orders tend to face higher slippage.

<b>Gas limit</b>
Please set this at 500000, so an order will never fail because you didn’t accept a higher gas.

<b>GWEI fee to use for trade</b>
This field is the amount of GWEI (fee) you want to use for a trade. For sniping you want to keep this much higher than normal trading, so the block is mined as fast as possible. I recommend using more than 20 when sniping maybe even more. (normal trading is done at 5 GWEI). How much higher depends on the token (how
much people are going to snipe), your latency with the RPC and if you really want to compete with
the fastest guys, or just don’t want to make a profit. The fastest snipes use the highest GWEI and are
only worth it when you play with a lot of BNB.

<H3>Buy</H3>

<b>Different deposit address</b>: Use this if you want the swap output to go to a different wallet address. There is a toggle for true/false and a field in config.py for the different address.

<b>Liquidity Check</b>: If the liquidty check toggle is set to true, a concurrent thread is created to continuosly check the liquidity. Firstly, the bot will check if the selected  pair contract is avaiable on the exchange factory contract for example (WBNB/SAFEMOON), if true the loop will start checking if the liquidity is available on the exchange router. Once liquidity is available the trade function is called as fast as possible. If the liquity check toggle is set to false, the trade function will start straight away. <b> This is not available on the demo due to testnet Pancakeswap factory contract not working.</b>

<b>Liquidity Speed</b>: The amount of time the bot has to wait per liquidity check. If this is set at 0ms, its fine.

<b>Only buy if price is less than </b>
This so you wont buy a token for too much $. Especially handy for failing buy orders due to too less
slippage or GWEI and for scam launches/IDO’s which add a token for too much $.

<H3>Sell</H3>

<b>Custom Slippage for selling</b>
The max slippage you want the bot to use when selling. Can be set from 1 to 100%. 100%= the bot only will
accept a trade if the minimal amount of tokens it gets is 0 (=always accepting).
Slippage is the expected % difference between these quoted and executed prices. Low liquidity can
also cause increased slippage, which is why larger orders tend to face higher slippage.

<b>Tokens to sell</b>: The exact amount of tokens you wish to sell for BNB.

<b>Amount of seconds to wait until sell</b>
This field is used for the time between the buy transaction and the sell transaction.

<b>Sell when token price is more than</b>
The price will be checked continously until this price is greater than the buy price. At that point a sell transaction will ber created. slippage and fees will still apply.

<b>Sell when token price is % higher than buy</b>
The price will be checked continously until this price is greater the specified percentage higher than the buy price. At that point a sell transaction will be creates. slippage and fees will still apply.

<H2>Buttons</H2>

<b>Wallet Balance</b>: A list of tokens that are listed in the tokens.json are used to retrieve the token balance from your wallet and the token price to calculate your total price from pancakswap. 

<b>Start</b>: A thread is created which the sniping bot will run on. please be aware every click will create a new thread and therefore a new transaction.

<b>Stop</b>: Stops all concurrent threads, includes buy/sell transaction threads or price/balance thread.

<b>Check Latency</b>: The time taken for you to receive a response from the blockchain.

<H2>Logging and Reports</H2>

There is more extensive reporting/logging in the if you turn debug mode on, either using the GUI or by setting debugmode='1' in the configfile.py.

The logging is added to logs/console.log in the directory of the release.

All transactions data is added to the json/transactions.json file

![image](https://user-images.githubusercontent.com/16119958/131032421-ad2e3071-4deb-4086-ad57-60b2953ee25f.png)

Once you have the tx you can search your transactions up on 'https://bscscan.com/tx/ADD_YOUR_TX_HASH_HERE'


<H2>Common Errors</h2>

- Transaction is not in sync with the chain. This is due to either a processing transaction using the same nonce as the current transaction or your nonces are out of sync. simple solution send your 0 using a custom nonce (get the last nonce from tx list and add 1). this should reset your nonce.
- "Returned error: replacement transaction underpriced" 
  1. You have a pending transaction from your account
  2. The new transaction you are sending has the same nonce as that pending transaction
  3. The new transaction you sent has a gas price that is too small to replace the pending transaction
  
- 'transaction underpriced' Or your GWEI is too low or your max gas is too low.For max gas 700k (700000) is advisable, this way a transaction will never fail because of gas.

-'insufficient funds for gas * price + value', You didn’t have enough bnb on your account for the trade. transaction fee in bnb= (gwei* gas)* 0.000000001
- 'already known', This is the error you get when the bot was trying to approve a token, but that token was already approved in the end. 
- SSL errors. This is a problem is possibility that your vpn, anti-virus or firewall is blocking the bot.


<H2>BSC Errors</h2>
- Fail with error TransferHelper: ‘TRANSFER_FROM_FAILED’ ‘max gas' was too low. Please set the max-gas at 700k to be sure it never fails because of that.

<br> </br>
<H2>To do list</H2>

- Add multiple exchanges to choose from. uniswap, sushiswap etc
- create multiple bots for all blockchains. eth, matic, solana etc

<br> </br>
<H2>Author</H2>

If you have any questions you can contact me via telegram: @meadzy
<br> </br>
Donations: 0x4B4fB57652F1B87db1dC88e1E2Fbb85c85a60895

<br> </br>
<H2>Disclosure</H2>
Use the application at your own risk, I am not in any way responsible for losses.
