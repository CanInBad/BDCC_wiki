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

https://github.com/user-attachments/assets/ca26b427-ef34-4b96-bcde-7dbe58ee3c65

The reason why it began playing an intro scene of the game when our scene ended is because that's how the editor scene runner works. It 'starts a new game' and then plays our scene on top. You can actually choose to play off of any save that you have. Press the 'Pick save' button and it will show you a list of all the saves that you have.

https://github.com/user-attachments/assets/7c05a300-6f44-4745-889a-0888674c2edf

This is very useful in case you want to test your scene with different player characters who might have different stats or bodyparts.

And that's mostly it. You can go explore all the different tabs and code blocks from here, I (Rahi) tried to make everything as intuitive as possible.