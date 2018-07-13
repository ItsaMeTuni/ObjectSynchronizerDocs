# The SyncList<>

The `SyncList<>` is a type that derives from (and behaves like) a normal List. The difference is that it tracks every change you make to it (Add, Insert, Remove, etc) and when ObjectSynchronizer syncs it, instead of sending the entire List through the network it’ll only send the changes made to the List. This reduces (by a lot) network bandwidth usage when syncing big lists.  
You can use it just like `[Sync] SyncList<int> mySyncList;` and it’ll behave exactly like a normal list. You can call Add, Remove, etc methods on it like any normal list. You can cast to a normal List from it (since it derives from List). 

If you want to change the list without logging changes use `((List<int>)mySyncList).Add`, for example. To access the change log of the list use `mySyncList.changeLog`.  

A `SyncList<int>` will not appear on the inspector because Unity does not serialize generic types. If you want it to show up in the inspector use `IntSyncList`, which is just a wrapper class for `SyncList<int>` (other wrappers for other types available, like `StringSyncList`, `BoolSyncList`, etc). If you want to make a wrapper for a custom type of yours take a look at `IntSyncList` class and `IntSyncListPropertyDrawer`. Just copy those and adjust their names and types to your needs.  
