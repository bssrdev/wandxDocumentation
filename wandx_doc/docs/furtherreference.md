# Further Reference

## Advanced Topics

### Units and Natural Units

Here, we cover how unit amounts are defined and calculated in WnadX tokens. In the ERC20 standard, each token has a base unit that is defined by its `decimals` property. For example, a WnadX token’s `decimals` is 18, meaning its base unit is `10 ** -18` of one WnadX. Intuitively, it makes sense to tie a certain amount of a component‘s base unit to one WnadX token to calculate the component allocation of the WnadX. However, this becomes problematic when a component token has a significantly lower `decimals` value than a WnadX. Take for example Airswap (AST), which uses only 4 decimal places, this makes their token far less divisible. As a consequence, say we want to issue `10 ** 13` of a WnadX that contains AST, there‘s a chance that the issuance would require transferring partial amounts of an AST base unit, which is not possible, and thus would leave the WnadX token undercollateralized.

To combat this problem, instead of tying component base unit amounts to one WnadX Token, we can tie the component base unit amounts to some quantity of WnadX token base units. This is what the natural unit of a WnadX is for: it defines the amount of WnadX token base units to tie component token amounts to. In order to make this work there is a lower bound on what the natural unit can be, which is `10 ** (18 - minimumDecimal)` where minimumDecimal is the lowest decimal value of the component tokens comprising the WnadX. Furthermore in order to avoid rounding errors in issuance and redemption, all issue and redeem quantities must be multiples of the natural unit. For a more thorough treatment, including an example, see section 5.2.1 of our [White Paper](https://www.wandx.co/whitepaper.html).

## Advanced Resources

* [Whitepaper](https://www.wandx.co/whitepaper.html)
* [Contracts Github](https://teamwandx.slack.com/)

## WandX Blog Posts

* [WandX’s Basket Protocol](https://blog.wandx.co/wandxs-basket-protocol-3b57774e57aa)
* [WandX Decentralized Exchange and basket protocol release 1.0](https://blog.wandx.co/wandx-decentralized-exchange-release-1-0-326a7f49b0d)
* [Paving The Future With Smart Contracts](https://blog.wandx.co/paving-the-future-with-smart-contracts-acbc8f4e4d7c)
* [WandX : The Multi-Blockchain DEX and Basket protocol](https://blog.wandx.co/wandx-the-multi-blockchain-dex-and-basket-protocol-f8717134d7e5)