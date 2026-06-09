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

You can also do .add_rpc_attachment("self_spawned", func(node) which makes it run on every players PC not only on the client.

IF U ARE WONDERING WHAT CODING LANGUAGE IS THAT ITS GD SCIPRT USED BY GODOT FOR ITS DEFAULT LANGUAGE.

# Adding assets ( textures, sounds )
To add assets you need to create a folder inside ur Mod folder named textures or sounds. WARNING ITS CASE SENSETIVE! Then put ur files in there. Every texture needs to be a png, jpg and sound a ogg file.
After u add it the modloader should load it for you.

# Adding nextbots
To add a next bot u need to create a variable that will be ur nextbot. Then u give the variable a value of type NextbotData by writing ModAPI.create_nextbot("YOUR NEXTBOT NAME", "YOUR TEXTURE NAME", "YOUR SOUND NAME").
If u dont have a name or a sound u can leave it blank but never leave the texture blank.
Now after you created ur Nextbot you need to register it by writing ModAPI.register_nextbot(YOUR NEXTBOT VARIABLE)

```
extends Node

func init() -> void:
	var nextbot = ModApi.create_nextbot("Kamala", "kamala", "")
	ModApi.register_nextbot(nextbot)

```

# Attachments and their arguments
attachment: "self_spawned" arguments: Your players node,
attachment: "player_died_spawned" arguments: Runs when a player dies

# METHODS OR VARIABLES THAT U SHOULD NEVER USE ( PROBABLY CAUSE THE MOD API USES THEM )
ModAPI.Nextbots,
ModAPI.register_texture,
ModAPI.register_sound
