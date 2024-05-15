# Floors Basics

Floors can be registered by putting the script and scene file in `res://Game/World/Floors`, or it can be registered with a module calling a method `registerMapFloor(id:string, path:string)` in `GlobalRegistry`  
If the ID existed already, it will replace the floor entirely with new one.  
Registering new floor requires scene file (will go into detail next section).  
For example:
```gdscript
GlobalRegistry.registerMapFloor("grindingFloor","res://Modules/Z_IgrindingFloor/Floor/grindingFloor.tscn")
```
This will register a floor with ID "grindingFloor" with the path `res://Modules/Z_IgrindingFloor/Floor/grindingFloor.tscn`

# Floor anatomy
<sup>aka scene file</sup>

Each floor is consisted rooms in 64 unit grids in both X and Y axis, if they're unaligned, on runtime it will automatically snap to nearest point in a grid\*

*\* its not exactly nearest point, please check [these lines](https://github.com/Alexofp/BDCC/blob/58885806c1bb8254ce250a56a08d241d5a106623/Game/World/World.gd#L169-L170)*

![Editor showcasing a floor with grid turned on](images/mapEditing1.png)

Each room must be assigned to **unique** ID, if 2 rooms have the same ID, whichever load last get rejected, this also applies to other floors.
