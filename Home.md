Welcome to the BDCC modding wiki! Here you can learn how to make mods ^^

## How to start modding

BDCC is running on Godot 3.x engine, usually the latest stable version. At the writing of this tutorial Godot 4.x is in beta but moving to it would require major rewrites as the scripting language gdscript was changed quite a bit. So, what do you need to start modding.

- Latest Godot 3 build. Get it here: https://godotengine.org/download Standard 64 bit version will do, mono is not used. Download godot 3! not 4!
- Game source files. Use git if you know how or just download the zip archive from https://github.com/Alexofp/BDCC Click the green button and press Download as zip. Git is still preferred though in case you will want to make a pull request. Easiest git client is GitHub Desktop

That should be it. Launch Godot, press import and point it to the `project.godot` file inside the game source files folder. Editor should open with BDCC project loaded. From there you can start exploring or just run the game by pressing the play button in the top right corner. Best way to learn how to do something is to check one of the existing scenes.

## What things can be done through mods in BDCC

### Easy stuff:
- [Making Skins](Making-skins.md)
- [Your first mod. New item](Your-first-mod.-New-item.md)
- [What are modules](What-are-modules)
- [Writing scenes for the Scene Converter!](Writing-scenes-for-the-Scene-Converter.md)
- [Your first scene](Your-first-scene.md)
- [Image packs. Adding your character art](Image-packs.-Adding-your-character-art.md)
- Characters
- [Changing the core files of the game](Changing-the-core-files-of-the-game.md)

### Complicated stuff:
- [Bodyparts/hair, Species](Bodyparts,-Species.md)
- Events that can trigger new scenes
- Npc attacks
- Perks
- Status effects
- Arena fighters
- New map areas
- [New floors](New-floors.md)

Eventually each topic will have a dedicated tutorial



## How mods work in BDCC
Mods utilize godot's ability to load 'resource packs'. If you wanna read more about it, check this page: https://docs.godotengine.org/en/stable/tutorials/export/exporting_pcks.html

Unfortunately, due to how Godot currently works, it is impossible to load these resource packs while the game is running from the editor. That means that you can't load mods too. But you can still develop mods as part of the game and then isolating the files that you created into a mod. After that you can test your mod on a compiled version of the game. Tutorials will explain it ^^