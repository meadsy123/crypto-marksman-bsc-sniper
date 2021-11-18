# Crypto Marksman - Pancakeswap V2 BSC
A Pancakeswap V2 listing sniper bot on the bincance smart chain, includes a simple GUI and much more.

If you have any questions or inquiries, you can contact me via telegram: <b>meadsy</b>

<H2>Prerequisites</H2>

- An BSC address
- A Windows machine x64

<br> </br>
<H2>Getting started</H2>

0. Read prerequisites

1. Download the latest release or download "configfile.py", "tokens.json", "main.exe" from the repository.


2. Open "configfile.py" (with notepad for instance) and add your ethereum address and personal key at the bottom of the file between the quotation marks('').

<pre>...
my_address = ''
my_pk = ''
</pre>


3. Run "main.exe"

- Make sure the three files are in the same folder otherwise this program will not run.


5. Edit settings according to choice.


<br> </br>
<H2>Functions</H2>


<b>Get Total Wallet Balance</b>: A list of tokens that are listed in the tokens.json are used to retrieve the token balance from your wallet and the token price to calculate your total price from pancakswap. 

<b>Get Token Balance</b>: The balanace/price is retrieved from the token that is either selected from the token dropdown in the GUI or is specificed in the configfile.py.

<b>Snipe</b>: If the liquidty check toggle is set to true, a concurrent thread is created to continuosly check the liquidity. Firstly, the bot will check if the selected  pair contract is avaiable on the pancakeswap factory contract (for example SAFEMOON/WBNB), if true the loop will start which will then check if the liquidity is available on the panacakeswap router for that specificed contract. Once liquidity is available the trade funcdtion is called. If the liquity check toggle is set to false, the trade function will start.


<H2>Fields</H2>


<b>How fast liquidity checking</b>
The amount of time the bot has to wait per liquidity check. If this is set at 0ms, its fine.

<b>Only buy if price is less than (limit buy)</b>
This so you wont buy a token for too much $. Especially handy for failing buy orders due to too less
slappage or GWEI and for scam launches/IDO’s which add a token for too much $.

<b>Max overall slippage</b>
The max slippage you want the bot to handle. Can be set from 1 to 100%. 100%= the bot only will
accept a trade if the minimal amount of tokens it gets is 0 (=always accepting).
Slippage is the expected % difference between these quoted and executed prices. Low liquidity can
also cause increased slippage, which is why larger orders tend to face higher slippage.

<b>GWEI to use for trade</b>
The amount of GWEI you want to use for a trade. Remember to keep this 10-15 (when bsc is not the
usual 5 GWEI) for testing. But for sniping much higher. How much higher depends on the token (how
much people are going to snipe), your latency with the RPC and if you really want to compete with
the fastest guys, or just don’t want to make a proft. The fastest snipes use the highest GWEI and are
only worth it when you play with a lot of BNB.
https://bscscan.com/tx/0xc13c8150dc5eb37fde31cc9d155349af57a2b0973e35f0cd82942c6459b29
bd6


<b>Sell when price is higher than (Limit sell)</b>
Limit sell option. If the current price of the token is higher than the amount set here, the bot will
buy.

<b>Sell when token is this much higher than start (= Sell when you have this much profit ,if
you would sell)</b>
The amount of profit you want to have, and want to sell for. This is not the profit that you are going
to make, there is still slippage.

<b>Custom slippage for selling</b>
The slippage you want the bot to handle specially for selling. Can be set from 1 to 100%. 100%= the
bot only will accept a trade if the minimal amount of BNB it gets is 0 (=always accepting). If you don’t
check it, it will use the overall slippage.
Slippage is the expected % difference between these quoted and executed prices. Low liquidity can
also cause increased slippage, which is why larger orders tend to face higher slippage.

<b>Gas limit</b>
Please set this at 700000, so an order will never fail because you didn’t accept a higher gas.

<b>Sell this many times</b>
Perform a sell in multiple orders. In the future this will get more advanced, with different profits you
accept as sniper per number of order in a sequency.

<b>Only sell token, don’t buy</b>
Will ignore settings that have to do with buy, and will only sell token


<b>Token address</b>: Fill the token address of the token you want to trade (such as 0x0000000000000000000000000000000000000000)

<b>Token name</b>: The name of the token, fill it in yourself

<b>Dec.</b>: The amount of decimals the token operates with (18 is normal)

<b>Sell(£)</b>: The price you want the trader to sell the token for (0.01 = 1 dollar cent)

<b>Buy(£)</b>: The price you want the trader to buy the token for (0.01 = 1 dollar cent)

<b>Different deposit address</b>: Use this if you want the swap output to go to a different wallet address. There is a toggle for true/false and a field in config.py for the different address.

<br> </br>

<br> </br>
<H2>Current bugs</h2>

- Some tokens or trading amounts are not possible to trade with, due to this issue: https://github.com/ethereum/web3.py/issues/1634
  This is the error-message you get: "Python int too large to convert to C ssize_".
  If you get this error its best to exclude the token (which probably has a very low price per token) or trade with lower amounts.
- Sloppy dinamic design of GUI
- Sometimes lag when updating names or when starting the bot (0-10 seconds)
- More: Let me know!

<br> </br>
<H2>To do</H2>

- Let the amount of decimals and the token-name be derived automatically (like in the uniswap-bot)
- Add pcs v1 support
- New, more user-friendly design
- Fix "Python int too large to convert to C ssize_"

(Depends on whether the application is used)

<br> </br>
<H2>Author</H2>

If you have any questions you can contact me via telegram: meadsy92
<br> </br>
Donations: 0xEE2FB21ecf35bc3f061b780Ebb3bf0299337EFc0


<br> </br>
<H2>Disclosure</H2>
Use the application at your own risk, I am not in any way responsible for losses.

  

