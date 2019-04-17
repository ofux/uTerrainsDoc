# Ultimate Terrains documentation


## Download and install

See [installation](installation.md) page for details.

## Getting started

Before starting, just a word to say that you can get more explanation about almost any parameter in Ultimate Terrains just by hovering it (wait 2s and it will display help). This is very useful to get more information about a field without having to go to the documentation all the time.

### Example scenes

If you want to see directly what kind of things Ultimate Terrains can do, you can open the provided example scenes (in the folder Assets/uTerrains/Scenes) and just press 'Play'.  
You can use these scenes to get an idea of how to setup a terrain, but I strongly recommend that you actually setup a scene from scratch by yourself so you will understand what's going on and what parameters stand for what.

### Overview in video

Get a look at our video tutorial (might not be as up-to-date as the written documentation) here: https://youtu.be/gpsxX0kHlHI

### Setup your terrain from scratch

See [this page](setup-from-scratch.md) page for a detailed, step-by-step tutorial that explains how to setup Ultimate Terrains in a new scene.

## Settings

- [Global Settings](global-settings.md)

## Node based editor

Ultimate Terrains let's you configure terrain generation through a node-based editor. This is highly flexible and powerful. A lot of built-in nodes are provided but you can implement your own ones easily.
- [Overview](node-based-editor.md)
- [Nodes reference](nodes.md)
- [Source code of all nodes](https://github.com/ofux/uTerrainsExtensions/tree/master/Nodes)

## Editor tool

The Editor tool allows to manipulate the terrain directly within Unity editor. See [this page](editor-tool.md) page for more information.

## Real-time editing

In Ultimate Terrains, real-time modifications are made through operations. See [this page](operations.md) page for more information.

Ultimate terrains provides many built-in operations but as for nodes, you can implement your own ones easily. See [here](https://github.com/ofux/uTerrainsExtensions/tree/master/Operations) to get a look at the source code of built-in operations.

## Saving, loading and sync over network

See [this page](save-load.md) page to see how to save, load and sync terrain data on disk or through the network.

## Third party assets integration

- [MegaSplat](megasplat.md)
- [RTP3](rtp3.md)
