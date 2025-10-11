---
title: Creating a Mod
layout: default
parent: Modding
---

# Creating a Mod

So, as you probably know if you're on this wiki I make a lot of Gelli Fields mods. It's pretty difficult to figure it all out on your own, so I've compiled a bunch of info to help anyone else make mods (though I doubt anyone will, sadly)

This page covers actually creating the modding environment, not coding it.

## Prerequisites

There are a few programs you need to install to begin modding. Firstly, I recommend installing [Visual Studio Code](https://code.visualstudio.com/download). It's what I use for modding and it's ideal for creating mods due to its simple interface. Visual Studio often has tons of extra features and bloat that aren't necessary for modding. For it to work well for C#, you need to install a few extensions, though.

Next, you'll want a program to look at the decompiled source of the game to see how it works. This is necessary to understand what a function does, what's needed to override it, and other useful stuff. [ILSpy](https://github.com/icsharpcode/ILSpy) is great for this, as DNSpy was discontinued and ILSpy has similar syntax highlighting to VSCode and is incredibly accurate to the source code.

The next thing needed is the .NET SDK, it's what actually compiles C# into runnable code. You can download the latest version [here](https://dotnet.microsoft.com/en-us/download).

Another thing needed obviously is BepInEx. It needs to be installed to the game to actually run your mod. You can find a guide to installing it here. Once you have it installed to the game, you need to install the pre-built packages for creating plugins. The simplest way is to run this command:

```batch
dotnet new install BepInEx.Templates::2.0.0-be.4 --nuget-source https://nuget.bepinex.dev/v3/index.json
```

Wow, there were a lot more prerequisites than I expected.

## Creating the Mod

Now that you have all of the prerequisites for making mods installed, we get to actually make it!

To actually create the mod, you can run this command to set it up. You can put the mod's name where it says "MyFirstPlugin". This will automatically create a new folder for you with all the needed stuff inside.

```batch
dotnet new bepinex5plugin -n MyFirstPlugin -T netstandard2.1 -U 2022.3.14
```

Alright, now that we have a plugin set up, we need to open it in Visual Studio Code. Open the folder, then in the file address bar type in "code .". This is a shortcut to open VSCode in the current location.

If you're making a mod, you probably want to access the base game's code. This is really simple, and it's done like adding any other dependency. In your mod's .csproj file, add

 ```html
<Reference Include="Assembly-CSharp">
    <HintPath>PathToAssemblyCSharp</HintPath
</Reference>
```

If you ever want to change the name of the mod, you can find the GUID and name in the .csproj file. The GUID should NOT be changed once the mod is released, think of it like a Minecraft mod-id. It should be a unique and constant name.

The version can also be changed in this file. It should preferably follow the [SemVer standard](https://semver.org/). (Though you don't have to follow it exactly, just understand what numbers need to be changed)

Once you have your mod ready to be built, you can run the command ``dotnet build`` to create a .dll file that can be loaded into the game. The file can be found in the ``bin/Debug/netstandard2.1`` folder and will have your mod's GUID as the name. Just put this file into your bepinex plugins folder, and you're done!

## Support for Other Mods

As you probably know, I've created some APIs and other useful utilities for Gelli Fields. If you want to support them, there are a few things you should do.

For the Mod Menu mod, all you need is an icon.png file next to your mod's dll. The mod will automatically load it and display it in-game!

If you want to use GFApi, there are a few steps needed. First, download the precompiled dll off of the [GitHub](https://github.com/bubbaboogs/GFApi). Then, install it as a mod as normal. Add this to your .csproj next to the Assembly-CSharp reference mentioned above.

```html
<Reference Include="GFApi">
    <HintPath>Libraries/GFApi.dll</HintPath>
</Reference>
```

You should then be able to access any of the game's classes now!
