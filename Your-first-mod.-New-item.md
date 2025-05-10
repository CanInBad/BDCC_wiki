So, easiest way to add an item is to create a new file inside Inventory/Items folder. The game reads that folder and registers each file automatically. So, create a file in that folder named TestItem.gd and paste this code

```gdscript
extends ItemBase

func _init():
	id = "TestItem"

func getVisibleName():
	return "Test item"
	
func getDescription():
	return "This is my first item in BDCC"
```

So this is simplest item one can make. id must be unique.
How can we get this item in-game? Well, at the moment, you can't. The only way is by using the debug panel. Enable it in the game's settings, that will add a DG button inside the game ui. Press it and select the "Give player item" option. That will open a menu with a list of all the items. TestItem should show up in there.

![pic](https://user-images.githubusercontent.com/14040378/186443254-88595e6b-504a-4177-8529-d3c163a1710b.png)

Okay. You got the item. You can look at its name and description but you can't interact with it in any way. How do we fix that? Easy. Take a look at this code.

```gdscript
extends ItemBase

func _init():
	id = "TestItem"

func getVisibleName():
	return "Test item"
	
func getDescription():
	return "This is my first item in BDCC"

func canUseInCombat():
	return true

func useInCombat(_attacker, _receiver):
	_attacker.addPain(-100)
	destroyMe()
	return "{attacker.name} used a test item!"
```

The item can now be used in combat. `_attacker` variable is player and `_receiver` is the enemy. `_attacker.addPain(-100)` means 100 pain will be removed from the player, essentially healing him. `destroyMe()` means the item will be consumed on use. And the last line shows what text will be outputted. So this is essentially a single-use healing item. If you wanna turn it into an offensive item you can change `_attacker.addPain(-100)` line to `_receiver.addPain(100)` That will make the enemy take 100 pain when you use this item, like a grenade or something.

Okay, great, we can use it in combat. But we can also make it usable outside of it with minimal changes.

```gdscript
extends ItemBase

func _init():
	id = "TestItem"

func getVisibleName():
	return "Test item"
	
func getDescription():
	return "This is my first item in BDCC"

func canUseInCombat():
	return true

func useInCombat(_attacker, _receiver):
	_attacker.addPain(-100)
	destroyMe()
	return "{attacker.name} used a test item!"

func getPossibleActions():
	return [
		{
			"name": "Eat it!",
			"scene": "UseItemLikeInCombatScene",
			"description": "Eat the thing",
		},
	]
```

We added a new function `getPossibleActions()`. As you can see, it returns a list of actions that we can do with this item outside of combat (there can be more than one). Each action is described by its name, description and what scene it will run. Scenes in BDCC are described in another tutorial. In this case `"UseItemLikeInCombatScene"` will just call `useInCombat()` inside of it. Since there is no enemy when we're using the item alone, the `_receiver` variable will be `null` Calling any function on a null variable will result in a crash so be careful ^^

Sooo, we can use the item in so many ways now but how can we get this item legitimately? There are a few ways.
- Adding it through code inside scenes
- Adding ability to buy it from vendomats
- Adding it as loot

First two are pretty use. To add an item using code use this
`GM.pc.getInventory().addItem(GlobalRegistry.createItem("TestItem"))`

To add ability to buy the item take a look at this code:

```gdscript
extends ItemBase

func _init():
	id = "TestItem"

func getVisibleName():
	return "Test item"
	
func getDescription():
	return "This is my first item in BDCC"

func canUseInCombat():
	return true

func useInCombat(_attacker, _receiver):
	_attacker.addPain(-100)
	destroyMe()
	return "{attacker.name} used a test item!"

func getPossibleActions():
	return [
		{
			"name": "Eat it!",
			"scene": "UseItemLikeInCombatScene",
			"description": "Eat the thing",
		},
	]

func getPrice():
	return 1
	
func getTags():
	return [
		ItemTag.SoldByGeneralVendomat,
		]
```

We added the item's price and this `getTags()` function. Item tags are just little hints that the game can use to use your item. `ItemTag.SoldByGeneralVendomat` item tag will add ability to buy this item inside the general vendomat. There are a few tags currently defined. Most interesting are

- `ItemTag.Illegal` Item is illegal and will be taken away during any searches
- `ItemTag.SoldByGeneralVendomat` Item is sold in the general vendomat
- `ItemTag.SoldByMedicalVendomat` Item is sold in the medical vendomat
- `ItemTag.SoldByUnderwearVendomat` Item is sold in the underwear vendomat

This is only the basic information about making a new item. If you wanna make something complicated such as a new BDSM restraint or new clothing you will have to look at other items and use them as examples

## Turning your item into a mod
Okay, great, you have an item. Now how do we make a mod that adds this item so other people don't have to use godot editor to use it?

Firstly, you have to create a module. What's a module? It's basically just a folder where you can group all your new stuff together all neatly.

Create a new folder inside `Modules` Name it `TestItemMod` or something. Move your `TestItem.gd` file inside it and also create a new file named `Module.gd` with this:

```gdscript
extends Module

func _init():
	id = "TestItemMod"
	author = "Rahi"
	
	items = [
		"res://Modules/TestItemMod/TestItem.gd",
	]
```

Change the author variable to your nickname ^^.

As you can see, the files aren't loaded automatically anymore, you have to define them so the game knows how to load them. But if you run the game, everything should stay the same.

Great. Now we can actually package our mod. Open the game, go into devtools menu and click on a 'ModMaker'. Find the module folder that you created and add it. That should add both files into the right list, that will be the contents of your mod.

![pic2](https://user-images.githubusercontent.com/14040378/186454139-2bfeca4f-5a05-4f02-b5b6-e2f9a537c886.png)

Now press the 'Make mod' button. That will gather all the files that you added and present you with the folder. To completele the mod, you gotta select everything and make a .zip archive yourself, godot can't do that on its own. Can't you gather the files yourself? Yeah, but this tool preserves the folder structure which is important and also does extra things if your mod contains new textures/images. So its important to do it this way, just trust me.

Now that you have the mod, you can put it into the mods folder and try it in-game. To use/test mods you gotta have a separate complied version of your game since the mods don't work inside the editor (godot quirk). When you launch the game you should see a new module appear inside the mods menu together with your zip file loaded.

![pic3](https://user-images.githubusercontent.com/14040378/186455813-5738cf09-df7d-48b3-a662-d3b6fa1d8c81.png)

Here is the resulting mod from me. Use as example or to troubleshoot if you want

[TestItemMod.zip](https://github.com/Alexofp/BDCC/files/9417316/TestItemMod.zip)

## Do you have to make a module?

Not really, module is basically just a way of grouping all the files related to your mod into one folder. Very handy for organizing. But it's possible to create a mod without it having any modules in it.

## Adding metadata to your mod

Making metadata should provide your users information about the mod inside the launch screen/mod launcher.

You can simply create new `.json` file named after your mod, like for example I want to create metadata for `TestItemMod.zip`, I have to create `TestItemMod.json` and put it inside the zip file.

Inisde the `.json` required 4 names and its datatypes:
1. `author` **|** `string`
2. `gameversion` **|** `string`
3. `modversion` **|** `string`
4. `description` **|** `string`

> [!NOTE]
> `gameversion` can take single OR multiple version OR all version by providing one of these syntax:
>
> For singular just provide the version like for example `"gameversion": "0.1.8"`  
> For multiple version, provide versions separated by command for example `"gameversion": "0.1.3,0.1.4,0.1.5,0.1.6"`  
> For all version you can just provide a star (\*) in the gameversion string for example `"gameversion": "*"`
>
> Version suffix doesn't matter, the version comparison doesn't care the suffix eg `fix1`

And you can provide additional information for people who maintain mod browser by adding the name `name` with data type `string`

In summary, inside your json should look like this

```json
{
    "name": "Test Item Mod",
    "description": "\nAdds something, probably",
    "author": "Wiki: CanInBad, Game: Alexofp",
    "modversion": "Test1",
    "gameversion": "0.1.1,0.1.2,0.1.3"
}
```