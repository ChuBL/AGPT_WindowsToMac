# Quick Start Guide for Installing Windows Steam Games on macOS

## About This Repository
This repository, a fork from [InstallAware's AGPT](https://github.com/installaware/AGPT), simplifies the process of installing Windows apps and games on macOS. It's not affiliated with OpenAI products. Our guide will help you navigate through the installation steps and troubleshooting.

## What to Expect
Run Windows Steam games like Sekiro on Macbook M1 Pro with nearly 60 fps and minimal frame skips.

## Prerequisites

### Hardware
- A Mac running macOS 14 Sonoma or later.

### Software
1. **Xcode** (Version 15 or later): [Download Xcode from App Store](https://apps.apple.com/us/app/xcode/id497799835)
2. **AGPT DMG**: [Download AGPT DMG](www.installaware.com/iamp/agpt.dmg) - [Source](https://github.com/installaware/AGPT)
3. **Apple Game Porting Toolkit DMG**: [Download from Apple](https://developer.apple.com/download/all/?q=game%20porting%20toolkit) (Requires Apple ID) - [Source](https://developer.apple.com/videos/play/wwdc2023/10123/)
4. **Windows version of Steam**: [Download Steam](https://cdn.cloudflare.steamstatic.com/client/installer/SteamSetup.exe) - [Source](https://www.applegamingwiki.com/wiki/Game_Porting_Toolkit#:~:text=Steam%20%E2%80%A2-,Link,-Download%20the%20Windows)

## Installation Steps
1. Install Xcode.
2. Open AGPT.dmg and move **Game Porting Toolkit Installer.app** to the Applications folder.
3. Launch **Game Porting Toolkit Installer.app**.

<img width="609" alt="Screenshot 2023-09-24 at 02 06 19" src="https://github.com/installaware/AGPT/assets/24454000/780e4c57-d24f-43a9-885f-a2a6fe5cb5b7">

4. Check requirements in the app window.
5. Browse and select **Apple Game Porting Toolkit DMG** and **Windows version of Steam EXE** in the first and third fields.
6. Proceed with the installation wizard for Steam.
7. Ignore if the first Steam launch attempt fails.
8. Steam is now installed on your Mac.

## Creating a Steam Shortcut
Follow the guide from [AppleGamingWiki](https://www.applegamingwiki.com/wiki/Game_Porting_Toolkit#Shortcut) to create a Steam shortcut using macOS's Automator app. Adjust `{path1}`, `{path2}`, and `{path3}` as per your system's directories.


1. **Open Automator**: Locate and open the Automator app on your Mac.
2. **Create a New Application**: In Automator, choose to create a new application.
3. **Run Shell Script**: In the actions panel, search for and select the 'Run Shell Script' action.
4. **Determine Paths**: You need to find three specific paths on your Mac:

   - **Wine Prefix Path (`{path1}`)**: This is the directory for `.wine`, typically found in your user directory. For example, `/Users/[YourUserName]/.wine`.

   - **Wine Binary Path (`{path2}`)**: Locate the `wine64` binary in the `game-porting-toolkit` directory. For example, `/usr/local/Cellar/game-porting-toolkit/1.1/bin/wine64`. Note that `1.1` is the version number, which may vary.

   - **Steam Executable Path (`{path3}`)**: The path to your Steam executable, usually `"C:\Program Files (x86)/Steam/steam.exe"`. Remember to include quotes due to spaces in the path.

5. **Enter the Script**: In the Automator script box, enter the following code, replacing `{path1}`, `{path2}`, and `{path3}` with your actual paths:

   ```
   MTL_HUD_ENABLED=0 WINEESYNC=1 WINEPREFIX="{path1}" "{path2}" "{path3}"
   ```

   Example:

   ```
   MTL_HUD_ENABLED=0 WINEESYNC=1 WINEPREFIX="/Users/John/.wine" "/usr/local/Cellar/game-porting-toolkit/1.1/bin/wine64" "C:\Program Files (x86)/Steam/steam.exe"
   ```

6. **Save the Application**: Save the Automator application, ideally in the Applications folder for easy access.
7. **Customize Shortcut (Optional)**: To add a custom icon, select the shortcut, press ⌘ Command+I to get info, and drag a PNG file onto the icon in the top left of the info window.

## Exiting Steam
Always use the Exit button in the Steam menu to prevent background processes from unintentionally relaunching Steam.
