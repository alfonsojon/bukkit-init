Init script for various Minecraft servers
=======================================
A init script that, apart form starting and stopping the server correctly, has many extra features
for running a vanilla Minecraft or Spigot server.

Features
--------

 * Utilization of a RAM disk for world data, which decreases lag when reading world chunks
 * Backup for worlds
 * Support for automated server management
 * Server updating and complete backup
 * Exclude files and directories from full backup by adding them to "exclude.list"

Requirements
------------
git, java, screen, rsync

Access server console
=====================

	screen -x minecraft

Exit the console
	
	Ctrl+A D

Setup
=====

1. Symlink the minecraft file to `/etc/init.d/minecraft`, set the required premissions and update rc.d.

		sudo ln -s ~/minecraft-init/minecraft /etc/init.d/minecraft
		chmod 755  ~/minecraft-init/minecraft
		sudo update-rc.d minecraft defaults

2. Edit the variables in `config.example` to your needs and rename it to `config` (leaving it in the same folder as the original minecraft script)

3. Move your worlds to the folder specified by `WORLDSTORAGE`

4. Edit crontab

	As the server user:
	
		crontab -e

	Add these lines:

		#m 	h 	dom	mon	dow	command
		02 	05 	*	*	*	/etc/init.d/minecraft backup
		55 	04 	*	*	*	/etc/init.d/minecraft log-roll
		*/30 	* 	*	*	*	/etc/init.d/minecraft to-disk


5. To load a world from ramdisk run:

		/etc/init.d/minecraft ramdisk WORLDNAME
	
	to disable ramdisk, run the same command again.


For more help with the script, run

	/etc/init.d/minecraft help

[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=Ahtenus&url=https://github.com/Ahtenus/minecraft-init&title=minecraft-init&language=en_GB&tags=github&category=software) 

Good stuff
==========
[Backup rotation script](https://github.com/adamfeuer/rotate-backups) good if you want some kind or rolling of the world backups.
