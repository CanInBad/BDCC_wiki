Thanks to the way Godot's resource packs work mods can actually override pretty much any file. Here is how you do it

- Open the project inside the godot's editor
- Change any file, any script, any image, etc. Remember which ones.
- Use the mod maker to export the files that you changed. Use the other tutorials if you're not sure how
- zip up the files. Put it into the mods folder and test the mod in a standalone game. If it works, you're done ^^

This opens up huge opportunities, you can pretty much change the whole game if you wanted. This method doesn't come without its drawbacks though, any update might break your mod, forcing you to make changes again. And also, if two mods override the same file, only the last one's changes will stay, that's just how it works. So be careful ^^

> [!IMPORTANT]
> Some systems/scripts like bases for bodyparts and perks is loaded before mods and maybe unchangeable with this method.  
> Yes, it works in the editor but when you export it they might not change at all. It's a hit or miss.