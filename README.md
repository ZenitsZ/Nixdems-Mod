# Nixdems-Mod Modding
Documentation for nixdems mod modding

# Mod Structure
To create a mod you need to go into "C:\Users\user\AppData\Roaming\Godot\app_userdata\Escape the plakal\mods" and then create a new folder with the mods name.
After that u will need to create a json named "mod.json" the content of the json should be:
[mod.json](https://github.com/user-attachments/files/28671146/mod.json)
```
{
	"name": "YOUR MODS NAME",
	"author": "THE AUTHOR"
}
```

After u created the json we can go into the next part.

# Basic scripting
You can create as many scripts in the root folder for ur mod as u want every of them will be run. It can help you with keeping the mod structure clean.

```
extends Node

func init() -> void:
	ModApi.add_attachment("self_spawned", func(node):
		node.max_speed = 35
		node.max_air_speed = 50
		)
```

First u need to reference the ModApi.
After that u make .add_attachment("self_spawned", func(node) which means: you attach a chunk of code to a attachment. Attachments are signals that run after smth happens for an example if u want to do something after your Player spawns u write "self_spawned" into the attachment and u create a function with func(node) the node is the player node aka character.
after that you run your code.

In this code u can see me setting the max players speed on the ground and the max players speed in the air.

IF U ARE WONDERING WHAT CODING LANGUAGE IS THAT ITS GD SCIPRT USED BY GODOT FOR ITS DEFAULT LANGUAGE.
