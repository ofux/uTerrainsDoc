# Common Concepts


## How Voxels Define Terrain



*   Every XYZ coordinate in the grid is assigned voxel type, and a positive or negative distance.
*   The voxel type determines what voxel art appears in this grid (at the surface or beneath it).
*   The distance determines if the location is outside or inside the terrain.
    *   Negative numbers are inside the terrain; positive are outside.
    *   The visible surface occurs wherever distance = 0, i.e. at whatever location interpolated between grid points where negative values cross over into positive values.


## Noise Functions, and Generating Heightfields from 2D noise



*   Noise functions generate a smooth progression of random values across a range from (usually) -1 to 1, or -2 to 2.
*   2D noise functions are great for generating heightmaps via the ToHeight node.
    *   To-Height generates a "column" at (X,Z) where:
        *   the surface (voxel-value = 0) is where Y= noise-value)
        *   everything above the surface is positive ("outside")
        *   Everything below the surfave is negative ("inside")
*   3D noise functions generate 3-dimensional structures of noise.
    *   This can create a weirdly undulating surface, where all noise values > 0 are void, and all < 0 are solid.
    *   By biasing the result (offsetting it so that there are more positive numbers than negative), you can create floating blobs/islands.
*   Layering multiple 2D and 3D noise functions are the main way to create complex, potentially natural-looking (or appealingly unnatural) terrains.


## Nodes and Dimensions



*   Notes at the "start" of a node-graph (those which take no inputs) can generate output for every 3D location in the world in different ways.
    *   Some nodes (such as "Fast Noise 3D" generate unique values for every 3D location in the grid.)
    *   Some nodes (such as "Fast Noise 2D") generate unique values for every X/Z location in the grid.
    *   Some nodes (such as "Position") generate unique values along one axis of the grids (i.e. a value that returns the X value of the current grid location).
    *   Some nodes are constants, returning the same value for all nodes.
*   All nodes output a single number, so once you move past these "starting" nodes, you're processing a single value for the current X/Y/Z grid location.


## Filter Mask and Intensity



*   Mask and Intensity are both multipliers, clamped to 0-1, that attenuate the output of the node.
*   Intensity if a constant multiplier, whereas the mask is a variable input.
*   If no input is attached to Mask, it defaults to 1 (i.e has no effect).
