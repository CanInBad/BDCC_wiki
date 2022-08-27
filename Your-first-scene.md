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
Don't be afraid, if you don't understand code just skip to the part where I explain how to structure your raw texts. You can let somebody else code it for you or something.

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


### How to write

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

I kept the last 'Okay' button too. So, now this looks a lot like our previous example. As you can see, anything that starts with a > will turn into a `addButton` call. Anything between ( and ) will turn into a comment.