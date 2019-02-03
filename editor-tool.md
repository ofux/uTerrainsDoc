# Editor tool

The editor tool allows to edit the terrain directly within the scene view as you would do with a standard Unity terrain.

It generates the terrain in the editor and temporarly replaces the player object of the terrain by the scene view camera, so the terrain is built around the scene view camera.

To begin, click on 'Start editing' and wait for the terrain to be generated. Then, you can select an operation (like Dig Sphere, etc.), change its parameters (like radius, etc.), and apply it by clicking on the terrain directly in the scene view.

Once you're done, you can click on 'Stop editing' (the terrain will still be visible in the scene view but won't be updated as the scene view camera moves) or on 'Clear' (the terrain will be destroyed and removed from the scene but all your modifications will be saved, don't worry).