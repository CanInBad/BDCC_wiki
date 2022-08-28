Scenes are pretty much the main part of BDCC, they are the things that react to the player's input and then output text.

Here is how the simpliest scene looks in code:
```
extends SceneBase

func _init():
	sceneID = "TestScene"

func _run():
	if(state == ""):
		saynn("Hello world!")

		addButton("Okay", "End this scene", "endthescene")

func _react(_action: String, _args):
	if(_action == "endthescene"):
		endScene()
		return

	setState(_action)
```
Save it as `TestScene.gd` inside the `Scenes` folder, that way it will be registered automatically. Don't be afraid, if you don't understand code just skip to the part where I explain how to structure your raw texts. You can let somebody else code it for you or something.

So, each scene is an object that inherits the base class `SceneBase`. Each scene must have a unique `sceneID`, you can run a scene just by having its id. There are many functions that you can override but 2 of the main ones are `_run` and `_react`. It's VERY important to understand what each one does. `_run` is a function that outputs text and gives the player options, that's it. These are the only things that this function should do. `_react` is a function that 'reacts', it doesn't output text, it instead runs code depending on what choice the player made.

Double n at the end of `saynn` function means it will add 2 newlines, it's equivalent to using `say("Hello world!\n\n")`
First two arguments of `addButton` are the button name and description. Third argument is an 'action'. When the player presses this button `_react` function will be called with the '_action' argument being that action. Pressing the button in our case will call 'endScene()' ending the scene.

So, that's only one screen and one button. How do we add more? Take a look.

```
extends SceneBase

func _init():
	sceneID = "TestScene"

func _run():
	if(state == ""):
		saynn("Hello world! The world asks if you are evil.")

		addButton("Yes", "Tell the world that you came to burn it", "say_yes")
		addButton("No", "Tell the world that you are kind", "say_no")
		
	if(state == "say_yes"):
		saynn("[say=pc]I'm here to burn you![/say]")
		
		saynn("The world frowns at you.")

		addButton("Okay", "End this scene", "endthescene")

	if(state == "say_no"):
		saynn("[say=pc]I'm kind! I'm here to hug you.[/say]")
		
		saynn("The world smiles happily.")

		addButton("Okay", "End this scene", "endthescene")

func _react(_action: String, _args):
	if(_action == "endthescene"):
		endScene()
		return

	setState(_action)
```

Should be mostly self-explanatory. Since the `_react` function doesn't handle 'say_yes' and 'say_no' actions in any way they become the new 'state' (last line does that). The whole `[say=pc]bla bla[/say]` thing is how you make somebody talk, you can put a character id in there or use pc for player.


### Running the scene
So, we got our scene written. How can we play it in-game? Easiest way is through the debug panel. Open it, press the 'Run scene' button and type in `TestScene` as the sceneID argument. If you close the panel, you should see your scene.

