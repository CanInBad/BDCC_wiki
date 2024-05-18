Scene converter is a powerful tool that allows you turn scenes written in google docs into working code in two clicks as long as you follow the format that's outlined here. This saves time both for you (the writer) and the coder, eliminating the boring task of manually translating text into code. It also allows you to preview the scene inside the game.

What do you need:
- A text editor of your choice. I strongly recommend google docs as it catches most of the typos and grammatical errors while being free and widely used.
- Game.

Example of a simple scene:

```
sceneID=MyTestScene

! addCharacter(“rahi”)
! playAnimation(StageScene.Duo, “stand”, {npc=”rahi”})

Rahi enters the room.

=rahi: Hi, {pc.name}! I'm Rahi!

[[Wave hand, Do a friendly gesture, wave_hand]]
[[Pat cat, Pat Rahi on the head, pat_rahi]]

> wave_hand
You wave your hand.

=pc: Hello Rahi.

[[Continue, This will end the scene, endthescene]]

> pat_rahi
You pat Rahi. She purrs.

[[Continue, This will end the scene, endthescene]]

```

To preview this scene, copy it into the scene converter, then press Convert and then Test Scene. You don't need much more if you just want a scene with actions. If you want to run code when you select certain actions, you will have to use someone's help or by learning gdscript yourself.

