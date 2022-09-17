Just a heads up, the system of adding new bodyparts will probably be simplified quite a bit in the future. I have some ideas how to make it way easier but it would take quite some time. So for now this will have to do.

## Adding new bodypart
Probably the easiest bodypart type to start with is hair. So let's add some hair

The easiest and the best way of doing so is copying one of the existing hairs and just changing the texture. That’s the best way to add any new bodypart too unless you wanna mess with create a custom mesh in blender. But if you need to do so - look at the `DollSkeleton.blend` file inside the `AssetsSource/character` folder, it has all the current meshes and animations. But if you just wanna swap the texture, this tutorial is for you.

Open the game in the godot editor. Navigate to the `Player/Player3D/Parts/Hair` folder. Duplicate one of the folders and rename it to whatever you want. I will just dublicate `PonytailHair` and name it `RedPonytailHair`

![pic](https://user-images.githubusercontent.com/14040378/190865371-a64c5388-55dd-4f4b-a666-b133bbebeef4.png)

Expand it and change the scene name too. Png file can have whatever name.

Now you can draw the new hair, using the old one as the base if you want. I just tinted the texture red outside of godot.

![pic](https://user-images.githubusercontent.com/14040378/190865500-0ba2d2c7-3e7c-4479-93bb-3c8787b8980e.png)

Double click the .tscn file. If you switch to the 3d view you will see that the hair is still using the old texture. That’s because the mesh’s material is still from the old hair. When you duplicate the scene, the materials DON’T get duplicated, they are shared, keep that in mind.

So you gotta make the material ‘unique’ first. To do so click on the mesh, open the materials tab, right click the material and press ‘make unique’

![pic](https://user-images.githubusercontent.com/14040378/190865718-ab231cea-987c-4c16-8b8b-57cee41b32b2.png)

Now open the material by clicking on it. Then find the Albedo section and drag your texture onto the texture field. You should see your hair in 3d viewport now.

![pic](https://user-images.githubusercontent.com/14040378/190865931-7dce58c2-ba27-42c7-8aaa-1f27c6a8cbef.png)

That’s it on the model side. You still gotta ‘define’ it as hair for the game. To do so navigate to the `Player/Bodyparts/Hair` folder and duplicate one of the hair definition files.

Now double click on it. It would look something like this.

![pic](https://user-images.githubusercontent.com/14040378/190866015-aeba4627-50e7-4e4d-ba70-7186031fbcc5.png)

id must be unique, I will change it to `redponytailhair` . I will also change the visible name to ‘red ponytail’ and change the `getDoll3DScene()` return string to point to the scene file we created before. It should look like this.

```
extends BodypartHair

func _init():
	visibleName = "red ponytail"
	id = "redponytailhair"

func getDoll3DScene():
	return "res://Player/Player3D/Parts/Hair/RedPonytailHair/RedPonytailHair.tscn"

```

Now you should be able to just run the game and see that the new hair has appeared in the character creator.

![pic](https://user-images.githubusercontent.com/14040378/190866131-6d64f3bd-869e-41db-a5e3-751abbe8a455.png)

If it did - good. Now you can follow the steps from other tutorials to create a new module and then create a mod. Don’t forget to change the `getDoll3DScene()` function to point at the new location when moving files.

Here is an example mod that adds the red ponytail.