![pic1](https://user-images.githubusercontent.com/14040378/187076143-b4be0ceb-d08f-46ef-9ff3-ed087feee531.png)
![pic2](https://user-images.githubusercontent.com/14040378/187076153-d2046ff1-7890-4cb1-b568-2a642e7ece0f.png)

If you want to add ability to run that scene without debug panel you will have to use events. Events provide a great way of extending the game without making it a mess. Events can 'subscribe' to certain 'triggers' like entering a room, talking to a npc, etc and then running some code. There will be a bigger tutorial about events so for now just try to understand what this event will do. Create a file called `TestSceneEvent.gd` inside `Events` folder and paste this:

```
extends EventBase

func _init():
	id = "TestSceneEvent"

func registerTriggers(es):
	es.addTrigger(self, Trigger.EnteringPlayerCell)

func run(_triggerID, _args):
	addButton("TestScene!", "Run the test scene", "testScene")

func getPriority():
	return 0

func onButton(_method, _args):
	if(_method == "testScene"):
		runScene("TestScene")
```

This event subscribes to `EnteringPlayerCell` trigger which will run each time we enter the player's cell. Inside `run` we add a new button that will run our test scene. If you launch the game and go to your cell, you will see a new button appear.

![pic](https://user-images.githubusercontent.com/14040378/187076809-279a5297-03d2-474b-85c8-68927bf4f71d.png)

Pressing it will run the `TestScene` that we created. Great. If you want more ways to use events you will have to look at other ones and use them as an example, explaining everything will take too long.

### Running code
Okay, we added our scene and can even trigger it without using the debug panel. How do we do something useful inside our scene? By using the `_react` function. Take a look

```
extends SceneBase

func _init():
	sceneID = "TestScene"

func _run():
	if(state == ""):
		saynn("Hello world! The world asks if you are evil.")

		addButton("Yes", "Tell the world that you came to burn it", "say_yes")
		addButton("No", "Tell the world that you are kind", "say_no")
		
	if(state == "say_yes"):
		saynn("[say=pc]I'm here to burn you![/say]")
		
		saynn("The world frowns at you.")

		addButton("Okay", "End this scene", "endthescene")

	if(state == "say_no"):
		saynn("[say=pc]I'm kind! I'm here to hug you.[/say]")
		
		saynn("The world smiles happily.")

		addButton("Okay", "End this scene", "endthescene")

func _react(_action: String, _args):
	if(_action == "say_yes"):
		GM.pc.addLust(100)
		addMessage("The world made you horny!")
		
	if(_action == "say_no"):
		GM.pc.addPain(-100)
		addMessage("The world healed your wounds!")
	
	if(_action == "endthescene"):
		endScene()
		return

	setState(_action)
```

Now if we press 'yes' the scene will add 100 lust to us and display a message. `addMessage` is a way of outputting text from the `_react` function, great for describing what happened. You do a lot of things, like ending the scene, running another scene using `runScene()`, changing flags, variables, anything. Best way to learn would be to look at the other scenes.

![pic](https://user-images.githubusercontent.com/14040378/187077031-0703f091-e636-4163-88fa-07320fe9634e.png)

### Adding state

So, sometimes you will need to add some state into your scene. The tricky thing here is supporting saving/loading. But the scenes make it very easy to save/load variables, let's add a simple counter.

```
extends SceneBase

var counter = 0

func _init():
	sceneID = "TestScene"

func _run():
	if(state == ""):
		saynn("Hello world! The world asks if you are evil.")

		saynn("The counter button was pressed "+str(counter)+" times")

		addButton("Yes", "Tell the world that you came to burn it", "say_yes")
		addButton("No", "Tell the world that you are kind", "say_no")
		addButton("Counter", "Increment the counter", "add_one")
		
	if(state == "say_yes"):
		saynn("[say=pc]I'm here to burn you![/say]")
		
		saynn("The world frowns at you.")

		addButton("Okay", "End this scene", "endthescene")

	if(state == "say_no"):
		saynn("[say=pc]I'm kind! I'm here to hug you.[/say]")
		
		saynn("The world smiles happily.")

		addButton("Okay", "End this scene", "endthescene")

func _react(_action: String, _args):
	if(_action == "add_one"):
		counter += 1
		setState("")
		return
	
	if(_action == "say_yes"):
		GM.pc.addLust(100)
		addMessage("The world made you horny!")
		
	if(_action == "say_no"):
		GM.pc.addPain(-100)
		addMessage("The world healed your wounds!")
	
	if(_action == "endthescene"):
		endScene()
		return

	setState(_action)

func saveData():
	var data = .saveData()
	
	data["counter"] = counter
	
	return data
	
func loadData(data):
	.loadData(data)
	
	counter = SAVE.loadVar(data, "counter", 0)
```

As you can see, you only need to define 2 extra functions, `saveData` and `loadData`. The last argument of the `loadVar` function is the default value in case that variable wasn't found in the save file.

Here is how the scene will look if you press the counter button a few times.

![pic](https://user-images.githubusercontent.com/14040378/187077345-ddcce1f0-65a1-4d8b-8427-0bdc01e24c41.png)

The scene gets destroyed when it is ended, meaning all its state gets lost. If you wanna save a variable over a long time you will have to use flags. Flags need to be defined inside the module before they can be set with `setModuleFlag` and `getModuleFlag` functions, just look at how other modules do it.

### Packing it up into a mod

Okay, we have our scene and an event that will launch that scene. How do we make that into a mod. First, you have to create a module. Create a new folder inside `Modules` and name it something like `TestSceneModule`, move both our scene and the event files inside it. Then create a `Module.gd` script and paste this:

```
extends Module

func _init():
	id = "TestSceneModule"
	author = "Rahi"
	
	scenes = [
		"res://Modules/TestSceneModule/TestScene.gd",
	]
	events = [
		"res://Modules/TestSceneModule/TestSceneEvent.gd",
	]
```

Now if you run the game you should see a new module appear and our scene and event should function the same. Now to make this into a mod you will have to run `ModMaker` inside the devtools menu and add our whole module into the list on the right like so:

![pic](https://user-images.githubusercontent.com/14040378/187077915-8feb8fa8-0664-4fe6-b9f5-938f13e6b363.png)

Then when you press the `Make mod` button the game will gather your files and present you with a folder. Select everything and use any file archiver like WinRar to make a .zip archive. Then put that archive inside the mods folder and open a standalone version of the game (mods don't work if running the game from the editor). You should see this.

![pic](https://user-images.githubusercontent.com/14040378/187078058-b158595b-0348-4f86-89ee-f3ca67865746.png)

And the scene should appear inside the game too. If you did this, congrats, you made a mod. Use this one to troubleshoot if something doesn't work: 
[TestSceneMod.zip](https://github.com/Alexofp/BDCC/files/9439807/TestSceneMod.zip)

### Best way to write scenes

I (Rahi) write my scenes in google docs first before turning them into code and I very much suggest you to do the same. Please, don't write text inside the code editor, use anything that can spot and correct errors, you will save the eyes of many people that won't see your typos.

So, you have your text editor of choice opened. How do you structure a scene so it can be easily turned into code. Here is a simple example scene

```
The world spins around.

You approach it.

> Say hi, Greet the world
[say=pc]Hello world![/say]

The world didn't seem to care, aww.
(scene ends here)
```

Okay, great. To turn this text into actual code run the game, open the devtools and select `SceneConverter`. Paste the raw text into the top textbox and press the `Convert` button. It should give you something like this:

```
	if(state == ""):
		saynn("The world spins around.")

		saynn("You approach it.")

		addButton("Say hi", "Greet the world", "say_hi")

	if(state == "say_hi"):
		saynn("[say=pc]Hello world![/say]")

		saynn("The world didn't seem to care, aww.")

		# (scene ends here)
```

![pic](https://user-images.githubusercontent.com/14040378/187075768-59b6bf04-83b8-4e9c-978b-38ae3dbae556.png)

Okay, it gave us something but it's not working code yet. To make it work paste it into the `_run` function like so

```
extends SceneBase

func _init():
	sceneID = "TestScene"

func _run():
	if(state == ""):
		saynn("The world spins around.")

		saynn("You approach it.")

		addButton("Say hi", "Greet the world", "say_hi")

	if(state == "say_hi"):
		saynn("[say=pc]Hello world![/say]")

		saynn("The world didn't seem to care, aww.")

		# (scene ends here)
		addButton("Okay", "End this scene", "endthescene")

func _react(_action: String, _args):
	if(_action == "endthescene"):
		endScene()
		return

	setState(_action)
```

I kept the last 'Okay' button too. So, now this looks a lot like our previous example. As you can see, anything that starts with a > will turn into a `addButton` call. Anything between ( and ) will turn into a comment. That's how you turn a raw text into a scene quickly.

Here is a full example of how I wrote one of the scenes using google docs: [https://docs.google.com/document/d/1vfhiaFHgUD6SJMLzg_XrpE87-4S21XX_6dJxQkrUNxY/edit?usp=sharing](https://docs.google.com/document/d/1vfhiaFHgUD6SJMLzg_XrpE87-4S21XX_6dJxQkrUNxY/edit?usp=sharing)

If you're a writer, just to stick to that style

Currently there is no way to define multiple-actions, the scenes produced by the sceneConverter will all be 'linear'. If you want to give the player a choice, you will have to write your scene in a flat style and then re-arrange the addButton calls yourself after converting. Sorry. Just look at how other scenes do things if you're unsure.