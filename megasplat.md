## MegaSplat integration

MegaSplat is a famous package of shaders on the Asset Store that offers high quality shaders for terrains. It includes a mesh shader that is perfectly compatible with Ultimate Terrains.

First, go to uTerrain inspector, in Voxel Types tab, and add or replace the terrain material with MegaSplat mesh material. Then, change the voxel-type-functions script of **all** your voxel types to "MegaSplatVoxelTypeFunctions". This displays a GUI which allows you to select textures and adjust some other parameters related to MegaSplat.

Finally, open the MegaSplat material inspector (just click on the material from Unity project view) and make sure to select "Triplanar" for Splat UV Mode and "World" for Space (just below).

That should be enough!