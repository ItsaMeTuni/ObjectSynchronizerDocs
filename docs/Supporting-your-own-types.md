# Supporting your own types

## Serialization

To support a custom type (like a struct) you have to implement `ISerializable` and add the `[System.Serializable]` attribute to it. Check how `SyncInfo` was made for an example.
If you have a type you can’t modify the source of, create a class that implements `ISerializationSurrogate` and add the `[SyncSerializationSurrogate]` attribute to it. Check `Vector3SerializationSurrogate` for an example.


## Value preprocessing and postprocessing

Before serializing the values to send to the synchronization RPC, the ObjectSynchronizer applies what we call preprocessing, this allows us to send a different value over the network than the field value itself. This, for example, allows to send GameObject references over the network by sending its Network View ID.
Postprocessing methods are the same as preprocessing methods, but in reverse. The ObjectSynchronizer sends the value received from the RPC to the postprocessor, so we can turn an int (Photon View ID) to a GameObject reference.
You can do the same for any type you wish, you just have to create a static class with the `[SyncProcessingClass]` and add the preprocessing and postprocessing methods you wish in it. 
The methods have to have the following signatures, modifiers and attributes:

### Preprocessing
```c#
[SyncPreProcess(typeof(myType))]
public static object MyTypePreProcess(object _val)
```

### Postprocessing

```c#
[SyncPostProcess(typeof(myType))]
public static object MyTypePostProcess(object _val, System.Type _expectedType, object _currVal)
```
