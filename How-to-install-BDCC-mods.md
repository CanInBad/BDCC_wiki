# Where <sup><sub>(and how)</sub></sup> to get mods

> [!IMPORTANT]
> Mods are simple zip archives. **Don't unpack them.**
>
> Keep in mind that some mods **NEED** to be updated for each new version of a game. If the game crashes on start, remove mods.

There are two ways.

You can either get them inside the game's discord.  
[BDCC Discord Invite](https://discord.gg/7UGYBvQrc3)  
Though, you have to manually install it. How you install it will be covered in [this section.](#manually-installing-a-mod)

Or you can get them inside the mod browser, instructions are below.

## Mod Browser

### Enabling BDCC Mod Launcher

If you already installed mods, [skip this section.](#inside-the-mod-launcher)

To enable BDCC Mod Launcher, you must at least reached title screen.  
1. Click Options.
2. Find and click the box next to "Enable Modded BDCC Launcher", Make sure that it's checked.
3. Save and close.
4. Quit Game.

Once you restart the game and you done everything correctly, a new screen will show up before loading.

### Inside the mod launcher

#### Downloading mods

Click the "Mod Browser" button
<div align="center">

<img src="images/installMods/installModsModsBrowser.png" alt="A image showing WHERE to click in the launcher" /> 
</div>
<br />

Inside the mod browser, on the left should be a list of mods. It is recommended to click "Newest first" to sort mods by date that its updated. Click for selecting one of the mods will show its information on the right as well as a big "Download mod" button.  

> [!NOTE]
> 1. The mod browser is sorted by newest first by default.   
> 2. You can scroll down in the mod's information if the description is long enough.
> 3. Don't forget to read the description.  
> 4. Download button is always on top of the metadata/information  

> [!WARNING]
> Some mods will show you what game version its compatible with.  
> It is not recommended to download and run mods that isn't compatible.
> On that note, few mods' description will tell you if it should be fine to run or not.

<div align="center">

<img src="images/installMods/modBrowserAnatomy.png" alt="A image showcasing anatomy of the mod browser" /> 
</div>
<br />

Once you click "Download" Mod, a dark transparent screen with text "Downloading..." will appear then quickly disappear <i><sup><sub>(or not depends on your internet connection speed)</sub></sup></i>  
If you wish to continue download more mods, select another and download them. Repeat this until you're satisfied

> [!CAUTION]
> Make sure to read the mod's description, some mods will conflict with each other. 

Once you finished downloading mod(s) you can then click "Close" on the top left of the screen

#### Managing installed mods

The mod launcher's interface should resemble the mods browser and this section will not explain how it works here. If you do not know how to use the mod browser, please [see previous section](#downloading-mods)

Once selected a mod, you should see that the information side is slightly changed.  
It now has 3 sections, The metadata / general information w/ description, buttons to manage the mod, and files that came with the mod in order from top to bottom.

<div align="center">

<img src="images/installMods/modSelectedInfoAnatomy.png" alt="A image showcasing anatomy of the mod browser" width="80%" /> 
</div>
<br />

This section will skip the general information.

> [!NOTE]
> If the Game Version shows red, that means the mod **may not** be compatible with this this game version you're running. It doesn't prevent the mod from working.

> [!IMPORTANT]
> If the mod doesn't have metadata packed with them, it will display
> `No 'insertModFileNameHere.json' file provided inside the mod`.  
> This **DOESN'T HAVE ANY IMPACT ON ITS FUNCTIONALITY**.  
> If you're having trouble(s) playing the game with mod(s), please consult this page (not done)
<!-- Don't forget to link it here when finished troubleshooting page -->

There are 4 buttons to manage mods, they're pretty self explanatory but we'll cover what order of mods affect them.

You can get the gist on how large a mod is inside the last section.

### Updating mods

To update mods, simply delete the current old version from your device and redownload it from the mod browser.

Sometimes there will be a changelog exclusive to the mod browser.

## Manually installing a mod

Once you obtained packed mod(s) either from [Alexofp/BDCCMods](https://github.com/alexofp/bdccmods) or the game's discord, here are many ways to install them manually

### Windows

#### Open folder

##### AppData way

1. Open a run windows box (Win+R).
2. Type in `%appdata%/Godot/app_userdata/BDCC/mods` then enter,  
   this will open a new explorer/file browser window.
3. Move the packed mod(s) inside the newly opened explorer window.

Restart the game and the mod(s) should appear.

##### Inside mod launcher

0. Open the game with [mod launcher enabled](#enabling-bdcc-mod-launcher)
1. Click the Mods Folder button,
   this will open a new explorer/file browser window
2. Move the packed mod(s) inside the newly opened explorer window.

Restart the game and the mod(s) should appear.

##### Inside the game.

1. Open the game. If you already have [mod launcher enabled](#enabling-bdcc-mod-launcher), either hit Launch BDCC with mods (Slower if you have mods) or Play without mods (This will load faster).
2. Once you reach title screen, click Mods
3. Click Open mods folder and move the packed mod(s) inside the newly opened explorer window

Restart the game and the mod(s) should appear.


#### Import in Mods menu at title screen

1. Open the game. If you already have [mod launcher enabled](#enabling-bdcc-mod-launcher), either hit Launch BDCC with mods (Slower if you have mods) or Play without mods (This will load faster).
2. Once you reach title screen, click Mods
3. Click Import mod. This will show a dialog inside the game. You can then navgiate to where you downloaded packed mod files, select, and click open.

Restart the game and the mod(s) should appear.

### Linux

#### mv

1. Open your terminal, make sure that you're on user that you're playing on
2. `mv <path to packed mod file> ~/.local/share/godot/app_userdata/BDCC/mods`

Restart the game and the mod(s) should appear.

#### Inside mod launcher

0. Open the game with [mod launcher enabled](#enabling-bdcc-mod-launcher)
1. Click the Mods Folder button,
   this will open a new file browser window
2. Move the packed mod(s) inside the newly opened file browser window.

Restart the game and the mod(s) should appear.

#### Import in Mods menu at title screen

1. Open the game. If you already have [mod launcher enabled](#enabling-bdcc-mod-launcher), either hit Launch BDCC with mods (Slower if you have mods) or Play without mods (This will load faster).
2. Once you reach title screen, click Mods
3. Click Import mod. This will show a dialog inside the game. You can then navgiate to where you downloaded packed mod files, select, and click open.

Restart the game and the mod(s) should appear.

### MacOS

#### mv

1. Open your terminal, make sure that you're on user that you're playing on
2. `mv <path to packed mod file> ~/Library/Application Support/Godot/app_userdata/BDCC/mods`

Restart the game and the mod(s) should appear.

#### Inside mod launcher

0. Open the game with [mod launcher enabled](#enabling-bdcc-mod-launcher)
1. Click the Mods Folder button,
   this will open a new file browser window
2. Move the packed mod(s) inside the newly opened file browser window.

Restart the game and the mod(s) should appear.

#### Import in Mods menu at title screen

1. Open the game. If you already have [mod launcher enabled](#enabling-bdcc-mod-launcher), either hit Launch BDCC with mods (Slower if you have mods) or Play without mods (This will load faster).
2. Once you reach title screen, click Mods
3. Click Import mod. This will show a dialog inside the game. You can then navgiate to where you downloaded packed mod files, select, and click open.

Restart the game and the mod(s) should appear.

### Mobile (Android)

<sup>*please just use the mod browser :sob: :pray:*</sup>

> [!IMPORTANT]
> Requires [BDCC.pck](#android-bdccpck) for mods to work

#### Manually moving them

Default mods folder location for android is inside your Documents folder.
Look for folder named `BDCCMods`, if there is no such folder, make a new folder with exact letter cases.

Move the packed mod(s) to `/Documents/BDCCMods`

Restart the game and the mod(s) should appear.

#### Import in Mods menu at title screen

> [!CAUTION]
> If you're running Android 13+, please give the game permission to access your files. Please see this [page for extensive guide](https://gist.github.com/CanInBad/cd1fb519a4fc604a83115b553a4a7402#file-3permshenanigans-md).

1. Open the game. If you already have [mod launcher enabled](#enabling-bdcc-mod-launcher), either hit Launch BDCC with mods (Slower if you have mods) or Play without mods (This will load faster).
2. Once you reach title screen, click Mods
3. Click Import mod. This will show a dialog inside the game. You can then navgiate to where you downloaded packed mod files, select, and click open.

Restart the game and the mod(s) should appear.

## Android BDCC.pck

Exclusive to android, you can build BDCC.pck inside the mod launcher. If you do not know how to open the mod launcher, [please see this section.](#enabling-bdcc-mod-launcher)

<br />
<br />
<br />
<br />

# Old Information

### Where to get mods
For now the only source of mods is the game's discord

[BDCC discord link](https://discord.gg/7UGYBvQrc3)

Mods are simple zip archives. Don't unpack them

Keep in mind that some mods NEED to be updated for each new version of a game. If the game crashes on start, remove mods

### Windows/linux/mac
1) Open the game
2) Press 'Mods'
3) Press 'Open mods folder' or go to `%appdata%/Godot/app_userdata/BDCC/mods` folder
4) Copy the zip files into that folder
5) Restart the game, mods should appear

### Android
1) Open the game
2) Press 'Mods'
3) If the game asks for external storage permissions, you gotta accept
4) Press 'Import mod' button. Game should tell you where to store mods on your device. It's usually the `documents/BDCCMods` folder
5) Copy `BDCC.pck` file into that folder. Warning. You will need to update this file with the new ones after each game update or stuff will crash
6) Copy the zip files into that folder
7) Restart the game. There should be a BDCC.pck file loaded as mod and you should also see other mods

If you don't do Step 5 the game will crash! Limitation of godot engine. `BDCC.pck` file can be downloaded separately from itch/github releases

### HTML5
1) Open the game
2) Press 'Mods'
3) Press 'Import mod'. Select the zip file
4) Reload the page. Mod should show up

Be very careful with mods and HTML5 version. If the mod crashes the game, your only option is to clear your localstorage. That will also delete your saves!