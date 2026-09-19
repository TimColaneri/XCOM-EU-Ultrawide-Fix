# XCOM: Enemy Unknown Ultrawide Fix

An unofficial ultrawide resolution fix for **XCOM: Enemy Unknown** that corrects mouse cursor and UI alignment problems at ultrawide and super-ultrawide resolutions.

XCOM: Enemy Unknown does not properly handle mouse coordinates at certain aspect ratios. The game can render across the entire display while calculating mouse positions using a different aspect ratio, causing the visible cursor position and the location where the game registers clicks to become misaligned.

This fix provides resolution-specific patched executables for both the **Steam** and **GOG** versions of XCOM: Enemy Unknown.

## Supported Resolutions

| Resolution | Aspect Ratio | ConstrainedAspectRatio |
| ---------- | -----------: | ---------------------: |
| 2560×1080  |         21:9 |              `2.37037` |
| 3440×1440  |         21:9 |              `2.38889` |
| 3840×1600  |        24:10 |              `2.40000` |
| 5120×1440  |         32:9 |              `3.55556` |

Each resolution requires its corresponding patched executable and `ConstrainedAspectRatio` setting.

## Compatibility and Testing

The current release includes separate packages for the **Steam** and **GOG** versions of XCOM: Enemy Unknown.

| Version | Resolution | Status                                 |
| ------- | ---------: | -------------------------------------- |
| Steam   |  2560×1080 | ✅ Confirmed working                    |
| Steam   |  3440×1440 | Generated, awaiting additional testing |
| Steam   |  3840×1600 | Generated, awaiting additional testing |
| Steam   |  5120×1440 | Generated, awaiting additional testing |
| GOG     |  2560×1080 | Generated, awaiting additional testing |
| GOG     |  3440×1440 | ✅ Confirmed working                    |
| GOG     |  3840×1600 | Generated, awaiting additional testing |
| GOG     |  5120×1440 | Generated, awaiting additional testing |

**Steam 2560×1080** has been tested and confirmed working by the project author.

**GOG 3440×1440** has been tested and confirmed working with help from the community.

The remaining executables were generated using the same patching method and resolution-dependent calculation, but have not yet been independently tested in-game.

If you successfully test one of these combinations, please consider opening an issue or discussion with your results so its status can be updated.

---

# Installation

## 1. Download the Correct Package

Go to the **Releases** section of this repository and download the package corresponding to your version of the game:

### Steam

`XCOM_EU_Ultrawide_Fix_Steam.zip`

### GOG

`XCOM_EU_Ultrawide_Fix_GOG.zip`

**Do not mix the Steam and GOG executables.**

The Steam and GOG releases of the game use different executables. A Steam executable should only be used with the Steam version of the game, and a GOG executable should only be used with the GOG version.

Each package contains patched executables for:

* 2560×1080
* 3440×1440
* 3840×1600
* 5120×1440

Choose the executable matching the resolution you intend to use.

---

## 2. Locate XComGame.exe

The file that must be replaced is:

`XComGame.exe`

### Steam

For a standard Steam installation, it is normally located at:

`C:\Program Files (x86)\Steam\steamapps\common\XCom-Enemy-Unknown\Binaries\Win32\XComGame.exe`

If your Steam library is installed somewhere else, the beginning of this path will be different.

To find the installation through Steam:

1. Open Steam.
2. Go to your Library.
3. Right-click **XCOM: Enemy Unknown**.
4. Select **Properties**.
5. Select **Installed Files**.
6. Click **Browse**.
7. Open `Binaries\Win32`.

### GOG

The GOG installation directory depends on where you chose to install the game.

Locate your XCOM: Enemy Unknown installation and open:

`Binaries\Win32`

Inside you should find:

`XComGame.exe`

---

## 3. Back Up the Original Executable

**Do not skip this step.**

Before replacing anything, make a backup of your original:

`XComGame.exe`

For example, rename it:

`XComGame_original.exe`

or copy it somewhere outside the game directory.

Keep the original executable from your own version of the game.

Steam and GOG executables are not interchangeable.

---

## 4. Install the Patched Executable

Extract the ZIP for your version of the game.

Inside are separate executables for each supported resolution.

For example, a Steam user running at 2560×1080 would select:

`XComGame_Steam_2560x1080.exe`

A GOG user running at 3440×1440 would select:

`XComGame_GOG_3440x1440.exe`

Rename the selected executable to:

`XComGame.exe`

Copy it into the game's:

`Binaries\Win32`

directory and replace the original executable.

Make sure you have selected both the correct:

* Game version: **Steam or GOG**
* Screen resolution

---

# Configure XComCamera.ini

Replacing the executable is only one part of the fix.

XCOM must also be configured to use the aspect ratio corresponding to your resolution.

## 5. Locate XComCamera.ini

The configuration file is normally located at:

`%USERPROFILE%\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config\XComCamera.ini`

An easy way to get there is to press:

**Windows Key + R**

and enter:

`%USERPROFILE%\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config`

If your Documents folder is managed by OneDrive, also check:

`%USERPROFILE%\OneDrive\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config`

Do not edit the similarly named default configuration files inside the game's installation directory.

If the configuration directory does not exist yet, launch XCOM: Enemy Unknown at least once so the game can create it.

---

## 6. Back Up XComCamera.ini

Before editing the configuration, make a copy of:

`XComCamera.ini`

For example:

`XComCamera_backup.ini`

---

## 7. Set ConstrainedAspectRatio

Open `XComCamera.ini` in Notepad or another text editor.

Find the:

`[Engine.Camera]`

section.

It should contain settings similar to:

