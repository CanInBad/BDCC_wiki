This page will list out problems then solutions, like QnA.

# General

### I have general gameplay questions

Simply ask them in the game's discord. If you're lucky, they might answer to you in a short period.  
[Discord Invite Link](https://discord.gg/7UGYBvQrc3)

### Where can I enable the debug menu

Inside main menu, click options. Find the Debug section. Click on the square until it is checked, then Save & close.

> [!NOTE]
> It is **NOT recommended** to turn on debugging menu on your first run, if you need genuine help with gameplay, please follow the last question.

### My game CRASHES/force close when loading into main menu

This might be Android only issue since it's necessary to tap on the screen for preventing the phone to go to sleep. And since you're tapping on the screen while it is technically not responding, Android will ask user to stop the game.

Although, you can try to mitigate the problem by doing these steps:  
1. Clear your RAM
   * Your phone might come with performance booster so use that to clear your RAM.
2. Clear your cache
   * Clearing your cache might help make the game load "smoothly" (not tested but some say it helps).
3. Upgrade your phone
   * If you already tried all of those options then it about time to upgrade your smart phone.

**If you're using mods, please see [this section.](#my-game-crashesforce-close-when-loading-into-main-menu-while-the-game-had-mods)**

if this happens on other devices than android then please report it a bug with the following information:
 - Your OS
 - Your device specification (must include CPU, GPU, driver versions)
 - What you think what is the version you're playing on.

### I can't export or import saves using the in-game exporter/importer

This is an issue exclusive to Android. For Android's case, you have to grant the game permissions to `android.permission.WRITE_EXTERNAL_STORAGE` and `android.permission.READ_EXTERNAL_STORAGE`. Since those permissions technically don't existed in Android 13 and up, the game can't request them. You can find the instructions to [grant them here.](User's-Permission-Shenanigans)

### My game CRASHES when I loaded into a game save or playing

If you're using mods, [skip to this section](#my-game-crashes-when-i-loaded-into-a-game-save-or-playing-with-mods).

This might be a bug in the game. If you can recall, please take notes of:  
* Steps you did to get the game crash.  
* Save that you played with, if possible, please provide the save too.

Please provide those notes when you're reporting in [issues](https://github.com/Alexofp/BDCC/issues/new) or the game's discord [report-a-bug channel.](https://discord.com/channels/972105858932678656/973843818996727818)

# Modding

### How do I install mods?

[How to install BDCC mods](How-to-install-BDCC-mods)

### How can I manually install mods?

[Manually installing mods](How-to-install-BDCC-mods#manually-installing-mods)

### My game hangs when loading into main menu while the game had mods

Please wait until it finishes loading. If you're on Android and you tap the screen, it will prompt you to stop the game since technically its not responding.  
We don't know what exactly cause the pause but its likely read speed and device's performance.

### My game CRASHES/force close when loading into main menu while the game had mods

This might be Android only issue since it's necessary to tap on the screen for preventing the phone to go to sleep. And since you're tapping on the screen while it is technically not responding, Android will ask user to stop the game.

Android also has unique way to use mods, its the fact that the game **requires BDCC.pck to be rebuilt every update**.  
Please try to rebuild BDCC.pck then try to start the game

There might other reasons such has mods force closing the game or your device is out of memory.

Although, you can try to mitigate the problem by doing these steps:  
1. Clear your RAM
   * Your phone might come with performance booster so use that to clear your RAM.
2. Clear your cache
   * Clearing your cache might help make the game load "smoothly" (not tested but some say it helps).
3. Upgrade your phone
   * If you already tried all of those options then it about time to upgrade your smart phone.

if this happens on other devices than android then please try without mods first, if the issue persisted please report it as a bug using same information as [this section](#my-game-crashesforce-close-when-loading-into-main-menu). 

### My game CRASHES when I loaded into a game save or playing with mods

There might be bugs in the mods. If you can recall, please take notes of:  
* Steps you did to get the game crash.  
* Save that you played with, if possible, please provide the save too.
* What mods were you playing with.
* If possible, which mod caused it.

Please provide those notes when you're reporting in [mods-discussion](https://discord.com/channels/972105858932678656/1026503369579302922) on discord or contract one of the channels the mod provides you.

### The body part skins' is not colored!

Some body part/skins mods doesn't support skins because they came before skins exists. We cannot fix those mods magically. [See issue #1 of Alexofp/BDCCMods.](https://github.com/Alexofp/BDCCMods/issues/1)
