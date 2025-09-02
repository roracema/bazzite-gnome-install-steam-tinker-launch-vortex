Installation Guide: Vortex Mod Manager on Bazzite GNOME

This guide provides a comprehensive, step-by-step walkthrough for installing and configuring Steam Tinker Launch and Vortex Mod Manager on a Bazzite GNOME system. By following these instructions, you will correctly set up your environment to run and mod games, addressing common installation errors and ensuring both tools work seamlessly with your Steam library.
1. Prerequisites

First, ensure that Steam Tinker Launch is properly installed and its command-line tool is functional. You can verify this by checking the version:

steamtinkerlaunch --v

2. Install Vortex

Run the following command to initiate the installation of Vortex Mod Manager within its own isolated Wine prefix.

steamtinkerlaunch vortex install

3. Initial Vortex Launch

Launch Vortex for the first time. This step allows the application to initialize its necessary files and will likely produce a .NET error, which we will fix in the subsequent steps.

steamtinkerlaunch vortex start

Once the Vortex window appears with the .NET error, close it.
4. Find the Wine Executable Path

The winetricks command requires the exact path to the wine executable that Steam Tinker Launch is using. This file is located inside your Proton installation.

ls ~/.steam/root/compatibilitytools.d/<PROTON_VERSION_HERE>/files/bin/wine

Note: You must replace <PROTON_VERSION_HERE> with the name of the specific Proton version you are using (e.g., GE-Proton10-15). Copy the full path that is output by this command.
5. Get the Vortex Wine Prefix Path

This command will print the full path to Vortex's dedicated Wine prefix. Copy this output, as it is required for the next step.

steamtinkerlaunch vortex gp

6. Install .NET with winetricks

Now, combine the two paths you collected in the previous steps to run winetricks in the correct environment. This will bypass the "wineserver not found" error you were experiencing.

WINE="<OUTPUT_FROM_STEP_4>" WINEPREFIX="<OUTPUT_FROM_STEP_5>" /usr/bin/winetricks

7. Select and Install the .NET Component

Once the winetricks graphical user interface (GUI) appears, follow these steps to install the required .NET component:

    Select the option "Select the default wineprefix".

    Select the option "Install a Windows DLL or component".

    Scroll down the list and select dotnet6.

    Click the "OK" button to begin the installation.

8. Run Vortex

With the required .NET component installed, you can now launch Vortex without the previous error. Use the following command every time you want to use Vortex for modding a specific game:

steamtinkerlaunch vortex start --game <game_id>

Note: Replace <game_id> with the numerical Steam ID of the game you want to manage.
Enjoy!


Adding collections
1. Create a desktop application on applications
2. run:
   echo "[Desktop Entry]
Name=Vortex Mod Manager
Comment=Launches Vortex through SteamTinkerLaunch
Exec=steamtinkerlaunch vortex start
Icon=vortex
Terminal=true
Type=Application
Categories=Game;Utility;
" > ~/.local/share/applications/Vortex-SteamTinkerLaunch.desktop && \
chmod +x ~/.local/share/applications/Vortex-SteamTinkerLaunch.desktop && \
update-desktop-database ~/.local/share/applications

NOTE: Dont run via the desktop app, only via command line
