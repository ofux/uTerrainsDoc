# Installation

## Download Ultimate Terrains

Welcome to the community of uTerrains users! :)

You can download Ultimate Terrains through the [Asset Store](https://www.assetstore.unity3d.com/en/#!/content/31100). 

If you are still hesitating, you can try the [online demo](https://uterrains.com/demo/), get a look at the [official Ultimate Terrains thread on Unity's forum](https://forum.unity.com/threads/uterrains-ultimate-terrains-voxel-terrain-engine.383959/) or ask for details on the [official Discord server](https://discord.gg/tzrBuyY).


## Installation instructions

Installing Ultimate Terrains is a very simple process.

### Unity 5.6 or 2017.x
Ultimate Terrains is fully compatible with Unity 5.6.x and Unity 2017.x, however it is **strongly recommended** to use Unity 2018 as **it will run approximately 2 times faster with it**. So if you *can* update your Unity version, **do it**!

However, if you do need to keep using an older version of Unity:

1. Download and import Ultimate Terrains into your project like any other asset. All files are mandatory so please import everything.
2. You may need to restart Unity in order complete the installation and see the uTerrains menu appear under *Tools > uTerrains*.

That's all!


### Unity 2018.x newer
It is highly recommended that you use Unity 2018 or newer in order to get the most out of Ultimate Terrains. The performance increases for Ultimate Terrains between 2017 and 2018 are massive.

Installation is still very simple; it just requires one simple configuration change in your project settings (highly recommended, but not mandatory).

1. **Before importing Ultimate Terrains into your project**, set the *Scripting Runtime Version* and *API Compatibility Level* to *.NET 4.x Equivalent* in *Player Settings.
  * In Unity, open Player Settings: *Edit > Project Settings > Player*.
  * In the Player Settings window, under the *Other Settings* rollout, below the *Configuration* heading, set *Scripting Runtime Version* to *.NET 4.x Equivalent*.
  * Unity will probably tell you that it needs to restart. Select Restart.
  * Navigate back to the same place in Player Settings and make sure *Api Compatibility Level* is also set to *.NET 4.x*.
2. Once this is done, download and import Ultimate Terrains into your project like any other asset. All files are mandatory, so please import everything.
3. You may need to restart Unity once more in order complete the installation and see the uTerrains menu appear under *Tools > uTerrains*. Otherwise, that's it!

### Errors After Installation
At this point, uTerrains should be working correctly, but if you are seeing errors please try to re-import Ultimate Terrains in a blank project to see if the problem comes from a conflict with other scripts, packages, or settings in your main project.

You shouldn't get any conflict with other assets, but if you do please [let us know](https://uterrains.com/report/).

In particular, if you are updating an existing project, you should remove the old uTerrains folder before importing the new version. **IMPORTANT: be sure to CREATE BACKUPS of your own scripts before you do so** so that you can re-import them afterwards!