# Allowed types

The types that the synchronizer is compatible with are:  
- Any primitive types (`int`, `string`, `float`, `byte`, etc)  
- `GameObject` (must have a Photon View component)  
- Any component that derives from Photon.MonoBehaviour and is in a Game Object that has a Photon View component  
- `Vector3`, `Vector2` and `Quaternion`  
- `SyncList<>`: a custom List class that works with the ObjectSynchronizer to improve network bandwidth usage. Learn more about it [here](SyncList.md)  
- `List<>` or an array of any of the other types allowed here **(not recommended for network bandwidth usage issues, use SyncList for an optimized way of syncing lists)**

!!! note
    Take a look at [Supporting your own types](supporting-your-own-types.md) to know how you can have a custom class/struct work with the Object Synchronizer.
