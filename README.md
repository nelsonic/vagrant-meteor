vagrant-meteor
==============

A VM to run Meteor apps (with different versions of Meteor!) on any OS without installation issues.

# NOT WORKING! :-(

> see: https://github.com/pedantic-git/vagrant-meteor-repro


Boot MongoDB using:

```sh
mongod --dbpath /home/vagrant/local/db --setParameter textSearchEnabled=true
```

Error:
```sh
Unexpected mongo exit code 100. Restarting.
Can't start Mongo server.
MongoDB had an unspecified uncaught exception.
This can be caused by MongoDB being unable to write to a local database.
Check that you have permissions to write to .meteor/local. MongoDB does
not support filesystems like NFS that do not allow file locking.
```
Looked at: http://stackoverflow.com/questions/21272446/error-with-mongo-starting-meteor


Error:
```sh
FATAL ERROR: Evacuation Allocation failed - process out of memory
Killed
```

Apparently Vagrant does not play well with Meteor... :poop:  <br />
see: https://github.com/meteor/meteor/issues/1337#issuecomment-47439995


I created a database in Mongo
and booted Meteor with:

```
MONGO_URL="mongodb://localhost:27017/meteor" meteor
```

It briefly booted...
But after a few seconds I got the following error:

```sh
FATAL ERROR: JS Allocation failed - process out of memory
Aborted (core dumped)
```

Tried it again, just to confirm I wasn't going crazy.
Second time got:

```
=> Starting your app...
/root/.meteor/packages/meteor-tool/.1.0.33.k69mx++os.linux.x86_64+web.browser+web.cordova/meteor-tool-os.linux.x86_64/dev_bundle/lib/node_modules/fibers/future.js:173
						throw(ex);
						      ^
Error: ENOTEMPTY, directory not empty '/vagrant/leaderboard/.meteor/local/build-garbage-186xwdx/programs'
    at Object.fs.rmdirSync (fs.js:617:18)
    at Object.files.rm_recursive (/root/.meteor/packages/meteor-tool/.1.0.33.k69mx++os.linux.x86_64+web.browser+web.cordova/meteor-tool-os.linux.x86_64/tools/files.js:238:8)
    at /root/.meteor/packages/meteor-tool/.1.0.33.k69mx++os.linux.x86_64+web.browser+web.cordova/meteor-tool-os.linux.x86_64/tools/files.js:236:13
```

OMG! Meteor is buggy! :cry:

Back to the drawing board.
