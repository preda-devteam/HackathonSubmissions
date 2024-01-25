Hey there,
We’ve got this on-chain orderbook dapp. Basically, it takes in buy and sell orders from users and does on-chain matching. There’re three main contracts:
* OrderBook.prd: This is like the base of the order book, defining various attributes of the order book and functions for adding, modifying, and removing orders.

* MatchEngine.prd: This is the match engine. It implements order matching and invokes functions of the OrderBook contract to operate orders.

* OrderService.prd: This one is the interface. It can create new trading orders with a transaction or a contract call.

In these on-chain orderbook contracts, contracts will route orders for a specified trading pair to the corresponding on-chain address shard for execution, enabling parallel execution of orders across different shards, making things faster.

Additionally, I’v created **OrderService.prdts** for testing.
