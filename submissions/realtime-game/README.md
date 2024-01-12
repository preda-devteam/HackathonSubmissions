# Moba metaverse
The **blockchain platforms** are the world computers, where changes into the programs is possible only by pre-defined permissions. The world computers enable the games, where game designers won't change the rules for the profit, unless players don't approve it.

According to the legends, Vitalik Buterin was playing World of Warcraft. One day, Blizzard Studio decided to remove his favorite asset without any notice. Outraged Buterin decided to create the first blockchain platform, Ethereum. With the world computer, the owners of the game wouldn't be able to do whatever they want.

Another problem in the current game industry is the ownership over the game mods. Game studio owns all rights to the items, mods that were created by the players.

The nature of the *blockchain platforms* allows creation of the games, where users could add more items, mods and own them. With the original game studio they may share the royalty by pre-defined rules in the smartcontracts.

> From my understanding the metaverse is only possible if the game is extendable by the community. And any mod, item  is owned by it's creator.

In order to create such kind of the metaverse, it must be a popular game with millions of the players. The most popular games are online, session based games such as *Counter Strike, GTA V Online, League of Legends, Dota 2 and etc*.

Unfortunately, the current blockchain platforms don't allow to create this types of games. It's not even possible if the game has it's own blockchain network. 

![alt text](dota_stats.png "Dota had 500,000 users")
*https://steamcharts.com/app/570*

*For example, Dota 2 had 500,000 users playing at the same time. Trying to process 500,000 requests in one queue would make game infinetely slow, therefore impossible to play*.


The PREDA's parallel execution model allows to build such kind of the games. In the example above, assuming that every *Dota 2* session has 10 players, we could parallelyze each session. Instead a half million requests, the nodes would need to parse 9 requests at most, which dramatically improves the game speed.

I present a **Moba game: Sedentary versus Nomads** inspired by *Dota 2*. Using the **Preda to track each session in parallel**, this game theoretically could support as many users as the most played multiplayer games. 

**This is also a community driven metaverse**. The Moba games have heroes, items to craft. In this game, users are able to create their items, heroes and different game mechanics. They own the full right for them. And if they trade the heroes, items in the marketplaces, then they give the royalty fee to the original authors of the Moba.

If the player created battle arena is not for free, then by discussion with the original authors they should give the part of the fees. The discussion is not meant about the permission, but notification about the charging part.

For example, someone may be a battle arena for **Chinese versus Huns**, or **Chengiz Khan** packs and have the full rights for that.

---

# Game rules
The game is the battle arena for ten players. They are split into two teams of five players. In this game, one team represents the sedentaries, while the other side represents the nomads. 

![battle arena](Map_of_MOBA.png "Battle arena")
*Battle arena map from Wikipedia*

Each team has a base building located in the opposing sides. The bases are connected through the three roads. Both sedentary and nomads are spawning army in every minute. These army marching along the lanes clash to each other. The game is won, when the team that destroys the opponent's base.

Players pick the hero from the pool.
![hero pool](hero_pool.jpg "Hero pool")

In our game, we provide the first 100 heroes available for everyone. The game has the **Hero creation** page where users could mint new heroes. Either by creating their own heroes, or buying from the marketplace, users can import custom heroes as well.

The heroes have different ability, different mechanism but equal in the power.

![Creeps](creeps.jpg "Creeps")
The goal of the players is to help to their army to win against the opponents.

Heroes are getting more powerful, by level increase, or by purchasing items for farmed gold. Along the lanes the parts have the towers that must be destroyed before reaching the base. 

The killing army, destroying buildings or killing heroes give to the player an experience and gold. The experience is used for the level. The gold is used to craft items.

In our game, we provide 100 items to buy for everyone. The game has **Item alchemy** where users can mint new items. Either created, or obtained from the marketplce, the items maybe added into the game as well.


The moba is defined with the four parts:
* Gameplay (the core with the initial MOBA gameplay by sessions).
* Hero (NFT that users could create or choose to play the in the game).
* Item (NFT that boosts the hero power in the game)
* Token (a token to purchase the assets in the game. Any modifications, NFTs of this metaverse has to use this token for the payments. The token defines the royalty that goes to the original creators).

## Smartcontracts
As our game is community driven, every hero, item is represented as an NFT.
There could be thousands if not millions possible options of hero, item.
To track which one is better and which one is not, we track the games that were won with the heroes and items.

During the game, the NFTs can not be traded. Therefore for every session we lock them in. Upon session end, we unlock the NFTs and update the stats as well.

### Session
The main smartcontract `moba.prd` spwans the session for each game matches.

Each session has two phases. The preparation phase and the game phase.

The preparation phase goes five minutes. In the preparation phase, players are picking the heroes that they will play with.

The game phase goes until the base is not destroyed.
The game has a game master. At the end of the game session, the master will inform the smartcontract about the game status. It's the only part that must be trusted by both parties.

## Hero
Unlike other Moba games, in **Sedentary versus Nomads** anyone can create their own hero. We represent the heroes as NFTs.

The heroes have various stats, agilities such as *intelligence, speed, health point* and etc. We define the common value as the sum of all stats.
Let's say all heroes have 1 points.

Then, users may create a hero with `[0.2, 0.2, 0.6]` or `[0.2, 0.5, 0.3]`,
parameters. But in the sum the stats will be equal to the `1 points`. This is defined in the smartcontracts, therefore anyone can create the heroes.

For Hero specification check the [Hero.md](./Hero.md) page.

> Implemented in the [./code/hero.prd](./code/hero.prd)

## Item
Items increase the hero stats, or adds additional abilities.

![Item](gloves_of_haste.png "Gloves of Haste")
*https://dota2.fandom.com/wiki/Gloves_of_Haste*.

For example, the item above from Dota 2 increases the hero attack speed by *20*.

Unlike other Moba games, in **Sedentary versus Nomads** anyone can create their own item. We represent the items as NFTs.

In the smartcontract, we define the ratio between item cost to the boost that it gives.

For Item specification including the formula by which it's cost is calculate is defined in the [Item.md](./Item.md) page.

> Implemented in the [./code/item.prd](./code/item.prd)

### Hero ability
The hero's abilities are like items attached into the heroes. There are four abilities.

The three abilities are available in the beginning.
They each cost `500 gold`. The fourth ability is the ultimate one and 
available only after level 6. It costs `3000 gold`.

In the hero creation, users may include the hero's items as abilities. But the first three should cost `500 gold`, and ultimate ability must be equal to the item that costs `3000 gold`.

# Token
The `TOKEN` is the in game currency that is used in the following cases:

* When user imports the hero or item into the game.
* In the shop to sell or buy the hero or item.
* Royalty if there are other games that use items, heroes.

The shop is out of the game for now. The royalty is defined in the `TOKEN` smartcontract itself.

## Royalty
The royalty is defined in the percentage wise and it's always 20%.

If there is a smartcontract that receives the heroes or items, then they must accept the `TOKEN` as their payment system.

> It's subject of organization by the DAO.

# Marketplace
The marketplace is the part where users can exchange their heroes and items
with other people.