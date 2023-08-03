# TL:DR

Download this, it has everything you need to start creating skins + intructions

[BDCCSkinStuff.zip](https://github.com/Alexofp/BDCC/files/12252933/BDCCSkinStuff.zip)

Below is stuff for mod creators.

# Converting custom bodyparts
To make it so your custom bodyparts have support for skins do this:

Right click the mesh instance node -> change type -> select `MeshInstanceWithPattern`  (it's one below)

Edit properties. Pattern start and pattern size define what region of the skin image will this mesh use. These numbers use the grid of the skin guide! Pattern start of 0x0 and size of 1x2 means the body region will be used. Start of 1x0 and size of 1x1 means the human head region will be used

Bodypart slot defines which bodypart's colors will be used

If your mesh needs some kind of overlay that won't be affected by the skin, make a new sprite with that just overlay and drag it into the custom overlay property. Useful for things like gags/eyes/etc

If your mesh doesn't really fit any of the current areas on the skin guide, you can create your own custom pattern for that mesh. See any of the hairs, ears and dicks. If you're using a custom pattern, set the pattern position to 0x0 and the size to 1x1

If the cum overlay looks wrong, change the Cum Layer Scale property until it looks right (will have to restart the game to see the change)