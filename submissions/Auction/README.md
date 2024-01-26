
# 🏷️ Auction DApp using **PREDA** <img src="https://preda-lang.org/img/logo.svg" alt="PREDA" width="24" height="24">

In this project I've created Auction DApp that is using Token contract for transactions, utilising both global and address scopes. I'm using custom Token contract to show how you can do token transfers similar to solidity ERC20 tokens.

# 📂 Directory Structure

* `Auction.prd` - Auction smart contract 
* `Auction.prdts` - Test script
* `Token.prd` - Token smart contract

# 📜 Contract Structure

## Auction.prd

### @address scope
* `@address bigint bid` - bid amount of address

### @global scope
* `@global address owner` - contract owner
    
* `@global bigint topBid` - highest current bid
* `@global bigint topBindingBid` - amount that will be withdrawn on auction end
* `@global bigint bidStep` - bid increment

* `@global bool canceled` - is auction canceled
* `@global bool ended` - is auction ended
* `@global address topBidAddress` - highest bidder address

* `@global function on_deploy(bigint _bidStep)` - Auction contract constructor
    - `bigint _bidStep` - max bid increment

*Explanation*: On contract creation, set owner to contract creator and initialize all variables

* `@address function placeBid(bigint amount) public export` - place bid method
    - `bigint amount` - amount of tokens to transfer

*Explanation*: Place bid in given amount of tokens or add this amount to bid if bid already exists. 
Only bids that are higher than topBindingBid are allowed.
Save bid variable to address scope

* `@address function bool withdraw() public export` - withdraw method

*Explanation*: Withdraw bid from auction. If sender is auction owner, withdraw `topBindingBid` and end auction.
If sender is the `topBidAddress`, only allow to withdraw anything above `topBindingBid`. In any other case, allow to withdraw entire bid.

* `@global function cancel` - cancel auction method

### Token.prd

### @address scope
* `@address bigint balance` - total balance of tokens for a given address

* `@address function bool transfer(address to, bigint amount) public export` - transfer amount to other address
    - `address to` - token recepient
    - `bigint amount` - amount of tokens to send


# 🧪 Testing

```
chain.deploy @0 Token.prd
state.set address.Token @all { balance:"10000000000000" }
```
Deploy token and set initial balance for all addresses

```
chain.deploy @0 Auction.prd={_bidStep:"10000"}
```
Deploy Auction contract and specify bidStep

```
Auction.placeBid @1 {amount:"100000"}
Auction.placeBid @2 {amount:"200000"}
```
Place bid for first address, then place bid for second address, outbiding previous

```
Auction.withdraw @0 {}
``` 
Owner withdraws and auction ends

```
Auction.withdraw @1 {}
Auction.withdraw @2 {}
```

Participants withdraw leftovers

----

Futher information:

[Language specification](https://github.com/preda-devteam/preda/blob/main/oxd_preda/spec/language_spec.md)

[Official documentation](https://docs.dioxide.network/doc/PREDA%20Language%20Specification)

[PREDA Whitepaper](https://preda-lang.org/pdf/preda-model-sole.pdf)