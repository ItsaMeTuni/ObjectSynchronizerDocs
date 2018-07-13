# Getting started

# Setting up
1.	Add an Object Synchronizer component to your Game Object.
2.	Drag and drop the components you want to synchronize to the Synchronized Components list.
3.	Whenever you want to sync your GameObject call `gameObject.Sync()` on it.

# How it works
When you call `gameObject.Sync()` the Object Synchronizer will search for fields in the components that are marked with the `[Sync]` attribute. It will then check which ones have changed from the last sync call and send only the changed ones. 
You can force to send all fields using `gameObject.Sync(true)`.
You can also target a sync call to a specific player using `gameObject.Sync(photonPlayer)`.
