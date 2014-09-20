vagrant-meteor
==============

A VM to run Meteor apps (with different versions of Meteor!) on any OS without installation issues.

# NOT WORKING! :-(

> see: https://github.com/pedantic-git/vagrant-meteor-repro


Boot MongoDB using: ```
mongod --dbpath /home/vagrant/local/db --setParameter textSearchEnabled=true
```

Error:
```
Unexpected mongo exit code 100. Restarting.
Can't start Mongo server.
MongoDB had an unspecified uncaught exception.
This can be caused by MongoDB being unable to write to a local database.
Check that you have permissions to write to .meteor/local. MongoDB does
not support filesystems like NFS that do not allow file locking.
```
Looked at: http://stackoverflow.com/questions/21272446/error-with-mongo-starting-meteor


Error:
```
FATAL ERROR: Evacuation Allocation failed - process out of memory
Killed
```


https://github.com/meteor/meteor/issues/1337#issuecomment-47439995