```ini
[Engine.Camera]
DefaultAspectRatio=1.778
bConstrainAspectRatio=true
ConstrainedAspectRatio=1.778
```

Make sure:

```ini
bConstrainAspectRatio=true
```

Then change `ConstrainedAspectRatio` to the value corresponding to your resolution:

| Resolution | Setting                          |
| ---------- | -------------------------------- |
| 2560×1080  | `ConstrainedAspectRatio=2.37037` |
| 3440×1440  | `ConstrainedAspectRatio=2.38889` |
| 3840×1600  | `ConstrainedAspectRatio=2.40000` |
| 5120×1440  | `ConstrainedAspectRatio=3.55556` |

The value is calculated from:

`Screen Width ÷ Screen Height`

For example:

`2560 ÷ 1080 = 2.37037`

and:

`5120 ÷ 1440 = 3.55556`

Save `XComCamera.ini` after making the change.

---

# 8. Launch the Game

Launch **XCOM: Enemy Unknown** normally.

Set the game's resolution to the same resolution as the patched executable you installed.

For example, a Steam 2560×1080 installation should use:

```text
XComGame_Steam_2560x1080.exe
renamed to XComGame.exe

ConstrainedAspectRatio=2.37037

Game resolution: 2560×1080
```

These settings must correspond to one another.

The mouse cursor should now line up correctly with the location where the game registers clicks.

---

# What Does This Fix?

At unsupported widescreen and ultrawide aspect ratios, XCOM: Enemy Unknown can incorrectly calculate mouse coordinates.

This can cause:

* Buttons to respond when the cursor is positioned beside them
* Mouse offset that becomes increasingly severe toward the edges of the screen
* Difficulty selecting UI elements
* Incorrect mouse interaction during tactical gameplay
* Severe cursor misalignment at very wide aspect ratios

The resolution-specific executable patches modify the game's mouse-coordinate scaling so it corresponds to the selected resolution.

---

# Technical Details

The original executable uses a horizontal mouse-coordinate scale based on a width of 1280 pixels.

The original scale is:

`1 / 1280 = 0.00078125`

The ultrawide fix replaces this with a resolution-dependent scale calculated as:

`height / (720 × width)`

which is equivalent to:

`1 / (720 × aspect ratio)`

The patch changes three four-byte locations in `XComGame.exe`.

Two locations redirect existing `mulss` instructions to a new scale value, while the third location stores the new 32-bit floating-point scale.

The same patch locations are present in the supported Steam and GOG executables. The scale value itself changes depending on the selected resolution.

| Resolution | Float Bytes   |
| ---------- | ------------- |
| 2560×1080  | `9A 99 19 3A` |
| 3440×1440  | `C8 68 18 3A` |
| 3840×1600  | `26 B4 17 3A` |
| 5120×1440  | `CD CC CC 39` |

The values above are stored as little-endian IEEE-754 32-bit floating-point values.

---

# Troubleshooting

## The mouse is still offset

Make sure all three of these match:

1. The resolution of the patched `XComGame.exe`
2. The `ConstrainedAspectRatio` value in `XComCamera.ini`
3. The resolution selected inside XCOM

Also make sure you installed the correct **Steam or GOG** executable.

---

## The game asks for steam_api.dll

If you own the GOG version and receive an error involving:

`steam_api.dll`

you most likely installed the **Steam executable**.

Restore your original GOG `XComGame.exe` and install the corresponding executable from the GOG package instead.

---

## The game crashes or does not start

Restore your original `XComGame.exe` backup.

Double-check that you selected the correct Steam/GOG package and the correct resolution.

### Steam

Steam users can restore the original executable using **Verify integrity of game files**.

Keep in mind that verifying the game files will replace the patched executable.

### GOG

GOG users should restore the original executable from their own backup or installation.

---

# Uninstallation

To completely remove the fix:

1. Remove the patched `XComGame.exe`.
2. Restore your original `XComGame.exe`.
3. Restore your backup of `XComCamera.ini`, or change `ConstrainedAspectRatio` back to its previous value.

---

# XCOM: Enemy Unknown vs. Enemy Within

This fix is specifically for:

**XCOM: Enemy Unknown**

Enemy Unknown uses:

`XComGame.exe`

Enemy Within uses:

`XComEW.exe`

**Do not replace `XComEW.exe` with these files.**

Enemy Within is not currently supported by this fix.

---

# Contributing and Testing

Additional testing is welcome, particularly for the resolution/version combinations that have not yet been independently confirmed.

If you test one of these versions successfully, please include:

* Steam or GOG
* Resolution
* Whether the game launches normally
* Whether menu/UI mouse alignment is correct
* Whether tactical mouse interaction works correctly

Bug reports and additional information can be submitted through the repository's Issues section.

---

# Credits

Created by **Tim Colaneri**.

Special thanks to the community members who helped add and verify GOG support:

* **tarnishedmoth** for reporting the original GOG compatibility issue and providing information about the problem at 3440×1440.
* **naqimirza-glitch** for helping develop and test the GOG 3440×1440 fix and providing the original and working patched GOG executables used to verify the patch.

Their contributions made it possible to identify the differences between the Steam and GOG releases and add separate GOG-compatible files to the project.

ChatGPT assisted with reverse-engineering analysis, comparison and verification of the executable changes, deriving the multi-resolution patching method, and development of supporting tools and documentation.

---

# Disclaimer

This is an unofficial community-created modification and is not affiliated with, sponsored by, or endorsed by Firaxis Games, 2K, GOG, Valve, or any other party associated with XCOM.

XCOM and related names and trademarks belong to their respective owners.

Always back up your original game files before installing modifications.

Use this modification at your own risk.
