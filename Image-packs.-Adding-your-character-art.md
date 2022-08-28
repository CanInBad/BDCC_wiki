! Download the game source files and godot itself before doing this, you will need the game opened inside the editor !

Image packs are the way of adding art to the characters. They work kinda like modules but allow the player to choose which artist they want to prioritize. Let's say you drew this fancy wolfo and wanna add him as a character art for the wolf that interogates you at the start of the game:

![wolfo](https://user-images.githubusercontent.com/14040378/187079102-c293831b-9156-4947-ae6a-917dac9e939d.png)

To do this create a new folder inside `Images/ImagePacks` and name it with your nickname. I will use `RahiTheSecond` since `Rahi` exists already. Put your artwork inside that folder, can sort it in any way, I do it by character. Also create a `ImagePack.gd` file with simillar contents:

```
extends ImagePack

func _init():
	id = "rahiTheSecond"
	artist = "RahiTheSecond"
	
	addCharacter("intro_detective", [], "res://Images/ImagePacks/RahiTheSecond/wolfo.png")
```

`id` must be unique, `artist` is who drew the art. Then you can add as much `addCharacter` calls as you want. You can even provide variations such as naked art, look at how I do it in my image pack.

After that, launch the game, you should see the image pack inside the settings

![pic](https://user-images.githubusercontent.com/14040378/187079457-b593e198-4b09-4d2c-868d-a373a6e95784.png)

If you start a new game you should see your art ^^

![pic](https://user-images.githubusercontent.com/14040378/187079626-10a9967e-bd6f-4158-8d65-5d5334773d23.png)

To make it into a mod, open the ModMaker inside the devtools. Add your whole image pack to the list of files.

![pic](https://user-images.githubusercontent.com/14040378/187079676-77793224-21b6-4320-a36d-5ffff230f27d.png)

Press `Make mod` and create a zip archive of what it gives to you. Move that archive to the mods folder and launch a standalone version of the game to see if it worked. The mod should show up in the loaded mods.

![pic](https://user-images.githubusercontent.com/14040378/187079805-ad65cff0-054d-43eb-a225-dbc0a45bc58b.png)

If it worked, you should see the art when you launch a new game ^^. If you did, congrats, you made an image pack. Here is an example by me: 
[RahiTheSecondImagePack.zip](https://github.com/Alexofp/BDCC/files/9439879/RahiTheSecondImagePack.zip)


