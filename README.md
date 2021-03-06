# Jython console plugin for Bukkit

By Seppe "Macuyiko" vanden Broucke

`minecraft-bukkit-console` is a Minecraft Bukkit plugin which provides server administrators with a python interpreter console (either locally though a GUI or remotely with an interpreter server) which can be used to administer running servers using the full arsenal provided by the Bukkit API. You can watch a [Youtube](http://www.youtube.com/watch?v=rI3PfgCSI7Y) video showing off some of the possibilities.

The implementation is based on Jython. This has the benefit that the whole Bukkit API can be utilized at runtime, without having to add commands to the Bukkit plugin itself.

On top of that, the console also provides a fun way to learn Python together with Minecraft. Students can see the results of their code immediately reflected in their Minecraft world.

The code is composed out of the following items. I assume you have CraftBukkit already running as a server.

* `BukkitConsole`: the Eclipse Java project. You don't need this if you wish to get up and running as soon as possible.
* `python`: contains the Jython Python interpreter console. This uses the excellent work by [Don Coleman](http://don.freeshell.org/jython/), with some minor changes to keep the autocomplete from raising exceptions. **Put this folder in your CraftBukkit installation directory, i.e. next to `plugins`.**
* `lib`: contains the Bukkit API and Jython libraries needed by the plugin. **Put this folder in your CraftBukkit installation directory, i.e. next to `plugins`.** (You might want to check if the libs are still up to date, though.)
* `jar`: contains the compiled plugin. **Put `bukkitconsole.jar` in the `plugins` folder of your CraftBukkit installation directory.**

Upon starting, the plugin will create a `config.yml` file in its `plugins` subdirectory where the following config parameters can be changed:

* `bukkitconsole.guiconsole.enabled [bool]`: start the GUI interpreter locally
* `bukkitconsole.serverconsole.enabled [bool]`: enable the remote interpreter server
* `bukkitconsole.serverconsole.password [string]`: interpreter server password
* `bukkitconsole.serverconsole.port [int]`: port to bind the interpreter server to
* `bukkitconsole.serverconsole.maxconnections [int]`: maximum number of simultaneous connections

Logging into the interpreter server can be done using telnet, e.g. `telnet 127.0.0.1 44444` you will be prompted for the password and an interpreter will be spawned after succesful authentication.

Both for the GUI based and server based interpreter, it's a good idea to execute `from org.bukkit import Bukkit` as your first command.

More information can be found on [this blog post](http://blog.macuyiko.com/post/2013/a-bukkit-jython-console-plugin-for-minecraft.html).
