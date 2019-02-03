# Global Settings

The tab 'Global Settings' contains a lot of very important parameters that control terrain size, quality, speed and more. Let's see what they do one by one.

## Infinite terrain

The first parameter is quite simple: is your terrain finite, or infinite? Finite terrains don't have specific advantages except that in a finite terrain, chunks are never destroyed to follow the player. Depending on what you want to achieve, this may be more suitable and save a bit of computation time by increasing the chance of using cached data.

## Chunk connection mode

This setting controls how chunks of different LODs should connect to each other.

Properly connected seams creates perfect transitions but requires to compute each chunk several times (to generate LOD transition versions).  
Skirts just adds some triangles to chunk meshes in order to make holes invisible. It is very cheap to compute, but it creates ugly artifacts.  
The third choice you have is to chose both of connection modes. This is heavier in computation time, but it is the safest way to avoid any possible visible hole between chunks of different LODs.

## Duplicate vertices

If enabled, Ultimate Terrains will duplicate each vertex so you can avoid texture stretching. This is more useful for cubical terrains.

## Compute tangents

If enabled, Ultimate Terrains will compute tangents for you. This is needed by some shaders (disable it if your shader doesn't need it).

## Acceptable geometric error

These settings are extremely important. The geometric error is related to the terrain quality. The lower it is, the better your terrain will look, but with a higher performance cost. If it's too low, the terrain will take too much time to get generated. If it's too high, your terrain may look ugly and even have holes!

Indeed, if the acceptable geometric error is too high, terrain generation could miss some voxels which you really want to avoid. There is no geomteric error value that works all the time: it really depends on your terrain (ie. biomes settings).

Max error multiplier on surface allows you to increase (or decrease) the acceptable geomteric error when surface has been detected. This is quite useful because you can lower a bit terrain quality (and save CPU) without the risk to miss voxels.

Max error multiplier on chunk borders allows you to ensure chunk borders are properly computed by decreasing the acceptable error on borders. This can avoid potential and unwanted terrain holes.

## Distance to be near the surface

This is the distance at which Ultimate Terrains should consider a voxel is really close to the surface and should make a special effort to ensure the surface won't be missed.

## Draw size (ie. build distance)

Draw size and vertical draw size are the number of chunks of highest LOD to generate around the user. For example, if you set the draw size (and vertical draw size) to 4, Ultimate Terrains will build 4 chunks in the front, the back, the right, the left, the bottom and the top of the player (so, 8x8x8=512 chunks).  
So, for example, if the highest LOD is 7, the size of a chunk in Unity's unit will be 1024x1024x1024, and consequently the size of the visible part of the terrain will be 8192x8192x8192.

## Level Of Details count

This defines the highest LOD to compute on the terrain. Each time you increase this by 1, you double the size of the terrain.

## Distance from LODs to each other

The next parameters allow to set how many chunks of a particular LOD you want to be generate before the next LOD starts. Generally, you want it to stay small in order to improve performance. Change it only if you want higher quality at higher distance.

## Initial chunk count per LOD

The following parameters simply allows to create some chunks at the very begining of the game and put them in a pool to avoid creating them at runtime (making possible lags).

## Max LOD with...

As you can guess, these parameters controls which LODs should have cache, colliders and so on. Keep these parameters as low as you can to improve performance. A special word for 'Max LOD with cache': when cache is enabled on a chunk, it will be faster to recompute in case an operation (like digging) is done on it. However, it consumes a lot of memory, so keep it low.

## Data path

This parameter is very important as it tells where terrain data (ie. operations) is stored on the filesystem. It must be a subfolder of StreamingAssets/uTerrainsData (you have no choice on this part) to ensure it will be included in your final build.

## Size of a voxel in Unity's world

This one is self-explainatory. This is the size of one voxel.

## Thread count

You can increase of decrease the number of threads dedicated to chunks generation. You should keep it under 3 unless you are sure the target CPU has more than 4 cores.

## Player object

This is the object around which the terrain will be generated. This is generally the main camera.

## Max time spent in post-building per frame

Post-building consists in applying computed mesh to a chunk object. It updates the mesh filter, the mesh collider (is any) and a few other things that can only be done on the main thread (Unity restriction). Post-building is very fast thanks to Ultimate Terrains that pre-compute almost everything in background threads, but if too many chunks get post-builded in a single frame, this would create lag.

To avoid this, you can setup the maximum time that must be spent in post-building per frame. For the same purpose, you can also limit the count of chunks to be post-builded in a single frame.

Keeping a max time spent / frame below 10ms should prevent FPS from droping under 60.

## Layers

You have to create a specific layer for chunks and select it in the 'Chunk layer' dropdown. This is mandatory.

You can also optionaly create a specific layer for grass.