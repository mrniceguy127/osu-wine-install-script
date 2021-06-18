# osu-wine-install-script

A complete re-write of my old distro-agnostic osu! wine installer (now on branch [old](https://github.com/mrniceguy127/osu-wine-install-script/tree/old)).

It:

- Installs osu!
- Installs the [wine-discord-ipc-bridge](https://github.com/0e4ef622/wine-discord-ipc-bridge)
- Installs [ThePoon's patched wine](https://blog.thepoon.fr/osuLinuxAudioLatency/) with a pre-compiled wine binary
- Generates a launch script to launch osu! with all of these patches
- Creates a desktop file to launch osu! with the generated launch script
- Automatically enables audio compatibility in osu! upon installation.

If you run into any problems with this, please open an issue!

# Requirements

- winetricks

# Instructions

1. `git clone https://github.com/mrniceguy127/osu-wine-install-script.git && cd osu-wine-install-script`
2. `./install-osu` Let osu! launch and close on its own. When osu launches to the main menu, close it. Even if it happens multiple times (extremely rare).
3. Follow the instructions under "Adjusting latency" [here](https://blog.thepoon.fr/osuLinuxAudioLatency/#adjusting-latency).
4. **IMPORTANT!!!** - Edit the script at `~/.local/bin/osu-wine` to adjust latency settings. You should set these values (see comments in file) as low as you can where osu!'s audio is still stable. These values vary by machine. If you don't do this, you will end up with severe audio instability or more latency than you could be getting. See [ThePoon's blog post](https://blog.thepoon.fr/osuLinuxAudioLatency/) on this.
5. Launch osu. You can either type `osu-wine` in a new terminal, or if you like GUI's, you can just search "osu" in whatever application launcher you might have. Use the command `osu-kill` to force kill osu!.

# Sources

- Pre-compiled wine binary with ThePoon's patch applied. You can find this on his [discord server](https://discord.com/invite/ThePooN) in one of the [pinned messages](https://discord.com/channels/209933203782369281/457310786994307073/700594232292802590). - [Link](https://5124.mywire.org/HDD/Downloads/wine-osu-4.13-1-x86_64.pkg.tar.xz)
- Official osu! branding icon - [Link](https://i.ppy.sh/916068c8e2d5f90be7766da5ce0ee7a7ea6c99b3/68747470733a2f2f6f73752e7070792e73682f68656c702f77696b692f4272616e645f6964656e746974795f67756964656c696e65732f696d672f75736167652d66756c6c2d636f6c6f75722e706e67)
- wine-discord-ipc-bridge - [Link](https://github.com/0e4ef622/wine-discord-ipc-bridge/releases/download/v0.0.1/winediscordipcbridge.exe)
- Official osu! installer - [Link](https://m1.ppy.sh/r/osu!install.exe)

# File listing

- WINEPREFIX: `~/.local/share/osu-wine/WINE.win32`
- osu! game files folder: `~/.local/share/osu-wine/osu`
- ThePoon's patched wine: `~/.local/share/osu-wine/wine-osu`
- wine-discord-ipc-bridge: `~/.local/share/osu-wine/wine-discord-ipc-bridge`
- osu! folder shortcut: `~/osu`
- osu! launch script: `~/.local/bin/osu-wine`
- osu! kill script: `~/.local/bin/osu-kill`
- osu! desktop file: `~/.local/share/applications/osu!.desktop`
- osu! logo file: `~/.local/share/icons/osulogo.png`

# Troubleshooting

- `osu-wine` command not found after installation.
  - Solution #1: Make sure you opened a new terminal after running the install script.
  - Solution #2: Make sure ~/.local/bin is in your `$PATH`.

- osu! simply doesn't work
  - Solution #1: Install the dependencies listed [here](https://github.com/lutris/docs/blob/master/WineDependencies.md). These dependencies are used for gaming on Linux using wine in general, so they're nice to have anyway.
  - Solution #2: Please create an issue ticket.
