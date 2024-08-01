This page will try to teach some of the advanced topics related to the scene creator. I (Rahi) tried to make the editor as intuitive as I can but it still has a fair share of tricky stuff.

# Buttons that lead to random states
By default, the `add button` block will always point you to the same selected State. But it's fairly easy to add randomness here:

![pic](https://github.com/user-attachments/assets/940cc8ac-7cd8-44af-8f28-6da0c78b432b)

As you can see, by default the State will be switched to 'pc_lost'. But there is also a 50% chance that the state will be switched to 'pc_won' instead and the player will also get 10 credits. If you want to expand it to 3 choices, you wanna do this:

![pic](https://github.com/user-attachments/assets/fe6856ab-df60-49e6-a09f-6ac22980048b)

In this setup, there is a 5% chance that the player will get some sex. If they don't, there is a 50% chance that they will still win. You get the idea I hope x3

# Starting fights, running scenes
Your usual setup for a fight should look like this:

![pic](https://github.com/user-attachments/assets/4e3d00c0-b9eb-4c7b-b70d-c8c964fc47e0)

The player might win or lose every fight so you gotta prepare 2 states, one for winning and one for losing.

The `Run scene` and `Start sex` blocks only have one space for code. It gets executed when the other-scene/sex ends. You want to have a `Set state` block in there too so you can progress with your scene.

![pic](https://github.com/user-attachments/assets/f023c9ec-3955-42c0-9c41-a13e364b03c2)

Hope it makes sense

# React and Run
The tutorial explains it a bit but I will try to go in-depth here

There are 2 contexts where your code could be executed in:
1. React. When the player picks any option, the game starts to REACT to that. In this context, it is safe to end or run new scenes (and some other misc stuff). It is also the perfect time to change variables/flags and use game-related (or sex-related) blocks. But you shouldn't output any text there (except for the `add message` block, that one stores the messages until the next time the scene is displayed) or add buttons.
2. Run. When the game needs to display the scene to the player, it RUNS the scene code. This is the time to show all the scene output and present the player with buttons. Changing variables/flags here -could- leave to problems because there are situations which will lead to your scene code getting ran more than once! So if you are incrementing a variable by 1, this very much might happen more than once. Easiest way to trigger that problem is to save/load or use any debug action.

Let me try to visualize it. By default, everything is executed in RUN mode:

![pic](https://github.com/user-attachments/assets/eac3b29a-4caa-49eb-a7d4-c5c3bbaaaff6)

As soon as you add `add button` blocks, you get this:

![pic](https://github.com/user-attachments/assets/1036fa2b-9427-44ea-a8a7-e9ecd62aa2b1)

Button's code gets executed when the player presses it so it is executed in the REACT mode/context. The code of the `run scene` (and `start fight/sex` blocks) is REACT too (it's executed when the scene ends). Hope it makes sense.

Doing stuff like this is wrong:

![pic](https://github.com/user-attachments/assets/9c60fa4a-d203-4132-b9f3-58bda15612d9)

So, keep all the blocks that affect the game's state inside the `add button` calls (the `run scene`/`start fight`/`start sex` ones are fine too).
SETTING a variable/flag to a specific value is mostly fine (because if it gets executed twice we will just set it to the same value again). INCREASING a flag/variable is bad because it might be triggered more than once, resulting in a wrong result.

If you -really- want to increase a flag/variable inside the RUN context, use the `Run code once` block. It tries to make sure that the code inside only gets ran once (it will not run the code if you save/load/use a debug action). But, you know, might as well keep all the var editing inside the `add button` calls.

![pic](https://github.com/user-attachments/assets/a601850e-3996-4b14-9b73-c6d6c7fe79d1)

# Button checks
You might have noticed that `Add button` block has a 'CHECKS' button. It allows you to easily add extra conditions to the button. For example, for sex that requires pc to have a vagina, you want to add a `HasReachableVagina` check. The difference between `HasReachableVagina` and `HasVagina` is that `HasReachableVagina`/`HasReachablePenis` will not 'succeed' if the player their penis/vagina in chastity.. so you usually want a 'Reachable' variant.

![pic](https://github.com/user-attachments/assets/16b0defb-9a37-48a4-b3d6-61ac92c9b5a7)

If there are more than one Check, they ALL will be required to be fulfilled.

# Typical sex progression
For a typical hand-written sex scene, you usually want to have this order of sex blocks:

![pic](https://github.com/user-attachments/assets/0f45d130-1494-4f91-a733-8b550ae971f3)

Time processing is important because it would help to generate some cum in player's/npc's balls (if they are spent for example)
Then the fuck block to stretch the hole
Then the cum inside block.. to cum x3
The orgasm block is important to be last because it will actually drain the balls of the one who's orgasming. So you want it to always be -after- the cum inside blocks. Orgasm block is also the one that sets the Lust to 0
You can add the opposite orgasm block (npc orgasms from pc) but that's not really required. Only if you want to

# Condoms in sex
For an optional condom support in your (hand-written) sex scene, you usually want 3 variables:
- CondomUsed (boolean)
- CondomBreakChance (number)
- CondomBroke (boolean)

Then you can present the player with an option to go raw or use a condom (make sure the condom button has a `HasCondoms` check added to it)

![pic](https://github.com/user-attachments/assets/5e72cf5b-6a2a-4c16-af69-4cfe5da15bb2)

Then, you can make each sex animation automatically show up with a condom if you make it read the variable like so:

![pic](https://github.com/user-attachments/assets/e7634888-b020-49d2-83c8-d4a612d68802)

Then, when it comes the time to cum, you can check if the condom broke like so:
![pic](https://github.com/user-attachments/assets/725b7c8d-072e-495f-be32-1934b8046943)

Yeah, it's a bit clunky. That's the best I got x3. Sorry

# Sex scenes with strapons
Adding strapon scenes is a bit clunky too, sorry x3

First, you want a special State where the player can choose one of their strapons

![pic](https://github.com/user-attachments/assets/4ccf06f8-1b5f-48b2-a8fa-1c7b6df45d78)

The `Add strapon buttons` adds a button for each strapon that the player has. Selecting any strapon will make the Wearer (pc in this case) put it on (But it's always the player's strapons that are offered! It's just that you can make an npc wear one of the player's strapons if you want). Then the state will be set to the selected one (sex_begins in this case) and the code will be executed (nothing in this case). It's important to let the player cancel the scene in case they don't have any strapons (otherwise they will soft-lock)

Then, after the sex scene ends, you want to return the strapon back to the player's inventory like so:

![pic](https://github.com/user-attachments/assets/4ad8aeb1-744e-4d9f-b284-489af773fbcf)

You get the idea hopefully x3. The `Cum inside` block has a strapon mode that allows to cum using the strapon's contents (if there are any)