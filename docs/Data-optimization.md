# Data optimization

The ObjectSynchronizer optimizes the data it sends so it consumes the lowest amount of bandwidth possible. When you call Sync the ObjectSynchronizer makes a copy of your synced values, so it can compare them on the next Sync call. If the ObjectSynchronizer detects that a value hasn’t changed since the last Sync call, it won’t send this value because this would be a waste of bandwidth.  

Another optimization the ObjectSynchronizer has is not using Buffered RPCs. Instead, you must add this to your network manager:    

```c#
public override void OnPhotonPlayerConnected(PhotonPlayer newPlayer)
{
    base.OnPhotonPlayerConnected(newPlayer);
    ObjectSynchronizer.SyncHelper.SyncAllWithTarget(newPlayer);
}
```

This improves data usage (and connection time) on a player that is connecting to the server. Instead of receiving a lot of buffered RPCs it will receive only one containing all current values.
