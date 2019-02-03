# Saving and loading

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
