<div class="documentation">

## Download Ultimate Terrains

You can download Ultimate Terrains through the [Asset Store](https://www.assetstore.unity3d.com/en/#!/content/31100 "Download Ultimate Terrains"). Welcome to the community of uTerrains users! :)

If you are still hesitating, you can try the [online demo](/demo/ "Demo"), get a look at the most [popular questions](/questions-answers/ "Answers") or ask for details on the [official Ultimate Terrains thread on Unity's forum](https://forum.unity.com/threads/uterrains-ultimate-terrains-voxel-terrain-engine.383959/ "Forum").

## Installation instructions

Installing Ultimate Terrains is a very simple process.

### Install with Unity 5.6 or Unity 2017

Ultimate Terrains is fully compatible with Unity 5.6.x and Unity 2017.x, however it is **strongly recommended** to use Unity 2018 as **it will run approximately 2 times faster with it**.  
So if you _can_ update your Unity version, **do it**!

If you are obliged to keep an old version of Unity, follow these instructions:

Just download and import Ultimate Terrains into your project like any other asset. All files are mandatory so please import everything.

To complete the installation you may need to restart Unity in order to get the new menu under Tools > uTerrains.

That's all! If you get any error at this point, try to re-import Ultimate Terrains in a blank project, so you can check if the problem comes from your project or not. In particular, if you are updating an existing project, you should remove the uTerrains folder before importing the new version (be careful to not lose your own scripts if you do so!). You shouldn't get any conflict with other assets, but if you do please [let us know](/report/ "Report a bug").

### Install with Unity 2018 or more recent

Unity 2018 or more recent version is highly recommended to get the most out of Ultimate Terrains. Installation is still very simple, but you'll have to do a small configuration change in your project settings (recommended, not mandatory).

**<u>Before importing Ultimate Terrains into your project, set the _Scripting Runtime Version_ to _.NET 4.x Equivalent_ in _Player Settings._</u>**

Go to Player Settings (Edit > Project Settings > Player) and select **.NET 4.x Equivalent** as Scripting Runtime Version.

Once this is done, download and import Ultimate Terrains into your project like any other asset. All files are mandatory so please import everything.

To complete the installation you may need to restart Unity in order to get the new menu under Tools > uTerrains.

That's all! If you get any error at this point, try to re-import Ultimate Terrains in a blank project, so you can check if the problem comes from your project or not. In particular, if you are updating an existing project, you should remove the uTerrains folder before importing the new version (be careful to not lose your own scripts if you do so!). You shouldn't get any conflict with other assets, but if you do please [let us know](/report/ "Report a bug").

## Getting started

Before starting, just a word to say that you can get more explanation about almost any parameter in Ultimate Terrains just by hovering it (wait 2s and it will display help). This is very useful to get more information about a field without having to go to the documentation all the time.

### Example scenes

If you want to see directly what kind of things Ultimate Terrains can do, you can open the provided example scenes (in the folder Assets/uTerrains/Scenes) and just press 'Play'.  
You can use these scenes to get an idea of how to setup a terrain, but I strongly recommend that you actually setup a scene from scratch by yourself so you will understand what's going on and what parameters stand for what.

### Overview in video

<iframe src="https://www.youtube.com/embed/gpsxX0kHlHI" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

### Setup your terrain from scratch

Everything has been made so you can start using Ultimate Terrains in a few minutes only. However, you will need some time to understand all parameters and to learn how to create the terrain you want.

Let's start with a blank, new scene. Please, create a new scene (File > New scene).

Then just add a player to your scene. You can drag & drop the FreeFlyPlayer prefab from uTerrains/Scenes/Misc folder (don't forget to remove the default scene camera if you do so). If you use your own prefab, just be sure to disable gravity (or to add a platform below it) otherwise your player will fall while the terrain has not been generated yet. We'll see later how we can prevent this.

All right, let's begin!

Add a new ultimate terrain to your scene: in the top menu of Unity, click on _Tools > uTerrains > Add terrain_. This will open a window where you can change the base settings of the new terrain. Don't worry, you will be able to change any of these settings later in the Ultimate Terrain inspector.

[![](https://uterrains.com/wp-content/uploads/2018/10/newTerrain-300x154.png)](https://uterrains.com/wp-content/uploads/2018/10/newTerrain.png)

Drag & drop your player object (this can be the camera) into the _Player Object_ field.

Drag & drop the material you want to use in the _Main Material_ field. You can use the included materials under Assets/uTerrains/Materials/Terrain.

Click OK.

You should now see a new object (named 'uTerrain' by default) in your scene. Select it to display the terrain inspector.

[![](https://uterrains.com/wp-content/uploads/2018/10/uTerrainHierachy-300x160.png)](https://uterrains.com/wp-content/uploads/2018/10/uTerrainHierachy.png)

As you see, the uTerrain inspector has 6 main tabs:

*   Voxel Types
*   Biomes
*   Scenery
*   Editor Tool
*   Global Settings
*   Documentation

Before going further, **you have to define a layer for chunks**. Go to the 'Global Settings' tab. You'll find a parameter named "Chunk layer" at the bottom of the 'General Settings' section of this tab. Please create a new layer and select it. Leave all other settings as-is.

Now let's go back to the Voxel Types tab.

#### Voxel Types

[![](https://uterrains.com/wp-content/uploads/2018/10/voxeltypestab01-845x1024.png)](https://uterrains.com/wp-content/uploads/2018/10/voxeltypestab01.png)

At the top of Voxel Types section, you can add one or more Terrain Materials. They are the material(s) that will be used on the terrain. You should see the material you've selected a few minutes ago in the Create Terrain window.

Just below, you can configure global parameters of grass and add one or more Grass Materials. As you can imagine, they are the materials that will be used for grass. We'll leave it empty for now.

Below this, you can add one or more Voxel Types. Typically, voxel types could be 'Grass', 'Rocks', 'Snow', 'Forest ground' etc. It will more or less match the different textures of your terrain.  
In the end, a voxel type is just a set of parameters. Indeed, each voxel type must specify:

*   a Name which must be unique. This parameter is important as it will allow you to reference it in biomes (that we'll cover after).
*   a Material Index corresponding to the index of the material to be used by voxels of this type. Remeber the Materials you added right before? This is about it.
*   a Priority which must be unique. In case there are several candidates for a voxel, the one with highest priority will be chosen over the others.
*   the Blockiness which determines if voxel of this type will look more or less cubical.
*   the VoxelTypeFunction which is a script that determines the color of vertices generated by voxels of this type. The default one simply returns a predetermined color that you have to specify in the 'Vertex Color' field right below.
*   then, you can choose to enable/disable grass on this type of voxels. For now, we'll leave it disabled.
*   finally, once you will have defined some details and trees (we'll see it later), you'll be able to choose which details & trees can be spawned on this type of voxels.

Your terrain should already have one voxel type that has been created for you. Change its name (let's say, "My Voxel Type") and leave the other values as-is.

[![](https://uterrains.com/wp-content/uploads/2018/10/firstVoxelType-300x251.png)](https://uterrains.com/wp-content/uploads/2018/10/firstVoxelType.png)

You can add as many voxel types as you want, but for now, one is enough.

#### Biomes

Move now to the Biomes tab. This is where you define how your terrain gets generated.

[![](https://uterrains.com/wp-content/uploads/2018/10/biomesTab-204x300.png)](https://uterrains.com/wp-content/uploads/2018/10/biomesTab.png)

##### Preview

The first section of the Biomes tab is called 'Preview'.

[![](https://uterrains.com/wp-content/uploads/2018/10/preview-300x112.png)](https://uterrains.com/wp-content/uploads/2018/10/preview.png)

From there, you can generate the terrain within the editor and watch the result in the scene view, just like with a standard Unity terrain. The 'Hot Reload' button allows you to re-generate the terrain to see more quickly how your biomes configuration affects it. It is faster than stopping and re-starting the whole terrain generation again, but it is limited and doesn't refresh vegetation such as trees.

For now, no biome as been created, so our terrain cannot be generated. Move on to the section right below, the 'Biome Selector'.

##### Biome Selector

Ultimate Terrains can handle multiple biomes on a single terrain. In this tutorial, we'll just create a simple terrain with only one biome.

You have to fill the 'Biome Selector' field. You can notice there is an error displayed in the inspector (just below this field) that tells you no script has been selected yet. The terrain cannot even start without it.

[![](https://uterrains.com/wp-content/uploads/2018/10/biomeSelector-300x71.png)](https://uterrains.com/wp-content/uploads/2018/10/biomeSelector.png)

As its name suggests, a Biome Selector tells Ultimate Terrains what biome should be used at a given world position. By using some noise functions (such as Perlin), altitude, or whatever you'd like, you can spread biomes procedurally. A very common example is to select biomes based on the altitude, like having one under-water biome and one land biome.

Anyway, for now as we said, we just want a single biome. Click on the field to select a script and search for 'UniqueBiomeSelectorSerializable'. Choose it.

You may have noticed there is a 'UniqueBiomeSelector' script and a 'UniqueBiomeSelectorSerializable' script. The first one is the actual implementation (doing the job at runtime) while the second one is in charge of displaying the editor GUI proper to this script (if any) and save its fields value. This is why in the editor you will always choose the scripts that end with 'Serializable'.

The UniqueBiomeSelector is the most simple selector you can imagine: it always returns the first biome defined on your terrain. It doesn't have any parameter.

##### Create a biome

All right, you are now ready to create your first biome. Look at the next section of the Biomes tab, simply called 'Biomes'.

[![](https://uterrains.com/wp-content/uploads/2018/10/biomeList-300x112.png)](https://uterrains.com/wp-content/uploads/2018/10/biomeList.png)

One biome as already been added by default, but it has no name yet. Give it a name.  
Note: you can click on the 'Add biome' button to add more biomes to your terrain, but we don't cover multiple biomes here.

Then, click on 'Edit Biome'. This opens a new windows that probably raises some questions and needs some explanation!

Before going further, please resize the window so you can view the whole picture.  
You should see a graph with these different nodes:

*   3D position
*   2D position
*   2D Generators
*   3D Generators
*   Final Combiner
*   and Voxel.

[![](https://uterrains.com/wp-content/uploads/2018/10/biomeEditor-1024x422.png)](https://uterrains.com/wp-content/uploads/2018/10/biomeEditor.png)

It is important to understand that this graph represents the workflow of voxel generation.

You have to read it from left to right:

1.  we start by a voxel 3D position (x, y, z coordinates) as well as its 2D position (x, z coordinates)
2.  the 2D position is the input of 2D values generators (if any) in the 2D Generators node. For example, this can be 2D Perlin noise like Perlin(x, z). 2D values generators are commonly used to create the ground of a classical height-based terrain (mountains, etc.).
3.  the 3D position is the input of 3D values generators (if any) in the 3D Generators node. For example, this can be 3D Perlin noise like Perlin(x, y, z). 3D values generators can be used to create caves, overhangs or floating islands for example.
4.  all values generated by 2D & 3D generators, as well as the voxel 3D position, are the input of the 'Ultimate Combiner' which uses all these values to finally set the definitive voxel value and type (you know, the voxel type we talked before).
5.  as a result, a voxel gets generated.

Ultimate Terrains comes with some 2D generators, 3D generators and Combiners so you can generate your terrain without the need to implement them by yourself. However, note that you have the possibility to implement your own ones. This makes Ultimate Terrains highly extensible and extremely powerful.

This is just a getting-started guide, so I won't deep dive about this here. If you want to know more (which I recommend if you want to get the max out of uTerrains), go to "Terrain generation / Biomes" section of this documentation.

Let's setup a minimalistic biome.

In the '2D Generators' node, click the field to select a 2D Master script (see "2D Master" section of this documentation for more info). Select 'Default2DMasterSerializable'.  
Click on 'Add 2D generator module' just below. Then, select 'HeterogeneousMultiFractal2DGeneratorSerializable'.  
For frequency, set 0.001 and for scale, set 80.

In the '3D Generators' node, click the field to select a 3D Master script. Select 'Default3DMasterSerializable'.

In the 'Ultimate Combiner' node, click the field to select a Combiner script (see "Final Combiner" section of this documentation for more info). Select 'BasicHeightmapCombinerSerializable'.  
In the voxel type name field, write the name of the voxel type you added previously (that should be "My Voxel Type").

Save your scene (Ctrl+S) and close the window.

### First run

Your terrain is ready to run. Press 'Play' and wait for the terrain to be generated. If you used FreeFlyPlayer prefab, it will probably raise an error because it is missing some setup, but you can just ignore it for now.

You should see your terrain. If you don't see anything, this is probably because the camera is below the ground of your terrain. Set its position Y to 300 for example. You can also move the scene-view camera to look at the terrain.

Stop it for now. The terrain disappears. Indeed, the terrain only exists at runtime. You can also create and edit the terrain from the editor without the need to press Play. To do so, go to 'Editor Tool' tab and enable 'Generate & display terrain in scene view'. Wait for the terrain to be generated. Once you're done, you can disable it to stop terrain updates within the editor.

[![](https://uterrains.com/wp-content/uploads/2018/10/editorToolTab-300x198.png)](https://uterrains.com/wp-content/uploads/2018/10/editorToolTab.png)

Each time you change terrain configuration, remember to reload it, because it is not automatically updated with new parameters until you restart it. Also, many parameters such as global settings cannot be edited while the terrain is displayed in the scene view.

Now, clear the terrain by disabling 'Generate & display terrain in scene view' and go to the Biomes tab again. Click on 'Edit Biome', and change the frequency value of the 2D generator module from 0.001 to 0.005. Press Play to generate the terrain. What do you see? What did it change?  
The mountains and the valleys are closer to each others. Actually, the look of your terrain has completely changed, just by modifying this little parameter. This illustrates how the biome configuration is important. It is the heart of your terrain configuration.

### Adding grass

Ultimate Terrains comes with a simple but powerful grass generator. Grass is generated depending on the voxel type, which allows to add different kind of grass to different parts of your terrain and to choose where to put grass and where not to put it.

Go to Voxel Types tab, scroll down to your voxel type and check the 'Enable grass' checkbox (you may have to unfold the voxel type by clicking on the little arrow at its left). New parameters appears to configure the grass.  
You can leave all the values as-is for now.

[![](https://uterrains.com/wp-content/uploads/2018/10/grass-232x300.png)](https://uterrains.com/wp-content/uploads/2018/10/grass.png)

At the top of the Voxel types tab, just below Terrain Materials, you will find the 'Grass Global Settings' section, and inside it, the 'Grass Materials' sub-section. You need at least one grass material. Click on 'Add Grass Material' and select 'WavingGrass01' material.

[![](https://uterrains.com/wp-content/uploads/2018/10/grassSettings-300x124.png)](https://uterrains.com/wp-content/uploads/2018/10/grassSettings.png)

Press Play to see your terrain with grass on it. When you're done, Stop.

Now, add a new grass material and select 'WavingGrass02'.  
In your voxel type, under grass parameters, click 'Add grass material' and set the value of 'Grass material index 1' field to 1 (which is the index of the second grass material you've just added: WavingGrass02).

Then, set the value of 'Probability 0' to 0.5.

Press Play again. You should now see the grass is a mix of the two grass materials. This allows to add different kind of grass very easily in order to get a nice result.

### Details objects

You have some grass, but you'd like to add some other plants or some stones or mushrooms or whatever details to your terrain. This is what details object are made for. In Ultimate Terrains, details objects are exclusively GPU instanced to avoir GameObjects overhead.

Go to the 'Scenery' tab, and 'Details' sub-tab.

Click on 'Add detail group'. A details group may be a set of stones, or a set of different plants for example. As you see, you can have one or more details objects per details group. A details object is defined by a mesh and a material. You cannot put gameobjects prefabs directly.

Give a name to your new details group (for example, "Stones"), and change its density to 2.

Then, go to Assets/uTerrains/Scenes/Misc/Rock_Set/Rock. There are an imported rock model, its texture and its material. Unfold the model 'Rock' and drag & drop its mesh into the 'Mesh 0' field of the detail object. Same thing for the material: drag & drop the 'RockMaterial' to the 'Material 0' field of the detail object.

Now you have a simple details group defined, containing a single detail object.

If you press Play, you will see that nothing changed! This is because you have to enable the details group on a voxel type to see it. Go back to the 'Voxel types' tab, and check the checkbox called 'Enable details 'Stones'.

Now, press Play. Thousands of little stones are spread over the ground! These stone don't look so good, I agree, but this is just an example. It's up to you now to use this for plants, wood sticks, mushrooms or whatever.

### Trees

All right, your terrain looks better and better, but it is missing one important thing: trees.

Trees are spawned independently from terrain generation. Thehe job is done in parallel of terrain generation. This is very fast and does not slow done the terrain.

Trees are spawned as gameobjects (not GPU instanced) so they can have colliders and so on. However, it is up to you to ensure that your trees has some LOD system. Ultimate Terrains won't generate billboards for you as the standard Unity terrain does. This is why I recommend to use SpeedTrees: they come with LODs and colliders out of the box.

Got to the 'Scenery' tab and 'Trees' sub-tab.

The first parameter 'Max LOD with trees' controls the distance (in term of terrain LOD) at which trees will be spawned. Set this value to 4.

The second parameter, 'Max trees spawned per frame', controls how many trees (at maximum) should be spawned per frame. 10 is generally a good value as it prevents lags.

Tree density is very important as it controls the average distance between two trees. This is more the inverse of the density actually, because the bigger it is, the less trees will be spawned. Set this value to 20.

Density noise controls the frequency at which the tree density varies. Indeed, trees are spread thanks to this noise to make it more realistic.

Finally, 'Trees height' represents the average height of a tree. This setting is extremely important as Ultimate Terrains will make sure there is enough vertical space before adding a tree somewhere. Ultimate Terrains also uses this internaly as a step to find where is the surface, so the lower it is, the longer it will be to spawn trees. Avoid to set a value lower than 10.

Below these settings, there is some space for Trees Groups.

Trees groups are similar to details groups, except that they contains a list of gameobjects (instead of mesh/material pairs). Click now on 'Add tree group', give it a name and drag & drop a tree object in the 'Tree 0' field. You can take a tree from SpeedTree that is available in the Unity's Environment package (menu Assets > Import package... > Environment).

Like for details, you have to enable the tree group on your voxel type otherwise it won't be used and no tree will be spawned.  
So go to 'Voxel Types' tab, and choose the tree group you've just created in the 'Tree group' dropdown of your voxel type.

Press play and see the result. You might be surprised to see that trees are spawned before the terrain has finished to be generated. This is because trees system does its job independently from terrain generation.

### What you've learned

This is the end of the Getting Started tutorial. You've learned how to setup a basic terrain from scratch, defining a voxel type, a biome and adding some grass, details and trees to it. You may still have a lot of questions (maybe even more than before!). You can deep dive each topic by reading the rest of the documentation.

## Global Settings

The tab 'Global Settings' contains a lot of very important parameters that control terrain size, quality, speed and more. Let's see what they do one by one.

### Infinite terrain

The first parameter is quite simple: is your terrain finite, or infinite? Finite terrains don't have specific advantages except that in a finite terrain, chunks are never destroyed to follow the player. Depending on what you want to achieve, this may be more suitable and save a bit of computation time by increasing the chance of using cached data.

### Chunk connection mode

This setting controls how chunks of different LODs should connect to each other.

Properly connected seams creates perfect transitions but requires to compute each chunk several times (to generate LOD transition versions).  
Skirts just adds some triangles to chunk meshes in order to make holes invisible. It is very cheap to compute, but it creates ugly artifacts.  
The third choice you have is to chose both of connection modes. This is heavier in computation time, but it is the safest way to avoid any possible visible hole between chunks of different LODs.

### Duplicate vertices

If enabled, Ultimate Terrains will duplicate each vertex so you can avoid texture stretching. This is more useful for cubical terrains.

### Compute tangents

If enabled, Ultimate Terrains will compute tangents for you. This is needed by some shaders (disable it if your shader doesn't need it).

### Acceptable geometric error

These settings are extremely important. The geometric error is related to the terrain quality. The lower it is, the better your terrain will look, but with a higher performance cost. If it's too low, the terrain will take too much time to get generated. If it's too high, your terrain may look ugly and even have holes!

Indeed, if the acceptable geometric error is too high, terrain generation could miss some voxels which you really want to avoid. There is no geomteric error value that works all the time: it really depends on your terrain (ie. biomes settings).

Max error multiplier on surface allows you to increase (or decrease) the acceptable geomteric error when surface has been detected. This is quite useful because you can lower a bit terrain quality (and save CPU) without the risk to miss voxels.

Max error multiplier on chunk borders allows you to ensure chunk borders are properly computed by decreasing the acceptable error on borders. This can avoid potential and unwanted terrain holes.

### Distance to be near the surface

This is the distance at which Ultimate Terrains should consider a voxel is really close to the surface and should make a special effort to ensure the surface won't be missed.

### Draw size (ie. build distance)

Draw size and vertical draw size are the number of chunks of highest LOD to generate around the user. For example, if you set the draw size (and vertical draw size) to 4, Ultimate Terrains will build 4 chunks in the front, the back, the right, the left, the bottom and the top of the player (so, 8x8x8=512 chunks).  
So, for example, if the highest LOD is 7, the size of a chunk in Unity's unit will be 1024x1024x1024, and consequently the size of the visible part of the terrain will be 8192x8192x8192.

### Level Of Details count

This defines the highest LOD to compute on the terrain. Each time you increase this by 1, you double the size of the terrain.

### Distance from LODs to each other

The next parameters allow to set how many chunks of a particular LOD you want to be generate before the next LOD starts. Generally, you want it to stay small in order to improve performance. Change it only if you want higher quality at higher distance.

### Initial chunk count per LOD

The following parameters simply allows to create some chunks at the very begining of the game and put them in a pool to avoid creating them at runtime (making possible lags).

### Max LOD with...

As you can guess, these parameters controls which LODs should have cache, colliders and so on. Keep these parameters as low as you can to improve performance. A special word for 'Max LOD with cache': when cache is enabled on a chunk, it will be faster to recompute in case an operation (like digging) is done on it. However, it consumes a lot of memory, so keep it low.

### Data path

This parameter is very important as it tells where terrain data (ie. operations) is stored on the filesystem. It must be a subfolder of StreamingAssets/uTerrainsData (you have no choice on this part) to ensure it will be included in your final build.

### Size of a voxel in Unity's world

This one is self-explainatory. This is the size of one voxel.

### Thread count

You can increase of decrease the number of threads dedicated to chunks generation. You should keep it under 3 unless you are sure the target CPU has more than 4 cores.

### Player object

This is the object around which the terrain will be generated. This is generally the main camera.

### Max time spent in post-building per frame

Post-building consists in applying computed mesh to a chunk object. It updates the mesh filter, the mesh collider (is any) and a few other things that can only be done on the main thread (Unity restriction). Post-building is very fast thanks to Ultimate Terrains that pre-compute almost everything in background threads, but if too many chunks get post-builded in a single frame, this would create lag.

To avoid this, you can setup the maximum time that must be spent in post-building per frame. For the same purpose, you can also limit the count of chunks to be post-builded in a single frame.

Keeping a max time spent / frame below 10ms should prevent FPS from droping under 60.

### Layers

You have to create a specific layer for chunks and select it in the 'Chunk layer' dropdown. This is mandatory.

You can also optionaly create a specific layer for grass.







## Editor tool

The editor tool allows to edit the terrain directly within the scene view as you would do with a standard Unity terrain.

It generates the terrain in the editor and temporarly replaces the player object of the terrain by the scene view camera, so the terrain is built around the scene view camera.

To begin, click on 'Start editing' and wait for the terrain to be generated. Then, you can select an operation (like Dig Sphere, etc.), change its parameters (like radius, etc.), and apply it by clicking on the terrain directly in the scene view.

Once you're done, you can click on 'Stop editing' (the terrain will still be visible in the scene view but won't be updated as the scene view camera moves) or on 'Clear' (the terrain will be destroyed and removed from the scene but all your modifications will be saved, don't worry).





## Realtime terrain editing

In Ultimate Terrains, terrain can be edited at runtime through what we call 'operations'.

### How to use Operations

Any action on the terrain (like digging, adding voxels, etc.) is performed _via_ **operations**. You cannot edit the terrain in any other manner. Operations are the unique entry point for editing a terrain once it has been generated. Even the Ultimate Terrain Editor uses operations to alter the terrain.

Ultimate Terrains comes with these common and most useful operations:

*   dig/add a cube
*   dig/add a sphere
*   flatten with rectangular brush
*   flatten with spherical brush

You can retrieve all these operations in the Ultimate Terrains Editor's inspector. By the way, you will be able to use any custom operation from the Editor too, because it scans your project and finds all scripts that implement IOperation interface. These is one of the powerful feature of the Editor.

Anyway, the point here is to see how to edit the terrain (ie. use operations) from your scripts. For example, you could make a script that dig the terrain spherically when the player shots with a super-laser gun! Doing such a thing is actually extremely easy: you just have to use the _OperationsManager_:

<pre class="prettyprint">IOperation operation = new DigSphere(position, radius, voxelType);
    if (terrain.OperationsManager.IsReadyToComputeAsync) {
        terrain.OperationsManager.Add(operation).PerformAll(true);
    }
    </pre>

Notice that we first create a new instance of the DigSphere operation with some parameters like the position (where we are going to dig), the radius (size of the sphere we dig) and the voxelType that will replace existing voxels (for example, a voxel type with an underground rock texture).  
Then, we add the operation to the list of _pending operations_ of the Operation Manager. Finally, we call _PerformAll_ method to perform all pending operations. The boolean parameter of _PerformAll_ method determines if the operations should be done asynchronously or not. Here, we pass the boolean value 'true' to the method, meaning operation will be done asynchronously.

The good point of doing it this way is that we are able to perform **several operations at the same time** and potentially **a lot faster** than if we performed operations one by one.  
For example, if you'd like to dig a sphere and add a cube at "same time" you would do it this way:

<pre class="prettyprint">IOperation operation1 = new DigSphere(position1, radius, voxelType1);
    IOperation operation2 = new AddCube(position2, size, voxelType2);
    if (terrain.OperationsManager.IsReadyToComputeAsync) {
        terrain.OperationsManager.Add(operation1).Add(operation2).PerformAll(true);
    }
    </pre>

or (which is strictly equivalent):

<pre class="prettyprint">terrain.OperationsManager.Add(new DigSphere(position1, radius, voxelType1));
    terrain.OperationsManager.Add(new AddCube(position2, size, voxelType2));
    if (terrain.OperationsManager.IsReadyToComputeAsync) {
        terrain.OperationsManager.PerformAll(true);
    }
    </pre>

One more word about synchronous vs. asynchronous operations:

*   If you decide to perform operations synchronously (passing _false_ to _PerformAll_ method) then they will all be done in one frame.  
    This is a good thing when you are in the editor, but this is not ideal at runtime as it can cause lag.
*   If you decide to perform operations asynchronously (passing _true_ to _PerformAll_ method) then you cannot be sure they will all be done in one frame, but you can be sure they won't add lag, making it ideal for runtime editing. **When you are performing operations asynchronously, it is very important to check if the state of the Operation Manager allows you to do that thanks to the boolean _terrain.OperationsManager.IsReadyToComputeAsync_.**

Now that you know how to use operations in your scripts, let see how to create your own custom operations.

### Implement your own Operations

We've seen how operations can be used to edit the terrain, it's time to see how to create our own custom operations.

Some basic-but-very-useful operations are already included in uTerrains (in the Presets folder) such as dig/add/paint cube, sphere and cylinder, but you may want to create an operation that add a custom shape like an arch, a building, a giant mushroom or whatever you want. In order to do this, you will have to create a new operation.

**Programming skills are needed to achieve this.** You do not need to be a C# expert, but at least you have to be able to create a class that implements an interface. If you have no idea of what is an [interface](http://msdn.microsoft.com/en-us/library/87d83y5b.aspx "C# interface"), we recommend to search over the Internet, there are plenty of tutorials that explain it well.

Creating a new operation is both easy and hard to do at the same time:

*   easy because everything has been made to hide to complexity (operations are actually a way to implement the [_visitor pattern_](http://en.wikipedia.org/wiki/Visitor_pattern "Visitor pattern")).
*   hard because if you do not pay attention of what your are doing you can quickly create an operation that will have horrible impacts on performance. Be careful when you write the script of your operation.

To create an operation, you must:

1.  Create a class that implements IOperation interface.
2.  Create a class that implements IOperationEditor interface. You must put it in _Editor_ folder, otherwise your project won't build anymore.

Ultimate Terrains Editor will automatically add your new operation to the list of available operations, so you will be able to use it from the Editor.

To see how to implement IOperation interface and IOperationEditor, get a look at DigCube.cs and DigCubeEditor.cs in the _Presets_ folder. Those are good examples.




## Terrain generation / Biomes

Biomes are at the heart of terrain generation. A biome is a set of generators and combiners (see below) that is in charge of producing voxel values (output) at asked positions (input). A single terrain can have many biomes, allowing to generate completely different kind of ground & shapes on a single terrain. A typical example of it could be a "above water" biome that generates hills and valleys and an "underwater biome" that generates underwater ground with cliffs, submarine caves or whatever. There can be only one active biome at a given world position. Ultimate Terrains knows which biome to ask for voxel value at some position thanks to the **Biome Selector**.

### Biome Selector

The role of the biome selector is simple: it tells what biome must be used for a given world position. It "selects" the right biome for the right place. There is one, and only one biome selector in a terrain.

To be clear, the workflow of the generation of a voxel is at a given 3D world position is:  
3D position -> biome selector -> biome 'A' is selected -> ask biome 'A' to generate voxel value

#### The UniqueBiomeSelector

Obviously, the most simple biome selector is the _UniqueBiomeSelector_ which always select the same biome. This is the default biome selector and this is the one that should be used when your terrain is made out of a single biome.

To give you an idea of how a biome selector is implemented (you can implement your own biome selectors) here is the code of the UniqueBiomeSelector:

<pre class="prettyprint">public class UniqueBiomeSelector : IBiomeSelector
    {
        /// 
        public short GetBiomeId (float x, float y, float z, float[] values2D)
        {
            return 0;
        }
    }
    </pre>

It returns the ID of the biome that must be used at position (x,y,z) which is always 0 in the UniqueBiomeSelector.

#### The AboveAndBelowBiomeSelector

Ultimate Terrains comes with another biome selector, the AboveAndBelowBiomeSelector, which selects biomes depending on altitude (y coordinate). It is more interesting than the UniqueBiomeSelector as it actually choose between two biomes, but it remains very simple.

Here is its code:

<pre class="prettyprint">public class AboveAndBelowBiomeSelector : IBiomeSelector
    {
        float yCoordinate;
        short aboveBiomeId;
        short belowBiomeId;

        public AboveAndBelowBiomeSelector(float yCoordinate, short aboveBiomeId, short belowBiomeId)
        {
            this.yCoordinate = yCoordinate;
            this.aboveBiomeId = aboveBiomeId;
            this.belowBiomeId = belowBiomeId;
        }

        /// 
        public short GetBiomeId (float x, float y, float z, float[] values2D)
        {
            return y < yCoordinate ? belowBiomeId : aboveBiomeId;
        }
    }
    </pre>

It has two biomes ID (one for the "above" and one for the "below") and an altitude (yCoordinate) from which the biomes are choosen.  
As you see, if the world position is below the yCoordinate, then it returns the ID of the "below" biome, otherwise it returns the ID of the "above" biome.

You should try to use this biome selector on your terrain. Go in the "Biomes" tab of the terrain inspector and change the Biome Selector script from "UniqueBiomeSelectorSerializable" to "AboveAndBelowBiomeSelectorSerializable". This will display a few more fields in the inspector allowing you to define yCoordinate, aboveBiomeId and belowBiomeId. At this point, there may be some error if you press Play because you defined only one biome on your terrain. Just create a second biome (like you did for the first one in the Getting Started section) and put different values for frenquency. Once it is done, press Play and see the result.

#### Implementing your own Biome Selector

It's quite easy to implement your own biome selector. All you need is to create a script that implements IBiomeSelector interface, and a script that extends SerializableBiomeSelector for the editor GUI.

The IBiomeSelector interface defines only one method with signature

<pre class="prettyprint">short GetBiomeId(float x, float y, float z, float[] values2D)</pre>

To put it simply, it must return the ID of the biome that must be used at position (x,y,z). It also provides 2D values (we'll see later what it is exactly) that can be used to select a biome. For example, these 2D values could allow you to select the biome depending on the value of some 2D Perlin noise generator.

The best is to give an example. Get a look at AboveAndBelowBiomeSelector.cs and AboveAndBelowBiomeSelectorSerializable.cs to see how it is implemented.

For your convenience, here is the content of these files:

<pre class="prettyprint">public class AboveAndBelowBiomeSelector : IBiomeSelector
    {
        float yCoordinate;
        short aboveBiomeId;
        short belowBiomeId;

        public AboveAndBelowBiomeSelector(float yCoordinate, short aboveBiomeId, short belowBiomeId)
        {
            this.yCoordinate = yCoordinate;
            this.aboveBiomeId = aboveBiomeId;
            this.belowBiomeId = belowBiomeId;
        }

        /// 
        public short GetBiomeId (float x, float y, float z, float[] values2D)
        {
            return y < yCoordinate ? belowBiomeId : aboveBiomeId;
        }
    }
    </pre>

And for the editor GUI:

<pre class="prettyprint">[Serializable]
    public class AboveAndBelowBiomeSelectorSerializable : SerializableBiomeSelector
    {
        [SerializeField]
        float
            yCoordinate;
        [SerializeField]
        int
            aboveBiomeId;
        [SerializeField]
        int
            belowBiomeId;

        public override void OnGUI ()
        {
            #if UNITY_EDITOR
            EditorGUILayout.LabelField ("Select a biome or another depending on height.");
            yCoordinate = EditorGUILayout.FloatField ("Y coordinate:", yCoordinate);
            aboveBiomeId = EditorGUILayout.IntField ("Id of biome above:", aboveBiomeId);
            belowBiomeId = EditorGUILayout.IntField ("Id of biome below:", belowBiomeId);
            #endif
        }

        public override IBiomeSelector CreateModule (UltimateTerrain uTerrain)
        {
            return new AboveAndBelowBiomeSelector (yCoordinate, (short)aboveBiomeId, (short)belowBiomeId);
        }
    }
    </pre>

### Biomes

A biome is a **set of generators and combiner** that is **in charge of generating voxels**. Basically, when Ultimate Terrains generates a terrain, for each (needed) 3D world position in the space, it generates a voxel. Then it will generate the surface of the terrain from all voxels thanks to the dual contouring algorithm.

To sum up, biome selector chooses which biome to use, then voxels are generated through the _generation flow_ defined in the biome, and finally surface (ie. polygons) will be created from them.

Remember a voxel has a value (which basically corresponds to the closest distance between the voxel and the surface) and a type (that will be used to determine the vertices colors, if there should be grass, or trees, etc.). Consequently, to generate a voxel, the biome must both generate a value and choose a voxel type. Let's see how it does.

#### The generation flow

A biome has a some 2D value generators, a 2D master, some 3D value generators, a 3D master and a final combiner. This looks like a lot to learn, but it's actually not that difficult and fortunately, the biome editor's GUI displays all of those components in a flow chart, making it a lot easier to understand.

Here is how a biome looks like in the editor:

![Biome configuration](https://uterrains.com/wp-content/uploads/2018/08/biome_conf-e1533893725668.png)

As you see, the flow chart shows the entire process of generating a voxel, starting from a 2D (top-down) world position and a 3D world position, to go through all generators and through the final combiner, to finally get a voxel as a result. This is what we call the _generation flow_.

Let's see each component in details.

##### 2D Master

2D Master is in charge of calling all wanted 2D value generators for a given top-down world position. Most of the time, you won't need to implement your own and you will just use the default 2DMaster implementation which simply calls all 2D value generators.

In some situations, it may be benefic to implement your own 2D Master in order to call only 2D generators that will trully be needed at a given position. This can improve performance, but you should not care about this unless you are an advanced Ultimate Terrains user.

##### 3D Master

This is the same as 2D Master but for 3D value generators.

##### 2D value generators

2D value generators take a top-down world position as input, and returns a float value.

**They are common to all biomes** meaning that if you change 2D generators in a biome, it will affect all other biomes. This is done this way for performance reasons, and also to allow the biome selector to use 2D generated values.

Here is an example of Perlin2DGenerator:

<pre class="prettyprint">public class Perlin2DGenerator : I2DGenerator
    {
        float frequency;
        float scale;
        ImprovedPerlin perlin;

        public Perlin2DGenerator(float frequency, float scale, int seed, NoiseQuality quality)
        {
            this.frequency = frequency;
            this.scale = scale;
            perlin = new ImprovedPerlin(seed, quality); // <- from LibNoise library
        }

        /// 
        public float GetValue(float x, float z)
        {
            return perlin.GetValue(x * frequency, z * frequency) * scale;
        }
    }
    </pre>

The important part in this code is the function that actually generates the value:

<pre class="prettyprint">public float GetValue(float x, float z)
    {
        return perlin.GetValue(x * frequency, z * frequency) * scale; // <- perlin is provided by LibNoise
    }
    </pre>

To create your own 2D generator, you will have to create a class that implements the I2DGenerator interface (just like in the example above) as well as a class that extends Serializable2DGenerator for the GUI. Get a look at /Assets/uTerrains/Scripts/Generators/2DValueGenerators folder to see a list of 2D generators that you can take as examples.

##### 3D value generators

3D value generators take a 3D world position (x,y,z) and 2D values generated at the equivalent top-down position (x,z) as input, and returns a float value. Here is an example of Perlin3DGenerator:

<pre class="prettyprint">public class Perlin3DGenerator : I3DGenerator
    {
        float frequency;
        ImprovedPerlin perlin;

        public Perlin3DGenerator(float frequency, int seed, NoiseQuality quality)
        {
            this.frequency = frequency;
            perlin = new ImprovedPerlin(seed, quality); // <- from LibNoise library
        }

        /// 
        public float GetValue(float x, float y, float z, float[] values2D)
        {
            return perlin.GetValue(x * frequency, y * frequency, z * frequency);
        }
    }
    </pre>

The important part in this code is the function that actually generates the value:

<pre class="prettyprint">public float GetValue(float x, float y, float z, float[] values2D)
    {
        return perlin.GetValue(x * frequency, y * frequency, z * frequency); // <- perlin is provided by LibNoise
    }
    </pre>

To create your own 3D generator, you will have to create a class that implements the I3DGenerator interface (just like in the example above) as well as a class that extends Serializable3DGenerator for the GUI. Get a look at /Assets/uTerrains/Scripts/Generators/3DValueGenerators folder to see a list of 3D generators that you can take as examples.

##### Final Combiner

The _final combiner_, is here to combine 2D and 3D values to compute the final voxel value, and choose its voxel type. There is one, and only one, final combiner per biome.

A final combiner must implement the _IFinalCombiner_ interface.

<pre class="prettyprint">public interface IFinalCombiner
    {
        ///
        /// Combines all 2D and 3D values computed at a given world position (in voxel units) and determines 
        /// the value and the type of the voxel at this position.
        ///</pre>

///The input coordinate on the x-axis. ///The input coordinate on the y-axis. ///The input coordinate on the z-axis. ///All 2D values that have been computed at this position. ///All 3D values that have been computed at this position. ///The final value of the voxel to be set. ///The final type of the voxel to be set. void Combine(float x, float y, float z, float[] values2D, float[] values3D, out float voxelValue, out VoxelType voxelType); }

As you see, the Combine method does not return anything. Instead, it uses [C# out parameters](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/out-parameter-modifier) so you have to assign a value to _voxelValue_ parameter and _voxelType_ parameter.

Here is a very basic example of a final combiner that just takes the first 3D value as-is, and uses always the same voxel type.

<pre class="prettyprint">public class LazyFinalCombiner : IFinalCombiner
    {
        VoxelType mainVoxelType;

        public LazyFinalCombiner(UltimateTerrain uTerrain, string voxelTypeName)
        {
            VoxelTypeSet voxelTypeSet = uTerrain.VoxelTypeSet;
            mainVoxelType = voxelTypeSet.GetVoxelType(voxelTypeName);
        }

        /// 
        public void Combine(float x, float y, float z, float[] values2D, float[] values3D, out float voxelValue, out VoxelType voxelType)
        {
            voxelValue = values3D[0];
            voxelType = mainVoxelType;
        }
    }
    </pre>

As always, there's also a class for the editor GUI:

<pre class="prettyprint">[Serializable]
    public class LazyFinalCombinerSerializable : SerializableFinalCombiner
    {
        [SerializeField] string voxelTypeName = "Some type";

        public override void OnGUI()
        {
    #if UNITY_EDITOR
            EditorGUILayout.LabelField("This combiner simply uses the first 3D value (ignoring the others) and uses the given voxel type.");
            voxelTypeName = EditorGUILayout.TextField("Voxel type name:", voxelTypeName);
    #endif
        }

        public override IFinalCombiner CreateModule(UltimateTerrain uTerrain)
        {
            uTerrain.VoxelTypeSet.AssertVoxelTypeExists(voxelTypeName);
            return new LazyFinalCombiner(uTerrain, voxelTypeName);
        }
    }
    </pre>

The final Combiner is the most important module of the generation flow. It is responsible for actually giving a value and a type to each voxel.  
Like 3D and 2D generators, it must be fast (it will be called million times) and naturally thread safe (it will be called from different threads). What is meant by "naturally thread safe" is that you should not use any _lock_ mechanism in it (for performance reason). It should be thread safe  
_by nature_.

If you get a result that looks blocky / not smooth enough (especially on big LODs), it's probably because voxel values are relatively too different between each others. Try to just divide the voxel values by some constant, typically 64\. This may solve your issue.




## Loading terrain changes

Operations (modifications) will be loaded automatically when the scene starts from these locations:

1.  <Application.persistentDataPath>/uTerrainsData/<runtime-data-path>/runtime_operations
2.  Assets/StreamingAssets/uTerrainsData/<terrain-data-path>/operations

The first directory contains operations persisted **at runtime**.  
The second directory contains only operations that have been done **at edit time** and that are included in the final package of your product.  
If a file is found in the first directory, it won't be loaded from the second one. In other words, the runtime-directory overrides the packaged-directory.

You can retrieve the actual runtime data path with:

<pre class="prettyprint">public class Example : MonoBehaviour
    {
        void Start()
        {
            var terrain = GetComponent();
            // THIS WILL NOT WORK IN AWAKE. ONLY IN START OR UPDATE.
            string path = terrain.OperationsManager.RuntimeDataPath;
        }
    }
    </pre>

You can change the runtime directory **before** the terrain gets loaded, like this:

<pre class="prettyprint">public class CustomRuntimePathSetter : MonoBehaviour
    {
        void Awake()
        {
            UltimateTerrain.OnBeforeLoad += ChangeRuntimeDataPath;
        }

        void ChangeRuntimeDataPath(UltimateTerrain terrain)
        {
            terrain.Params.RuntimeBasePath = "whatever you want";
        }
    }
    </pre>

## Saving terrain changes

Terrains configuration is entirely saved in the scene file. No need to care about that. However, terrain modifications (ie. Operations) must be saved separatly.

There are different ways to persist Operations.

### Saving at edit time

At edit time (ie. within Unity editor), the prefered way to save Operations is to call the _Persist_ method of _UltimateOperationsManager_.  
This method takes a boolean as parameter that indicates if you want to completely override all data when you save. In edit mode, you'll probably want to do that most of the time.

You can also specify a path (of a directory) where to write files. Unless you want to achieve something particular, you won't need this because it is a lot simpler to let Ultimate Terrains write data in the appropriate default folder (which is Assets/StreamingAssets/uTerrainsData/<terrain-data-path>/operations). See [Data Path](#global-settings-data-path) in Global Settings for more information.

This method should only be called at edit time (ie. not at runtime) because it writes files in the StreamingAssets folder by default, which is not writable at runtime.

### Saving at runtime

The prefered way to persist data at runtime is the _PersistModifiedRegions_ method of _UltimateOperationsManager_.

It will automatically save all regions that have been modified since last save. Once the method returns, you can be sure modifications have been saved to disk in the directory at RuntimeDataPath.

This method is not suitable for realtime saving as it may be too slow.

#### Saving at runtime, in realtime

The prefered way to persist data in realtime (ie. when the player is actually playing) is the _PersistModifiedRegionsAsync_ method of _UltimateOperationsManager_.

It is the same as _PersistModifiedRegions_ except all processing will be done asynchronously in a background thread, so it won't make your game lag. However, you cannot be sure of when saving is done, so it is always a good idea to call _PersistModifiedRegions_ before the game exits.

### 100% custom saving & loading

You can implement your own way to save and load Operations if you think the other methods don't fit your needs.

You can just serialize operations and write them to the disk as you wish.  
To load operations, you'll have to read your files, deserialize it, and then add operations back to the terrain with _terrain.OperationsManager.Add(operation)_.

If you implement your own loader, you will have to load needed operations before the terrain gets generated.  
You can do this thanks to _OnBeforeLoad_ event and _terrain.OperationsManager.AddBeforeLoad_ method, as shown below:

<pre class="prettyprint">public class CustomOperationLoader : MonoBehaviour
    {
        void Awake()
        {
            UltimateTerrain.OnBeforeLoad += LoadOperationsFromServer;
        }

        void LoadOperationsFromServer(UltimateTerrain terrain)
        {
            List operations = LoadOperations(); // <- this is YOUR code
            foreach (var op in operations) {
                terrain.OperationsManager.AddBeforeLoad(op);
            }
        }
    }
    </pre>

## Synchronizing terrain modifications in a multiplayer game

To synchronize changes made on a terrain by a player, you have to:

1.  Each time a player performs an operation, serialize it.
2.  Send it to all other players through the network.
3.  On each player that receive the serialized operation, deserialize it and perform it locally.

Here is an example of pseudo-code showing how it might look like:

<pre class="prettyprint">public class Multiplayer : MonoBehaviour
    {
        UltimateTerrain terrain;

        // Use this for initialization
        void Start()
        {
            terrain = GetComponent();
        }

        // Update is called once per frame
        void Update()
        {
            if (player wants to dig a sphere) {
                var operation = new DigSphere(terrain, position, radius);
                terrain.OperationsManager.Add(operation).PerformAll(true);

                // This should be done in a thread:
                string serializedOperation = terrain.OperationsManager.SerializeOperation(operation);
                network.SendToAllOtherPlayers(serializedOperation); // <- this is YOUR code. Ultimate Terrains does NOT handle network for you.
            }
        }

        void OnReceivingOperationFromNetwork(string serializedOperation)
        {
            var operation = terrain.OperationsManager.DeserializeOperation(serializedOperation);
            terrain.OperationsManager.Add(operation).PerformAll(true);
        }
    }
    </pre>

### Handling an online peristent world

To handle persistent worlds, you will have to persist operations by yourself on your servers (probably in some database). This part is not covered in this documentation.

You will also have to load operations from the server before terrain is generated. You can do this by implementing a _BeforeLoadEventHandler_ and registering it with _terrain.OnBeforeLoad += yourHandler;_ in an _Awake()_ method.

Here is an example of pseudo-code showing how it might look like:

<pre class="prettyprint">public class CustomOperationLoader : MonoBehaviour
    {
        void Awake()
        {
            UltimateTerrain.OnBeforeLoad += LoadOperationsFromServer;
        }

        void LoadOperationsFromServer(UltimateTerrain terrain)
        {
            List operations = GetOperationsFromServer(); // <- this is YOUR code. Ultimate Terrains does NOT handle network for you.
            foreach (var op in operations) {
                terrain.OperationsManager.AddBeforeLoad(op);
            }
        }
    }
    </pre>

## MegaSplat integration

MegaSplat is a famous package of shaders on the Asset Store that offers high quality shaders for terrains. It includes a mesh shader that is perfectly compatible with Ultimate Terrains.

First, go to uTerrain inspector, in Voxel Types tab, and add or replace the terrain material with MegaSplat mesh material. Then, change the voxel-type-functions script of **all** your voxel types to "MegaSplatVoxelTypeFunctions". This displays a GUI which allows you to select textures and adjust some other parameters related to MegaSplat.

Finally, open the MegaSplat material inspector (just click on the material from Unity project view) and make sure to select "Triplanar" for Splat UV Mode and "World" for Space (just below).

That should be enough!

## Relief Terrain Pack (RTP3) integration

Relief Terrain Pack v3 (aka RTP3) is a famous package of shaders on the Asset Store that offers high quality shaders for terrains. It includes a triplanar shader that is perfectly compatible with Ultimate Terrains.

Before using it, edit the file **ReliefTerrainPMTriplanarStandalone.shader** in ReliefPack/Shaders/ReliefTerrain/VertexControl in a text editor and comment the line **#define LOCAL_SPACE_UV** and the line **#define WNORMAL_COVERAGE_X_Z_Ypos_Yneg** (add "//" at the beginning of the line). Save it. The shader is now ready to be used with uTerrains.

Then, drag & drop ReliefTerrainVertexBlendTriplanar material (you will find it in the same folder than the shader) to the material field of your terrain (or you can add a new material if you want as uTerrains supports multiple materials).

Finally, be careful with your vertex colors: RTP uses colors differently than the shader that is included with uTerrains. First texture maps with red color (255, 0, 0, 0), second texture maps with green (0, 255, 0, 0), third texture maps with blue (0, 0, 255, 0) and fourth texture maps with alpha (0, 0, 0, 255). If needed, adjust the vertex color of your voxel types and you're done with RTP integration.

</div>