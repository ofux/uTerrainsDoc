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
