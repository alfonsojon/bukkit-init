Init script for various Minecraft servers
=======================================
A init script that, apart form starting and stopping the server correctly, has many extra features
for running a vanilla Minecraft, Spigot, or Bukkit server.

Features
--------

 * Support for automated server management
 * Easy updates with Spigot BuildTools support
 * Easily download and install the latest build of Paper
 * Run multiple servers on one host with Bungeecord or Waterfall

Requirements
------------
git, java, screen

Note: This currently does not work with OpenJDK 9.0.

Access server console
=====================

	service minecraft console

Exit the console
	
	Screen:	CTRL+A D
	Byobu:	CTRL+A A D

Setup
=====

1. Symlink the minecraft file to `/etc/init.d/minecraft`, set the required premissions and update rc.d.

		sudo ln -s ~/minecraft-init/minecraft /etc/init.d/minecraft
		chmod 755  ~/minecraft-init/minecraft
		sudo update-rc.d minecraft defaults

2. Edit the variables in `config.example` to your needs and rename it to `config` (leaving it in the same folder as the original minecraft script)

For more help with the script, run

	/etc/init.d/minecraft help

Todo:
=====

1. Implement multi-user servers i.e. /opt/minecraft-init/data/user1/server1, /opt/minecraft-init/data/user2/server1, etc...
2. chown that directory to the respective user
3. Allow the user to use `service minecraft-init` for their server