![pic](https://user-images.githubusercontent.com/14040378/221592289-b4dfd327-6a1e-488c-af6c-5a353a8e9edc.png)

First line defines the id of this scene. This id must be unique across all scenes in the game. No spaces allowed `sceneID=<SCENE_ID_HERE>`

Lines that begin with `!` are gdscript code that will be executed at the same time when this section is shown. The first line will add Rahi into the nearby characters list. The second line will show the doll of Rahi standing near yours. Keep in mind that this code will be executed each time this section of the scene is shown. That means don't add code that effects the game's state there (like adding pain to the player for example) or these effects will be executed multiple times. The way to run code only once will be shown later.

Character's dialogue must always be on the new line and start with a `=` symbol followed by the character's id followed by a `:` symbol and then the text that the character says. If you wanna speak as the player, use `pc` for id. `=pc: Hello, Rahi!`

The commands like `{pc.name}` will be parsed and replaced automatically when the scene is shown. You can find most of the parser commands below.

Lines that start with `[[` and end with `]]` are options/buttons. The syntax is as follows: `[[BUTTON_TEXT, DESCRIPTION, ACTION_ID]]`. Action id is basically the section that you will jump to when pressing that button. To start a new section use `> SECTION_ID`.

`endthescene` is a special action id that is always available. It will end the scene. `[[Continue, See what happens next, endthescene]]`

# Parser commands
Parser commands are the special tags that will be automatically replaced when the scene is shown. Example is `{pc.name}`

They usually start with the character id (pc is player's id), followed a command. Sometimes the command requires arguments that you pass like you would pass an arguments to function in a normal coding language. `{pc.you} {pc.youVerb('take'}} something`

Most commands work for both player and npcs but not everything.


|Command|Description                  |Example output|
|-------|-----------------------------|--------------|
|pc.name| The visible name of a character| Player       |
|rahi.name|  | Rahi         |
|pc.nameS| Visible name + s            | Player's     |
|pc.he  | he/she/they/it depending on the gender| he           |
|rahi.he|                             | she          |
|pc.his | his/her/their depending on the gender| his          |
|rahi.his|                             | her          |
|pc.him | him/her/them depending on the gender| him          |
|rahi.him|                             | her          |
|pc.is  | is/are depending on the gender| is           |
|rahi.is|                             |is            |
|pc.has | has/have depending on the gender| has          |
|rahi.has|                             | has          |
|pc.himself| himself/herself depending on the gender| himself      |
|rahi.himself|                             | herself      |
|pc.verb('take')| adds s depending on the gender| takes        |
|rahi.verb('take')|                             | takes        |
|pc.penis| full penis description      | large knotted cock|
|pc.penisSize| penis size                  | large        |
|pc.penisDesc| penis description word      | canine-shaped|
|pc.penisSizeStr| penis size in cm            | 15 cm        |
|pc.breasts| full breasts description    | soft perky breasts|
|pc.breastsSize| breasts size                | perky        |
|pc.breastsDesc| breasts description word    | soft         |
|pc.thick| thickness description word  | fit          |
|pc.masc| masculinity/femininity description word| girly        |
|pc.inmateType| inmate type                 | general      |
|pc.milk| fluid generated by breasts  | Milk         |
|pc.cum | fluids generated by the balls| Cum          |
|pc.analStretch| how stretched is the anus   | very tight   |
|pc.pussyStretch| how stretched is the pussy  | slightly loose|
|pc.throatStretch| how stretched is the throat | very tight   |
|pc.you | If player = you. If npc = npc name| you          |
|rahi.you|                             | Rahi         |
|pc.youHe| If player = you. If npc = he/she/they| you          |
|rahi.youHe|                             | she          |
|pc.youHim| If player = you. If npc = him/her/them| you          |
|rahi.youHim|                             | her          |
|pc.yourHis| If player = your. If npc = his/her/their| your         |
|rahi.yourHis|                             | her          |
|pc.your| If player = your. If npc = npc name + s| your         |
|rahi.your|                             | Rahi's       |
|pc.youAre| If player = are. If npc = is/are depending on gender| are          |
|rahi.youAre|                             | is           |
|pc.youVerb('take')| If player = no change. If npc = adds s| take         |
|rahi.youVerb('take')|                             | takes        |
|pc.yourself| If player = yourself. If npc = himself/herself| yourself     |
|rahi.yourself|                             | herself      |

If you wanna capitalize the output, capitalize the first letter of the command. Example `pc.He` would become He

> [!NOTE]
> For more commands, you can look inside [res://Util/GameParser.gd](https://github.com/Alexofp/BDCC/blob/58885806c1bb8254ce250a56a08d241d5a106623/Util/GameParser.gd#L66-L351)

# Running code when picking an action
This is an example of running code

```
[[Give me credit, Gives you one credit, give_credit
GM.pc.addCredits(1)
addMessage("You received 1 credit")
return # This return prevents us from going to give_credit section
]]
```
Everything between the first line and the last line is gdscript code that will only run once when you pick this action. You can also change the flow using the `setState("SECTION_ID")` function. Just don't forget to add `return` at the end or it will be overritten

```
sceneID=RandomFlowScene

Lets flip a coin.

[[Flip coin, See what happens, flip_coin
if(RNG.chance(50)):
	setState("if_won")
else:
	setState("if_lost")
return # important
]]

> if_won
You won!

> if_lost
You lost. Aw.
```

# Fights
Here is a simple example scenes that involves a fight

```
sceneID=RishaFightExampleScene
Risha wants to fight you!

[[Fight, Begin the fight, start_fight
runScene("FightScene", ["risha"], "risha_fight")
return
]]

[[[onSceneEnd, risha_fight
processTime(20 * 60)
var battlestate = _result[0]

if(battlestate == "win"):
	setState(“if_won”)
	addExperienceToPlayer(30)
else:
	setState(“if_lost”)
]]]

> if_won
! playAnimation(StageScene.Duo, "stand", {npc="risha", npcAction="defeat"})
You won against Risha!

> if_lost
! playAnimation(StageScene.Duo, "defeat", {npc="risha"})
You lost against Risha! Prepare to be fucked!

```

# Variables
You can define variables with `%var` command. These variables will be automatically saved and loaded when you save/load the game. The syntax is `%var VAR_NAME DEFAULT_VALUE`

examples:

`%var used_condom false`
`%var some_string "Hello world"`
`%var times_used 0`

You can then use these inside your gdscript code like normal variables

# Conditions
Allow you to show or not show certain parts depending on the condition

example:
```
? GM.pc.hasReachablePenis()
Player has a reachable penis. We can describe it by using {pc.penis}
?else
Player doesn't have a reachable penis
?!
```

```
? GM.pc.hasVagina()
Player has a pussy

[[Vaginal, Get your pussy bred, get_bred]]
?!
```

# String interpolation
Can be used to inject variables into the text. Or for conditional text too

examples:
```
%var some_text "asdsfgafdg"

Hello world, the variable some_text has {{some_text}} stored in it.
```

```
Hello. I will check if the player has a penis. Player {{"has a penis" if GM.pc.hasPenis() else "doesn't have a penis"}}. Easy.
```

# Full example
Here is a full example of a scene written in google docs that can be converted to code automatically:

[https://docs.google.com/document/d/1D2TNCRrZCFeMx8b4kI_U83yhRm8MzKro28AKQZU79UA/edit?usp=sharing](https://docs.google.com/document/d/1D2TNCRrZCFeMx8b4kI_U83yhRm8MzKro28AKQZU79UA/edit?usp=sharing)

There are 2 scenes actually. Don't copy the first >, it's not needed
