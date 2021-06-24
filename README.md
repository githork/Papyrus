# Tuinity fork for Erethon
## Building Papyrus
### Requirements:

* You need git installed, with a configured user name and email. On Windows you need to run from git bash.
* You need maven installed.
* You need jdk 16+ installed to compile (and jre 16+ to run).
* Anything else that paper requires to build.

### Building:
* Clone this repo and run ``./gradlew applyPatches.`` - this will take a while!
* Use ``./gradlew paperclipJar`` to create paperclip


## Doing things
### Adding patches:
* Every commit is a patch.
* Modify Papyrus-Server or Papyrus-API with your changes-
* ``cd Papyrus-Server`` or ``Papyrus-API``, depending on what you modified.
* ``git add .`` if you added new files
* ``git commit`` & enter the patch message. "save" (Ctrl+O if using nano)
* Run ``./gradlew rebuildPatches`` to create a patch from the commit
* (Test your changes by creating a paperclip jar or by using ``./gradlew runDev`` to start a server)

### Modifying patches:
* (Stash your changes using ``git stash``)
* ``git rebase -i origin/master`` // Todo: This isn't ideal.
* Replace ``pick`` with ``edit`` for the commit/patch you want to modify, and "save" (Ctrl+O if using nano) the changes. Only do this for one commit at a time!
* Make the changes you want to make.
* ``git add .``
* ``git commit --amend`` (you can modify the patch message here if you want)
* ``git rebase --continue``
* Run ``./gradlew rebuildPatches`` to rebuild all patches

### Formatting:
* All changes should be marked with a comment like ``// Papyrus - Do stuff`` and ``// Papyrus start`` / ``// Papyrus end`` for multi-line changes
* Keeping diff small makes future updates easier. 

### Adding more NMS files
Papyrus-Server only contains NMS files that are modified. To add new files:
* Add the artifact and package to ``build-data/dev-imports.txt``. e.g. ``minecraft net.minecraft.world.entity.ai.goal.AvoidEntityGoal``. You can use a tool like the [Mapping viewer](https://minidigger.github.io/MiniMappingViewer/#/mojang) to figure out the package.
* Run ``./gradlew rebuildPatches`` to rebuild all patcher
* Your new file(s) should appear

### Testing API
* Enter the API directory (``cd Papyrus-API)``
* Run ``./gradlew publishToMavenLocal``
* Use the API in your plugin (groupID``de.erethon.papyrus``, artifact ``papyrus``)
