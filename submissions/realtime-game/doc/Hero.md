## Hero
> Implemented in the [./code/hero.prd](./code/hero.prd)

The heroes have Health Points (HP), and Mana Points (MP).
Along with the indicators the heroes have the level that could upgrade up to 31 level.

The heroes have following parameters: 
* Attack, 
* Attack Speed, 
* Speed, 
* Attack Range,
* HP recovery,
* MP recovery,
* Defense,
* Magical defense,

The heroes have following stats:
* Intelligence,
* Agility,
* Strength,

The heroes have four abilities. The way how the ability behaves is defined by the script. They could be active or passive. The active abilities consumes mana.

Finally, the heroes have a meta which includes the 3d models, name, description and author of the model.

### Property Relationship
The stats (intelligence, agility, strength) influences the other properties of the heroes.

* Agility influences attack and speed parameters.
* Strength influences health point and defense and health regenaration.
* Intelligence influences mana point, mana defense and mana regeneration.

* Class: [Intelligence, Agility, Strength]

The class is the element of three numbers indicating how much the stats are increased by level upgrade.

Each stat have a ratio array that is defined as a constant.
The ratio explains how the stat is split into the parameters.

### Hero creation
As we said every user can create their own heroes. 

As we know, each hero has a level that increases by the experience.
At most 25 levels.
The level increase triggers the class which upgrades the stats.
Stat upgrade triggers the stat ratio which upgrades the hero parameters.
Improved parameters makes the hero more powerful.

The level gives the point that is defined by the game.

Initially it has 100 points. And each level adds 20 points into that.

That 100 points are split by the class.
For example class ratio is `[0.1, 0.3, 0.6]`. Which means
In the beginning the hero will have `10 intelligence`, `30 agility` and `60 strength`.

The level two will give: `12 intelligence`, `36 agility` and `72 strength`.

Then, those `10 intelligence` is split by the `intelligence ratio`:

`[0.8, 0.15, 0.05]` &ndash; mana points, mana recovery, mana defense.

Which means, in the beginning the hero has `8 mana points`, `0.15 mana recovered`, and `0.05% percent of all attacks are defended`.

In the level 2, with `12 intelligence` the hero will have
`9.6 mana points`, `0.18 mana recovered per second`, and `0.06% percent of all attacks are defended`.

## Item
Items are scriptable filters applied to the heroes.
Script defines the match making triggers when the filter is applied.
The triggers are hero actions such as stop, alive, attack, death or respawn.
Other type of triggers are based on the parameter change, or game stat change.
If the trigger is depends on alive status of the hero, then it will passive item.
Otherwise, it can be active trigger. In this case it is clickable.

The triggers applies the filter.
Filters are two types: to a hero, to a region.
If it's to the hero, then it maybe based on selected hero, or heroes in the region.

Lastly, it has the cost.

For example, there is an item that adds 20 HP.
The trigger is the hero's alive status, in match making it's:

`when (this.hp > 1) { this.params.hp += 20 }`.

Here, the trigger and the parameter value are defining the cost:

The alive trigger costs `200 gold`, the HP costs `20 gold`.
This item costs `220 gold`.

Items may have multiple triggers.

`this.on (params.hp > 1) { this.params.hp_reg += 0.1 }`

`click(this) { this.params.hp += 200 }`

Here, the second trigger is depends on the click. The cost of the click is
`20 Gold`, the `this` argument costs `20 gold`.

In total the item with two triggers above would cost `440.1 gold`.

The items have a boost in terms of the time. The time amplifies,
the filter with less gold. But time also comes with the reset:

`time.click (this, amplify = 100) { this.params.hp += amplify * 10 }`

The time based triggers always start with the `time` prefix.
The above example shows that it amplifies by 100. Which means,
it costs twice less gold but, active in every twice.
In short, the item above costs: `550 gold` but active active in every `200 seconds`.

## Script
Scripts are composed of multiple items.
Scripts adds the capability of the items that it used.

For example, if there is a script that depends on item that increases 20 HP,
Then the script will have ability to change the 20 HP.

Besides that, at the starting point, the scripts add a cost which could amplify the parameter.
The cost amplifies in the percentage wise where each percent costs `20 gold`.

If the script costs `200 gold`, it means it gives additional `10` to the item. With the item above, users will have `22 HP` to use.

Plus of the scripts is that, amplification goes to anything or users may change the type of the trigger of the underlying item.

## Ability
The hero's abilities are like items. There are four abilities.
The three abilities are available in the beginning.
They each cost `500 gold`. The fourth ability is the ultimate one and 
available only after level 6. It costs `3000 gold`.

In the hero creation, users may include the hero's items as abilities.
Note that, each level gives to the user an amplification.

Each level gives `300 gold` that amplifies the ability.

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