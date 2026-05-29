---
title: Viewing Ingame Content
layout: default
parent: Modding
---

# Prerequisites
Before you can start viewing gameobjects or other ingame stuff, you need to install a plugin called [UnityExplorer](https://github.com/sinai-dev/UnityExplorer).


# How to Install UnityExplorer
To install it, just download the correct file [UnityExplorer.BepInEx5.Mono.zip](https://github.com/sinai-dev/UnityExplorer/releases/download/4.9.0/UnityExplorer.BepInEx5.Mono.zip). Then, extract the zip and drop the plugins folder into the BepInEx folder. Now, just run the game. (You might also want to enable the console in the BepInEx settings, just open BepInEx/config/BepInEx.cfg and set Enabled to true)

# How to use UnityExplorer
You can toggle the UI for UnityExplorer using f7

On the left side is the hierarchy, it's basically identical to how it is in Unity with the exception of being able to choose a scene to load from in a dropdown at the top. The bottom of it also has the option to load a different scene, which is very useful for quickly getting to a scene (note that it does not load save data so it might be broken)

When you click on a gameobject in the hierarchy, it opens another "window" with the inspector for the object, this is again similar to Unity's inspector UI but you can access children of the gameobject in it too. Just click a component on the gameobject to access its properties.