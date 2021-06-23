# BYOF (Bring Your Own Fork)
Based off of Tuinity instead of Paper.
Uses Paperweight.

## Build Requirements

Requirements:
- You need `git` installed, with a configured user name and email. 
   On Windows you need to run from git bash.
- You need `maven` installed.
- You need `jdk` 16+ installed to compile (and `jre` 16+ to run).
- Anything else that `paper` requires to build.

## Building

To compile Byof, you need JDK 16 and an internet connection.

Clone this repo and run `./gradlew applyPatches`.

To get a full list of tasks, run `./gradlew tasks`.

## Mojang-mapped jar
Run `./gradlew shadowJar` from your terminal. You can find the compiled jar in the `Byof-Server/build/libs` directory.

## Reobfuscated Spigot-mapped jar
Run `./gradlew reobfJar` from your terminal. You can find the compiled jar in the `Byof-Server/build/libs` directory.

## Paperclip, reobfuscated Spigot-mapped jar
Run `./gradlew paperclipJar` from your terminal. You can find the compiled jar in the `build/libs` directory.

## Rebranding

Replace mentions of Byof with your preferred fork name in `settings.gradle.kts`, `build.gradle.kts` & `.gitignore`.
Set the right package group name in `gradle.properties`

After applying patches, git rebase in `<fork name>-Server`, edit "Build changes" and replace all mentions of Byof with your fork name. Replace `com.github.clrxbl.byof` in `Versioning.java` aswell.
