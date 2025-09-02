(WIP)
bazzite-gnome-install-steam-tinker-launch-vortex

This repository offers a comprehensive guide for installing Steam Tinker Launch and Vortex Mod Manager on Bazzite GNOME. The instructions will help you correctly set up your environment to run and mod games, covering everything from initial package installation to final configuration so both tools work with your Steam library.
1. Pre-requisite
   have steamtinkerlaunch command line running, do a:
   steamtinkerlaunch --v
2. steamtinkerlaunch vortex install
3. steamtinkerlaunch vortex start
   (Make sure the vortex opens normally with a dotnet error, close it afterwards, its just for test)
4. ls /home/roracema/.steam/root/compatibilitytools.d/GE-Proton10-15/files/bin/wine
   (ls /home/roracema/.steam/root/compatibilitytools.d/<PROTON_VERSION_HERE>/files/bin/wine)
   (Check if you have an output here)
5. steamtinkerlaunch vortex gp
   (save the output for next step)
6. WINE="<OUTPUT_FROM_STEP_4>" WINEPREFIX="<OUTPUT_FROM_STEP_5>" /usr/bin/winetricks
7. Select the option "Select the default wineprefix"
8. Select the option "Install a Windows DLL or component"
9. Select the following:
   ".NET Desktop Runtime 6"
   ".NET .NET Desktop Runtime 6.0 LTS"
   (Ensure both are installed correctly)
10. steamtinkerlaunch vortex start --game <game_id>

Enjoy!
