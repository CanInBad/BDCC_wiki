# Intro

Heya. If you're here, you want to learn how to use the visual scene creator. So let's go. The cool thing about datapack scenes is that they can be created entirely from inside the game. 

Go to the datapacks menu. Create a new datapack and then create a new scene, give it some random id like `test_scene`

<img src="https://github.com/user-attachments/assets/eee0eeb1-fae6-48be-bc5b-75a52c03c74c" width="50%">

That's how it will look. Not very scary so far. Here you can give the scene a name and add some dev commentary (if you want).

Switch to the `States` tab. That's where you will be doing most of the work

# States tab
![pic](https://github.com/user-attachments/assets/86da1ef4-5948-4fda-9bf3-fc288cdfff61)

That's how it will look for a new scene. Let's go through all the panels.

![pic](https://github.com/user-attachments/assets/37f0db34-e5b6-4e16-a09a-b972e0afbc4e)

That's a list of 'states' that your scene has. Each state is basically a different screen of your scene. By default you only have the 'initial' state. The initial state is the one that the player sees first when the scene runs. But scenes will almost always want to have more than one 'screen' so you can add new states here and switch between them by choosing them in the list.

There are also buttons here for removing, duplicating, renaming and re-arranging the states. Re-arranging the list has no effect on anything, it's just for you.

Keep in the mind that the inital state can not be removed/renamed, it must always exist. And also, internally, the initial state is actually an "" (empty string) state, the editor just shows it as initial for your convinience. This will be important when we will start adding buttons that change the current state.

Next is..

![pic](https://github.com/user-attachments/assets/350aa61d-49ac-4b44-b53c-faa37adc6d84)

Like the title says, this is 'code' for your currently selected state. There is nothing there yet but that dark line is where you will drag various 'code blocks' onto to compose your scenes.

Each state has its own code. This code gets executed when the player sees this state. Code can trigger functions that output text and add buttons that the player can read and press. You won't have to actually write code, it's a visual code editor. Very similar to Scratch if you ever used that.

Below there are Undo and Redo buttons that will allow you to undo changes that you made to the code. Keep in mind that if you pick another state, all the undos are forgotten.

The `Test` button allows you to execute the code inside the editor and see the output without having to actually play through the scene. It's useful to test how certain blocks work.

And the last panel is..

![pic](https://github.com/user-attachments/assets/133a8f21-8d99-46d7-8399-316e4a887340)

This is where you will find all the code blocks that the scenes support. They are grouped by their role. Open the groups to see the actual blocks.

![pic](https://github.com/user-attachments/assets/bb9495bc-e743-438b-bd63-5802051110b3)

Yes, there are -many- blocks but trust me, you only need to know about a few to start making scenes. The rest you can learn as the need arises.

As you can see, the blocks can have different colors and 'borders'. And some blocks even have space for adding more code (the dark lines with a half-transparent v)

Some blocks also have 'slots'. Like the 'IF' block has a slot for its condition. The idea of slots is that you can put another block in there. Composability of blocks is what makes this system really powerful. But, again, you don't have to worry about it much for now.

# Hello world
Alright. Let's make a simple 'Hello World'.

Navigate down to the 'Variables' group of blocks and open it. The first block will be a 'Console Print' one. It's useful for outputting debug info that the player won't see. Drag-and-drop it into the middle panel, onto the dark line. So it should look like this:

![pic](https://github.com/user-attachments/assets/d86535e6-e257-48e2-baf1-6512e20c2142)

If you press 'Test' now, you won't see any output. That's because we didn't type any text so it is outputting an empty string.

Click on the empty space to the right of 'Console Print' (on its slot, between the ( and ) ) and type in 'Hello World'. Then press 'Test'.

https://github.com/user-attachments/assets/b076202e-9dcd-4662-b506-80193799f9f5

You should see the same text appear below the 'Test' button. Good job!

Now let me show what 'composability' of blocks means. Open the 'Math' group, it contains all the blocks related to numbers. Grab the first one '+' and drop directly onto that 'Hello World' text that you typed. It should look like this.

![pic](https://github.com/user-attachments/assets/6ccca659-3ac5-420c-930b-7d910bb99554)

The plus block just sums two numbers together. Feel free to type some random numbers in like 23 and 46. Then press the 'Test' button again.

![pic](https://github.com/user-attachments/assets/f208e520-f903-4a78-af15-87ce9005e25b)

As you can see, the 'Console Print' block has outputted the result of the '+' block. Nice! Feel free to grab another math block and drag it onto one of the slots of the '+' block. You can compose these blocks as much as you want to get any math expression that you want.

To delete a block, just drag it back onto any empty space on the right. You can also double-right-click on it to delete it. (if you deleted a wrong block, you can always undo it with the undo-redo buttons).

# Types of blocks
The border of a block helps you understand how it is supposed to be used.

![pic](https://github.com/user-attachments/assets/edb6f894-0d55-4836-a4e0-78f90e2345ce)

The `<` and `>` border means that its a boolean logic block. It will either be true or false. These are usually used as conditions for the 'IF' block.

![pic](https://github.com/user-attachments/assets/f2d99fb4-6573-4375-a251-f4b7a58a32b4)

The `(` and `)` border means that its a block that gives you some kind of value. This value can either be a number or a string. As you can see, the '+' blocks takes 2 values (in its 2 slots) and gives you a value back (a sum of them). If you look at the '>' block, it also takes 2 values as inputs but it has a `<` and `>` border because it outputs a boolean (true or false, depending on if the first number is bigger than the second one or not).

Very often you will be able to just type in (or select) a 'raw' value into the value slots. But as soon as you drag any block into that slot, that 'raw' value will no longer be used.

![pic](https://github.com/user-attachments/assets/0eff3e91-8bb5-4548-a575-683d468b889f)

The blocks that have a little `v` as a border are 'calls'. These blocks usually actually do something. For example, this particular block adds a specified amount of pain to the selected character (but this block also has different 'modes' too, press on 'pain' to see what else you can add other than pain). These blocks might or might not 'return' something, depepends on the block. Most of the time these will be top-most blocks.

# Creating a simple scene
Alright, alright. You probably understand what blocks are. But how do you use them to create a playable scene?? Let's do this.

Remove all the blocks and open the 'Scene' group instead. It contains all the blocks that you need to create a scene.

First block looks like this and its actually the most important one.

![pic](https://github.com/user-attachments/assets/749c9e48-71eb-41a5-9868-835c162363ac)

This block outputs text that the player can see. It's big because it allows to output multiple lines. And you can also open a full-screen text editor by pressing the 'full screen' button. The fullscreen text editor has many buttons for formatting your text and also a button to spell-check its contents (using an online API).

![pic](https://github.com/user-attachments/assets/109b5a04-a4d5-4ae0-ae3f-da1fc708c24f)

Type in some text and then press the `Run scene` button at the top-right corner of the editor (feel free to press `Save all` too, it will make sure you won't lose anything if the game crashes)

![pic](https://github.com/user-attachments/assets/29eadcc3-ad36-41cc-b5fd-bbe112e2c555)

If you did everything correctly, you should see the game running your scene and outputting the text that you have written.

![pic](https://github.com/user-attachments/assets/ec8611dc-1b2c-45a1-a425-f40ef2e6742a)

The text is there.. but there are no buttons, no way to interact with the scene! Let's fix that.

Press the special `BACK TO EDITOR` button to return back to the editor. Make sure to not to use the normal in-game menu for this! Or you will lose your unsaved changes!

Alright, now grab a green 'button' code block and drop it below the text one. It has a lot of stuff in it but you should only worry about the name and description slots for now, this is what the player will see. Write something there so it looks like this:

![pic](https://github.com/user-attachments/assets/bebbea9e-4faf-4a0d-9b14-d746ead293c4)

You can run the scene and notice that this button has indeed appeared.. but it's not doing anything if you press it.

That's because the third slot (a currently empty drop-down list) is actually the 'state' that the scene will change to when pressing this button.

So, now is the time to add a second state to your scene! Look at the 'States' panel and type in a name for the scene's second state before pressing the 'Add' button. When you do that, that state will appear in the list like so:

![pic](https://github.com/user-attachments/assets/84db3850-6dcb-4217-8c2a-b5248995e2b6)

Select it. When you do that, the blocks that we have dragged in previously will dissappear. That's because we are now editing the second state!

Drag in a text block there too and write some stuff that you want to see when the button is pressed.

![pic](https://github.com/user-attachments/assets/5c1ca9f6-98a9-4a65-8240-ea9ca16f57fb)

Alright. Now go back to the 'initial' scene and you will notice that the drop-down list of the 'button' block now has 2 entries. An empty one (this is the 'initial' state, internally its an empty string) and a second one that we have created. Pick the second one.

![pic](https://github.com/user-attachments/assets/34e56ec5-e8a0-46f8-b5a6-1da9b414a016)

Now run the scene and press the button. If you see the text of the second state, congrats! You can probably see how you can create scenes with this.

https://github.com/user-attachments/assets/aec3d39b-45d2-4090-8fe4-b25023d1d68d

Let's say you want the second state to have 2 buttons. One that will return back to the first state while hurting the player a bit and one that will end the scene.

Select the second state and drag in 2 'button' blocks. Give them names and descriptions and make sure the first one is set to the empty state (it will be by default). To make it damage the player, find a `add Pain` block inside the 'Game' group and drag it INTO the code of the button. You can add more blocks there if you want.

To make it so the second button end the scene, find an `End scene` blocks and do the same, drag it inside the code of the second button.

By the way, it's very important that you don't use (or at least try to not use) blocks that modify the game's state outside of the `add button` calls (getting the pain value of the player is fine but modifying it is not for example). Why not? The scene's state code gets ran every time the game needs to present the scene to the player.. Which is -usually- only once.. but if the player, for example, saves and loads the game, the scene code will be ran again! Another way to trigger that is using any debug action.

So, the rule is very simple. If you want to 'react' to the player's selected action, put these blocks into the code of buttons, they are guaranteed to run once.

https://github.com/user-attachments/assets/ca26b427-ef34-4b96-bcde-7dbe58ee3c65

The reason why it began playing an intro scene of the game when our scene ended is because that's how the editor scene runner works. It 'starts a new game' and then plays our scene on top. You can actually choose to play off of any save that you have. Press the 'Pick save' button and it will show you a list of all the saves that you have.

https://github.com/user-attachments/assets/7c05a300-6f44-4745-889a-0888674c2edf

This is very useful in case you want to test your scene with different player characters who might have different stats or bodyparts.

And that's mostly it. You can go explore all the different tabs and code blocks from here, I (Rahi) tried to make everything as intuitive as possible.

# Characters tab. Playing animations
Alright, you know how to make scenes about meowing into the void. But how do you add someone into the scene who can meow back?

That's where the characters tab of the scene editor comes in!

When you switch to it, you will see something like this:

![pic](https://github.com/user-attachments/assets/4182014c-dba1-4403-b89f-207ac8572d2a)

BDCC has a lot of characters.. And so trying to remember all the IDs or making you choose the right one out of a giant list each time would be very time-consuming and tedious. So, to aid you, I added ability to define a list of 'involved' characters. You fill this list only once per scene and then, in return, the editor will present you with this small list each time you need to choose a character in any block.

The player character (pc) is always involved in all scenes.. but to add others you just choose someone from this list and press the Add button. All the datapack characters should be first so you can find them without having to use the search.

I'm gonna add Rahi.

https://github.com/user-attachments/assets/241e01e8-98a6-4d50-b9a6-526f0b6f69a5

As you can see, a new entry has appeared in the list.

![pic](https://github.com/user-attachments/assets/fc44bd1b-48f7-44ef-a51c-9b41c2a86c86)

The first field is 'Alias'. It's basically a replacement for an ID. Alias is what you will see (and use) instead of the full character ID. The point of an Alias is that datapack character IDs are usually pretty long (because they also contain the datapack ID). And so the editor will actually strip that datapack ID when choosing an Alias automatically. But you can also choose a different alias for any added character, your choice!

Added on start checkbox.. does exactly what it says it does. If it's checked, the character will appear in the 'nearby characters' panel when the scene starts. So if I start the scene now I will actually get Rahi's portrait in the top left corner.

https://github.com/user-attachments/assets/f3dd49dd-5c3e-41a6-8996-bda242639f5a

If you want characters to appear (or go away) after some player actions, you can use the `add character` and `remove character` blocks from the Scene group. Here is how you do that:

https://github.com/user-attachments/assets/b888193e-3f46-4353-bcbf-383864652548

The variant field defines which portrait variant will be used (if the character is added from the start). Pretty much all the characters only have 2 portraits: "" (empty string) which corresponds to their normal portrait and a "naked" one which makes them appear naked. The second slot of the `add character` block also defines which variant of the portrait to use.

https://github.com/user-attachments/assets/be7c0912-f78d-4d86-a316-76dbac472c58

Alright, we have the characters appearing the nearby panel. But how do we make them say something?

There are 2 ways to do this:
First way is by using a `Say` block. You add it, pick the character and type in the text that you want that character to say.

https://github.com/user-attachments/assets/79ac7829-04bc-44ad-af1f-ad71c0d30b7a

It works but it might be annoying for you to have to constantly split your big output blocks with these small say blocks. And so the second way is here to help with that.

Rather than adding a new block, you can type..

`=char_alias: Text that you want to be said`

..straight in the output block (it must be on a new line and the = character must be first).

So here is how I'd make Rahi say the same thing but with this method:

https://github.com/user-attachments/assets/63ba7da6-ab3f-4e74-9eff-276f1c6816d7

Much simpler, right? But you're free to choose any method. The fullscreen text editor has many buttons that can help you to add various macroses that the game has so feel free to explore it. For example, if you want Rahi to say the player's name you can type in this:

`=rahi: Hello, {pc.name}!`

You can use any alias or ID instead of `pc`.

`=rahi: Hello, {rahi.heShe} {rahi.isAre} {rahi.name}.`

This will output: Hello, she is Rahi.

Alright. We can make the characters appear in the nearby characters panel and we can even make them say stuff.. but how do we actually make it so we can see them? How do we make them do animations? Well, the `Play` block will help you with that!

It works slightly differently than most blocks.. because there are just too many things you can tweak about an animation. So the way the works is: You drag it into the code and then you press on it to 'configure' it.

When you will do that, a window will open with all the settings. It should be self-explanatory I hope. You choose an animation on the left and then change its settings in the middle. To pick the characters that will participate in the animation look out for the 'pc' and 'npc' settings. You can also make them naked/hard/caged-up here.. and some scenes also have additional unique settings, feel free to experiment!

https://github.com/user-attachments/assets/45aabef5-3219-4a81-a671-a9e1360fe8dc

As you may notice, the player character is actually a white placeholder doll (because there is no player loaded in the editor) but all the other characters will look like their normal self.

Alright, well.. This should be enough to let you add characters into your scenes!

# Variables tab. Variables and flags
Your scene of petting a meowing Rahi is almost perfect.. But you get a feeling that it's missing something.. Something like a.. A pat counter, of course, obviously!

To create it, we will need to use variables. So let's learn how to do that.

When you switch to the variables tab for the first time you will see this:

![pic](https://github.com/user-attachments/assets/46f28fbf-f904-4e9f-92d4-0411cdc4b9cd)

Variables and flags work very similarly. The main differences are:
- Variables are stored per-scene, flags are stored for the whole datapack. This means that you can use the same flags in different scenes of the same datapack.. but you can't get access to variables of another scene. Each scene has its own variables!
- Flags will stay here even if there are no scenes running. All the variables and their values will be lost when the scene that has them ends. 
- Changed/accessed by different code blocks
- The player can edit datapack flags through the debug menu. They can't edit the variables

So, basically, you use variables for local scene progress and you use flags if you want to track something over multiple scenes (or if you want to save the progress of the same scene).

Since I don't care about saving the amount of pats for now, I will use a variable.

After you enter the variable name (I chose headpats) and press 'Add', a new entry will appear.

![pic](https://github.com/user-attachments/assets/021c6e08-3bea-4900-900d-52db4aa3f533)

The type and the default values are quite important. You can make a variable/flag have one of the 4 supported types:
1. Bool. These only have 2 values: true or false. Useful for something like a 'met_Character_X'  or 'scene_X_Happened' flags.
2. Number. Yeah, just a number. Supports a decimal point. Useful for something like a.. counter.
3. String. Useful for storing text.
4. Any. Means this variable can hold any kind of value (bool, number, string). Doesn't support default values, will return Null by default (a special value that means 'nothing')

Use Any type only if you really have to. The code blocks will actually give you a useful error if you try to assign a wrong kind of value to the variables (if try to assign True to a number variable for example).

So.. for my counter I will use a number variable. And I will leave the default value at 0

To get or set the flags/variables, you can use these blocks here:
 
![pic](https://github.com/user-attachments/assets/d5c9eaa7-b880-4cad-92a0-e14b34fa59fa)

![pic](https://github.com/user-attachments/assets/4d6b6670-19f6-47fb-b44b-177aa55f6f0c)

Orange ones are for the variables and the cyan ones are for the flags.

First block gives you the value of a selected variable. The next 3 blocks set the variable's value instead. You got one for bools, numbers and strings. And the last one increases the selected number variable by a certain amount.. which is what we want.

Drag the orange `Inc` block into the code of the 'Meow' button.. You will notice that you can then choose what variable you want to increase.

![pic](https://github.com/user-attachments/assets/659f0fcc-0bf6-494e-954f-c5f8c8677996)

We only have one variable defined but just know that all of them will show up here, you don't have to type the variable name out every time.

Okay, how do we see how many pats we did? I will just make Rahi say it.. Look at the video for the whole process..

https://github.com/user-attachments/assets/ad02b281-54db-44b4-bec4-965073f2b4cb

As you can see, I dragged the 'get' block into the text field of the 'say' block, making Rahi say the amount of headpats she received. If you want to make it so Rahi says more than just a number, there 2 ways to do it:
1. Using more blocks. The strings group has a 'concat' block which allows you to combine texts (or any values really) together.
2. Using string interpolation. These are scary words.. but it just means that you can insert the variables into the text by surrounding them with `{{` and `}}` like `{{headpats}}`.

The video shows both ways:

https://github.com/user-attachments/assets/83bebf62-fb4d-4e7d-afa2-d1bb761dbf52

The second way is probably easier. But it's your choice.

Alright, we can change and output variables.. but how do we make it so certain elements of our scene depend on the variables? With 'If' blocks!

'If-then' blocks allows to execute code depending on the condition. Let's make it so we can't exit the scene if we haven't patted Rahi at least 5 times.. and also let's make it so she purrs at 10+ pats. You can try to do it yourself or watch and follow the video.

https://github.com/user-attachments/assets/f4dab44f-1de8-4edd-b015-8efbc2ea095d

(The reason why the 5 got reset to 0 is because dropping the block updates all other blocks.. and since I was still editing the number as far as the UI was concerned, it reset the value to its previous one. You can avoid that just by pressing Enter after entering the number)

The '>=' math blocks means 'more than or equal'. It will 'succeed' (return true) if the left number is more than or equal to the right one. The opposite block is '<=' or 'less than or equal'. Just so you know ^^

Alright, well! For the last thing.. let's turn our 'headpats' variable into a flag, just to test how those work. You can watch the video and see me do it or try it yourself.

https://github.com/user-attachments/assets/fbf9bb5d-00f1-45e7-bd07-9deb7e9004ff

As you can see, I just removed the variable and added the flag with the same name.. and then switched all the blocks with their flag variants.. and that's it! And, also, you might have noticed that the string interpolation works with flags too (Rahi still says the amount of headpats with `{{headpats}}`).. Keep in mind that if you have both a variable and a flag with the same name, it's the variable that will be outputted!

The nice perk of flags is that you can edit them inside the debug menu. The video showed me doing it. And if the player decides to open this scene later, the amount of headpats will be preserved! As it should be.

Alright.. well.. now you can script your scenes with all sorts of logic! There are now almost no limits for you.

# Scene triggers. Making your scene show up in-game

You have crafted the perfect scene of giving Rahi headpats.. but how do you see it in-game, how do you 'trigger' it? The answer is.. with triggers!

Triggers define exactly -when- your scene will be shown to the player. There are many trigger types, too many for me to explain.. You can make the scene show up as soon as you enter a certain room.. or as soon as you encounter your datapack character.. or when eating in a canteen, working in mineshafts, taking a shower.. or.. or.. or..

You can also add any kind of conditions and even execute some code before running the scene!

I will show you how to make a simple trigger that adds a 'Pat Rahi' button to the player's cell. Pressing that button will launch our scene that we made.

Start by switching to the 'Triggers' tab. You will see a somewhat familiar screen.. but with some small difference there and there..

<img src="https://github.com/user-attachments/assets/107fa1cf-170a-43e6-95e4-c32b1e80cbde" width="50%">

Triggers are also composed out of code blocks.. but as you might notice, the 'Scene' category got replaced with 'Event' one.. that has some trigger-specific blocks.

Add a new trigger and select it in the list. That's how it should look:

![pic](https://github.com/user-attachments/assets/5d68cb77-feb0-48e0-acb4-d07368ddf770)

As you can see, we got some fields that we can edit.. and also a place to put our condition code!

Type defines what kind of trigger it is. Each one has some description written for it so don't be afraid to select different types and read it (Description won't change until you press Save, committing the change of type). Like I said, we want the scene to be trigger-able from player's cell.. so I will choose a `EnterPlayerCell` type and press save.

Execute type.. is a bit tricky to understand. But I will try. It has 2 values you can set it to: React and Run.
- React means our trigger is checked as soon as the selected event happens. This means the scene would run AS SOON as you enter player's cell (when the game is -reacting- to the player's last action)..
- Run means our trigger is checked when the scene output happens (when the current scene is being -ran-). This means that we can hook into this output and add our own text or buttons.

We want to add a button to the player's cell so we want to select the 'Run' execute type.

Trigger priority doesn't matter too much in this case. Just know that triggers with higher priority are checked first (but some trigger types override this behaviour and make it so the triggers with higher priority have a proportinally-higher chance to be executed first.. don't worry about it x3)

Alright! Now, the condition code will actually be super simple.. because we don't have any conditions.. So all we need is a `Add button` block that has `Run event` block inside it! `Run event` is a block that will run the scene that the trigger belongs to. But you can also run any other scene from your datapack with the `Run scene` block.. if you want.

After that, you should be able to launch your scene from the player's cell in normal gameplay. Just make sure to 'load' the datapack inside your save first.

This is the video of me going through the whole process:

https://github.com/user-attachments/assets/b2856458-df2c-46a5-8a1b-0425ad5b415d

If you want to also output some text too into the player's cell, add a big text output block so it looks like this:

![pat](https://github.com/user-attachments/assets/62050168-df7a-42bc-a294-c6767f5e2586)

Just as a last test, let's change it so the scene launches as soon as you enter your cell.. but only with a 20% chance.

To do that, switch the 'Execute type' to `React` and remove the `add button` and text output blocks, they won't work with this execute type anyway.

Instead, add an `If` block that has a `Chance` block in it's condition and a `Run event` block in it's code. Set the chance to 20.

Now, if you load the datapack, roughly each 5th visit of your cell will result in Rahi wanting headpats ^^. Watch the video if you want to see the whole process

https://github.com/user-attachments/assets/58d56329-218b-4b7f-9f6a-fae88b8af9c6

The RNG has decided to troll me a bit.. but you get the idea. By using flags you can make it so the scene only gets ran once.. or doesn't get ran unless some other scene happens first and sets the right flags. You can create whole storylines like this!

And that's most of what you need to be able to make your scenes show up in-game! You can add more than one trigger if you want, all with different conditions and types. Again, just don't forget that the triggers won't be checked unless you load the datapack!

# Quests. Turning our scene into a quest

Quests (or tasks) are pretty easy to add if you already have a scene made. Doesn't that sound a bit backwards? Maybe. But that's why it is so easy.

Basically, quests in BDCC don't control anything, the sole purpose of them is to guide the player. An example should help you understand.

Let's make a simple quest where you have pat Rahi 15 times through the scene that we created.

Start editing the datapack (quests are a separate thing from scenes). Scroll down and you will see a place where you can make a new quest. Press new, give it some name, all the usual stuff.

![pic](https://github.com/user-attachments/assets/c58ba396-be6a-4966-8aad-fbfc3cc1c6a1)

After that, you will see this simple form. Fill it out as you see fit.

![pic](https://github.com/user-attachments/assets/7d976a80-6e64-435b-814e-716768b3ff05)

The only difference between a main and a non-main quest is that main quests are displayed first in the task list. Quests with higher priority will be first. Simple stuff.

Switch to the 'Stages', you will see this (somewhat familiar) editor:

![pic](https://github.com/user-attachments/assets/09c09772-1170-442e-b749-6d2ee94b94f4)

Yeah, quests are made out of code blocks too. But it's very easy! Just try to understand how it works.

The most important bit is that quest code only gets executed when the player looks at the task list. And only then. The purpose of this code is to decide if the quest should be 'visible', 'completed' and also to output a list of stages. Each stage is just a line of text, something like "Pat Rahi 15 times!" or "Go pay Tavi a visit" or just "You did it, task completed!".

By default the quest will be hidden and not-completed. To make it appear in the task list, you add a `Mark Quest as Visible` block. If you want the quest to always be visible, you just add it on the top-most level, outside of any ifs.

![pic](https://github.com/user-attachments/assets/a6f3be91-5621-4efc-a9d5-ef9bb247385a)

If you want the quest to only be visible after some flag was set, you wrap it into an if statement. This is just an example:

![pic](https://github.com/user-attachments/assets/664532ac-adfd-4e35-9af8-6fd4b20aef2a)

Same for the quest completed block, you will usually just add it behind some flag check like so:

![pic](https://github.com/user-attachments/assets/a1738c22-829c-4e18-81da-6f31aa6b31b5)

Then, all you need is to add a few 'stages' using the big text output block. You can add more if checks to make certain stages appear in the task list after certain flags were set.

![pic](https://github.com/user-attachments/assets/47b6f486-65cf-40b6-acb3-e098917c59fb)

This is how your quests will usually look, just a bunch of ifs, flag checks and big blue blocks. Hopefully it makes sense.

I will now create a simple quest for our scene that we created during this tutorial. The quest won't be visible unless the player pats Rahi at least once. It will track the progress and mark itself as completed at 15 pats.

https://github.com/user-attachments/assets/471d2257-4a94-45a7-9794-17cb54137cc7

(Btw, you can duplicate blocks by holding Alt when dragging and dropping. You can duplicate entire chains)

As you can see, you can use string interpolation inside these output blocks too.

If you want to show the same 'Task added', 'Task updated' messages that the game's built-in quest have, you will have to add them into your scene yourself with the `add Message` block. (The game does that for its quests).

And that's it. Like I said, quests work pretty simply in BDCC, they're just here for show. But that also makes adding them easier as they don't affect the gameplay in any way.

# Good job!

If you're reading this, good job! Hope you are now able to create something with this editor. Make your dreams come true x3

I tried to show all of the basics but obviously I can't explain what every block does and how it works, you will have to explore yourself or ask around. I will try to show some advanced examples here: [Advanced stuff](Datapack-scene-creator.-Advanced-stuff)

Take care! Meow meow.