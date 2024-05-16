Module is a simple way to group related files together. Best example of that would be the portal panties module, it contains everything related to portal panties, the item itself, the quest and all the scenes/events in a single folder. That makes it way easier to manage the project without you having to jump between all the different folders while working on something specific.

![pic](https://user-images.githubusercontent.com/14040378/191040547-52681cbe-7995-46d2-a343-df73ee56a0e7.png)


Does that mean you can just remove a module and everything is gonna work like it was never there? Not really, most of the current modules depend on each other and it’s okay. Again, a module is just a folder to group things together.

```gdscript
extends Module

func _init():
	id = "SomeModule"
	author = "Rahi"
	
	items = [
		"res://Modules/SomeModule/TestItem.gd",
	]
	scenes = [
		"res://Modules/SomeModule/TestScene.gd",
	]
	events = [
		"res://Modules/SomeModule/TestSceneEvent.gd",
	]
```

The point of a module is to add new things into the game. New scenes, events, characters, species, etc. That’s how you extend the game without changing the current files.

Mods and modules are different things. Mod is a .zip archive that contains files. Mods can have modules in them. A single mod file can add several modules or none at all.

Modules can have flags. Flags are basically variables but they are saved/loaded for you automatically and can also be edited through a handy in-game flags editor. Very handy for debugging.

```gdscript
extends Module

func getFlags():
	return {
		"PlayerDidSomething": flag(FlagType.Bool),
		"SomethingElseHappened": flag(FlagType.Bool),
		"ThisIsANumberFlag": flag(FlagType.Number),
	}

func _init():
	id = "SomeModule"
	author = "Rahi"
	
	items = [
		"res://Modules/SomeModule/TestItem.gd",
	]
	scenes = [
		"res://Modules/SomeModule/TestScene.gd",
	]
	events = [
		"res://Modules/SomeModule/TestSceneEvent.gd",
	]
```

![pic](https://user-images.githubusercontent.com/14040378/191041191-b38ef2cf-0a32-4d4a-9d7c-1f6a6a707957.png)

To use the flags you can use the `setFlag`, `increaseFlag` and `getFlag` functions.

`setFlag("ModuleID.FlagID", newvalue)`

`increaseFlag("ModuleID.FlagID")`

`getFlag("ModuleID.FlagID", defaultValue)`
