This page will try to teach some of the advanced topics related to the scene creator. I (Rahi) tried to make the editor as intuitive as I can but it still has a fair share of tricky stuff.

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
