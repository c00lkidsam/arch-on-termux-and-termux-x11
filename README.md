# arch-on-termux-and-termux-x11
run script in arch-install.sh up above run the commands in termux one by one or copy link and use when or gitclone
Launch and Set Up

After successful installation, you need to launch the system and make a few setups.
How to Launch

Launch the system by simply executing the following command.

archlinux

or with a shorter version

arch

You will be logged in with the default username, root.

Tip

You can log in as another user by providing their username as an argument.

See arch --help for usage information.
How to Set Up the Desktop

You will need to install a desktop environment and a VNC server to get a graphical interface to interact with because this is a minimal installation.

Launch the system and execute the following commands.

    Upgrade system packages

    pacman --color auto -Syu

    Install VNC server

    pacman --color auto -S tigervnc dbus

    Install desktop environment

    pacman --color auto -S xfce4

This command will not only take several gigabytes of your storage but also take a while to complete. Grab a coffee and ensure that Termux remains open during the installation to avoid potential issues.

Tip

You can acquire the Termux wake lock, but it will only work if battery optimization is disabled.
Login

Now all that's left is to log in to your newly installed system and start playing around with some commands. To do that, you need to start a VNC server in Arch Linux and connect to it through a VNC viewer.
How to Start the Desktop

Launch the system and execute the following command.

vncserver "${DISPLAY}"

On the first run of the command above, you will be prompted for a VNC password. This is the password that will be used to securely connect to the VNC server in the VNC viewer app, so save it somewhere.
How to Connect to the Desktop

To connect to the VNC server and view the desktop, you will need to download and install a VNC viewer app of your choice (I recommend AVNC).

    Start the desktop and minimize Termux.

    Open the VNC viewer app, click add server, and fill in the following details:

        Name

        Arch Linux Desktop

        Host

        localhost

        Port
        username 	port
        root 	5900 (works for all users)

        Password

        Enter the VNC password you set when starting the desktop for the first time.

Have Fun

If you managed to get this far without any problems, congratulations! Linux is now installed on your phone, and it's time to explore and have some fun with it!

The possibilities are endless, and the only limits that exist are the ones you set for yourself.

You might want to Google some cool commands and programs to execute or even when you get stuck. Good luck.
Management

A few features have been added to the arch command to simplify some tasks.
How to Rename

Renaming the installed system is far more complicated than just executing a regular mv command.

To rename your installation, execute the following command:

arch --rename <new-directory>

How to Backup

Backing up the installed system is far more complicated than just executing an ordinary tar command.

To back up your installation, execute the following command:

arch --backup <archive-name> [<dirs-to-exclude>]

Note

The backup is performed as a tar archive and compression is determined by the output file extension.
How to Restore

To restore your backed-up installation from the archive, execute the following command:

arch --restore <archive-name>

Note

The rootfs MUST be restored to the original location.

You can rename it afterwards.
How to Uninstall

To uninstall the system, just execute the following command:

arch --uninstall

FAQ

If you encountered some hiccups during the installation or have some burning questions, you are probably not the first one. Feel free to document them in the issues section.

However, a few frequently asked questions have been answered below.
What happens if Termux has root access?

This guide assumes that Termux has no root access and the only root permissions that exist are those simulated in the installed system.

However, if you have tried following the steps above with root permissions in Termux, then you have probably not succeeded because installing and running the system with root permissions in Termux can have unintended effects and should never be done (unless you are sure of what you are doing); otherwise, you might end up damaging your device.

For that reason, I added a safety check to the install script that terminates the installation process if Termux has root access.

There should not be a good enough reason to launch the system when Termux has root permissions because harmless root privileges are still simulated in the system with the help of proot.
Workaround

If you don't mind damaging your device (probably making it unusable) and are ready to get your hands dirty, this section might resonate.

Disabling the safety check will require a deeper understanding of the install script and the installation process. You will need to edit the install script as follows:

    Find and comment the call to the safety check function.

Not very helpful, is it? That's because this is definitely a bad idea, and you are completely liable for any unintended effects of this action.

Just remember, I am mostly lazy and would never implement a safety check for no reason.
Contribution

Contributions to this project are not only welcome but also encouraged.

Here is the current TODO list:

    Add Management Features

        Features:
            Uninstall, back up, restore, and rename an existing installation.

    Utilize the dialog command
        Perform the installation using a GUI (The dialog command comes pre-installed in Termux).

    Automate RootFS updates
        Implemented using GitHub Actions.

    Other improvements
        Ensure all new programs, scripts, or functions adhere to the principle: Perform only one task and do it extremely well.

License

    Copyright (C) 2023-2025  Jore

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
