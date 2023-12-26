# Burnout 3 Setup for PCSX2

This guide will help you turn the PS2 version of Burnout 3: Takedown into an HD remastered version running on the PCSX2 emulator.

> IMPORTANT: This guide will be solely focused on configuring the game, and will not include links to any BIOS or ISO/ROM files.

## Features

* High Resolution
    * Run the game at 1080p+, up from the 480p max of the original PS2 version
* High Quality Textures
    * Replace original textures with upscaled HD versions
* Better Controls
    * Remap controls similar to the original Xbox version, using analog triggers for gas/brake like every other driving game *not* on the PS2
    * Replace controller button textures with high quality versions of PlayStation, Xbox 360 and Xbox One style buttons
* Other perks of emulation
    * Fast forward
    * Save states

## Assumptions & Prerequisites

* PCSX2 Nightly (v1.7.5332 as of this writing)
    * Make sure PCSX2 is configured to run games, Google is your friend
    * XInput controller is being used, though other controllers will work if buttons are translated accordingly
    * Display will be 1080p, higher resolutions are untested
* Burnout 3: Takedown ISO file, USA version with disc ID `SLUS-21050`
* [Burnout 3: Takedown HD Remaster texture pack by Panda_Venom](https://gbatemp.net/threads/burnout-3-takedown-usa-hd-remaster.621068/)
    * You will need a method of extracting 7z files, 7zip is recommended
* A [zip file](https://codeload.github.com/FeralAI/pcsx2-burnout-3/zip/refs/heads/main) or Git clone of this repository

## Install Replacement Textures

PCSX2 replacement textures are typically located by default in a folder named `textures` in the PCSX2 install folder. Each game is in its own subfolder named with the game serial (disc ID), and contains another subfolder named `replacements` for all textures to be replaced.

Burnout 3 textures are located at: `<PCSX2 Install Path>\textures\SLUS-25010\replacements`

### Install HD Remaster Texture Pack

1. Go to [Burnout 3: Takedown HD Remaster texture pack by Panda_Venom](https://gbatemp.net/threads/burnout-3-takedown-usa-hd-remaster.621068/) and download the pack from the link in the first post.
1. Extract the contents of the downloaded .7z file to the `<PCSX2 Install Path>\textures\` folder. When finished you should see a folder named `SLUS-25010` in the `<PCSX2 Install Path>\textures\` folder.

### Install Button Textures (Optional)

I've used some existing button icons from the internet (see credits) to create three button style packs for the menus and UI: PlayStation, Xbox 360, and Xbox One.

Some notes about the button textures:

* A few of the UI textures in each pack were rescaled to render in a proper aspect ratio, instead of being stretched/squished.
* The stock buttons for Aftertouch/Boost (R1) and Crashbreaker (R2) will be remapped, so these texture packs use the remapped button icons. For example, for PlayStation Aftertouch/Boost will display the Cross button, and Crashbreaker will display the Circle button.

To install:

1. Locate the button texture folder from this repository for the buttons you want to install:   
    * `buttons-ps` folder for PlayStation style
    * `buttons-x360` folder for Xbox 360 style
    * `buttons-xb1` folder for Xbox One style
1. Copy the `SLUS-21050` folder from inside the `buttons-[style]` folder into the `<PCSX2 Install Path>\textures\` folder.
    * You will be prompted to overwrite the existing button files, which should be allowed

## Configure PCSX2 Global Settings

Any of these sections can be accessed directly from the top `Settings` menu.

### Graphics

#### Display Tab

* Enable Widescreen Patches: Enabled
* Enable No-Interlacing Patches: Enabled
* Anti-Blur: Enabled

#### Texture Replacement Tab

* Load Texture: Enabled
* Asynchronous Texture Loading: Enabled

### Hotkeys

Hotkeys are configured from the main menu via `Settings > Hotkeys`.

The `Open Pause Menu` hotkey is required to use the per-game controller settings, all others are optional.

These are the recommended hotkeys to set up:

| Hotkey Action | Button Combo |
| - | - |
| System > Open Pause Menu | Back + Start |
| System > Turbo / Fast Forward (Hold) | Back + R-stick Right |
| Save States > Load State | Back + Left Bumper |
| Save States > Save State | Back + Right Bumper |
| Graphics > Toggle On-Screen Display | Back + Y |

These are the same button combos I use in RetroArch so it's easier to remember across different emulators, but use whatever button combos make sense for your setup.

## Burnout 3 Per-Game Settings

In the PCSX2 game list, right click Burnout and select `Properties` to open the per-game settings window. Each of the following sections is an option in the per-game settings side menu.

### Patches

PCSX2 ships with several rendering patches we'll want to enable:

* Widescreen 16:9
* 60 FPS for Menus
* 60 FPS for Crashes
* Progressive Scan

> The `Widescreen 16:9` patch is redundant if `Enable Widescreen Patches` is enabled in PCSX2 global settings.

### Graphics

#### Rendering tab

These settings can be adjusted to taste:

* Internal Resolution: 3x Native (~1080p)
* Mipmapping: Off
* Texture Filtering: Bilinear (Forced)
* Trilinear Filtering: Trilinear (Forced)
* Anisotropic Filtering: 16x

These settings are required:

* Blending Accuracy: Basic (Recommended) **- workaround for HD texture error**
* Manual Hardware Renderer Fixes: Enabled

#### Upscaling Fixes tab

> This tab will only show when `Rendering > Manual Hardware Renderer Fixes` is Enabled.

* Half Pixel Offset: Special (Texture) **- fixes lines across textures**

## Remap Controls

### PCSX2 Controller Configuration

1. While the game is running, use the `Open Pause Menu` hotkey to open the PCSX2 in-game menu.
1. Go to `Game Properties` to open the per-game settings.
1. Go to the `Controller Settings` tab.
1. Remap the following buttons:
    * PCSX2 L2 = XInput Right Bumper
    * PCSX2 R1 = XInput A
    * PCSX2 R2 = XInput B
    * PCSX2 Right Stick Up = XInput Right Trigger
    * PCSX2 Right Stick Down = XInput Left Trigger

### "Burnout 3: Takedown HD" Controls

| Gameplay Action                             | PS                                                                                                                                                                                | XInput                                                                                                                                                                                            | Remapped |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Accelerate (analog)<br>Accelerate (digital) | ![R2](https://upload.wikimedia.org/wikipedia/commons/8/84/PlayStation_4_button_R2.svg)<br>![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg)  | ![RT](https://upload.wikimedia.org/wikipedia/commons/7/7a/Xbox_Right_Trigger.svg)<br>![A](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Xbox_button_A.svg/20px-Xbox_button_A.svg.png) | Yes      |
| Brake (analog)<br>Brake (digital)           | ![L2](https://upload.wikimedia.org/wikipedia/commons/6/67/PlayStation_4_button_L2.svg)<br>![Square](https://upload.wikimedia.org/wikipedia/commons/4/49/PlayStation_button_S.svg) | ![LT](https://upload.wikimedia.org/wikipedia/commons/2/23/Xbox_Left_Trigger.svg)<br>![X](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Xbox_button_X.svg/20px-Xbox_button_X.svg.png)  | Yes      |
| Boost/Aftertouch                            | ![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg)                                                                                            | ![A](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Xbox_button_A.svg/20px-Xbox_button_A.svg.png)                                                                                      | Yes      |
| Crashbreaker                                | ![Circle](https://upload.wikimedia.org/wikipedia/commons/6/6b/PlayStation_button_C.svg)                                                                                           | ![B](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b8/Xbox_button_B.svg/20px-Xbox_button_B.svg.png)                                                                                      | Yes      |
| Change camera                               | ![Triangle](https://upload.wikimedia.org/wikipedia/commons/6/69/PlayStation_button_T.svg)                                                                                         | ![Y](https://upload.wikimedia.org/wikipedia/commons/d/df/Xbox_button_Y.svg)                                                                                                                       | No       |
| Rear-view                                   | ![L1](https://upload.wikimedia.org/wikipedia/commons/6/6c/PlayStation_4_button_L1.svg)                                                                                            | ![LB](https://upload.wikimedia.org/wikipedia/commons/8/8c/Xbox_Left_Bumper.svg)                                                                                                                   | Yes      |
| Change Music                                | ![R1](https://upload.wikimedia.org/wikipedia/commons/3/3b/PlayStation_4_button_R1.svg)                                                                                            | ![RB](https://upload.wikimedia.org/wikipedia/commons/8/89/Xbox_Right_Bumper.svg)                                                                                                                  | Yes      |
| Pause Menu                                  | ![Options](https://upload.wikimedia.org/wikipedia/commons/3/34/PlayStation_4_Options_button.svg)                                                                                  | ![Start](https://upload.wikimedia.org/wikipedia/commons/5/59/Xbox_Start_button.svg)                                                                                                               | No       |

| Menu Action    | PS                                                                                        | Xbox                                                                                                         | Remapped |
| -------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------- |
| Confirm        | ![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg)    | ![A](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Xbox_button_A.svg/20px-Xbox_button_A.svg.png) | No       |
| Cancel         | ![Triangle](https://upload.wikimedia.org/wikipedia/commons/6/69/PlayStation_button_T.svg) | ![Y](https://upload.wikimedia.org/wikipedia/commons/d/df/Xbox_button_Y.svg)                                  | No       |
| Driver Details | ![Circle](https://upload.wikimedia.org/wikipedia/commons/6/6b/PlayStation_button_C.svg)   | ![B](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b8/Xbox_button_B.svg/20px-Xbox_button_B.svg.png) | No       |
| Car Color      | ![Square](https://upload.wikimedia.org/wikipedia/commons/4/49/PlayStation_button_S.svg)   | ![X](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Xbox_button_X.svg/20px-Xbox_button_X.svg.png) | No       |

### Dual Mapped Buttons

The ![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg) button in PCSX2 was not cleared or remapped, so pressing ![A](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Xbox_button_A.svg/20px-Xbox_button_A.svg.png)/![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg) will press ![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg) + ![R1](https://upload.wikimedia.org/wikipedia/commons/3/3b/PlayStation_4_button_R1.svg). This shouldn't be an issue in menus since ![R1](https://upload.wikimedia.org/wikipedia/commons/3/3b/PlayStation_4_button_R1.svg) doesn't do anything, and fine for gameplay since ![Cross](https://upload.wikimedia.org/wikipedia/commons/8/8f/PlayStation_button_X.svg) is Accelerate.

## Credits

* PlayStation buttons, README - [Category:PlayStation controller buttons - Wikimedia Commons](https://commons.wikimedia.org/wiki/Category:PlayStation_controller_buttons)
* PlayStation buttons, textures - [Vector PlayStation buttons by Metal-Txus on DeviantArt](https://www.deviantart.com/metal-txus/art/Vector-PlayStation-buttons-441793653)
* Xbox 360 buttons, README and textures - [Category:Xbox controller buttons - Wikimedia Commons](https://commons.wikimedia.org/wiki/Category:Xbox_controller_buttons)
* Xbox One buttons, textures - [Xbox One buttons by Sub-Zero on RocketLauncher Forums](https://www.rlauncher.com/forum/index.php?threads/xbox-one-controller-icons.2916/post-23882)
