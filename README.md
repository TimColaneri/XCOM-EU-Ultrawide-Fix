# XCOM: Enemy Unknown Ultrawide Fix

An unofficial ultrawide resolution fix for **XCOM: Enemy Unknown** that corrects mouse cursor and UI alignment problems at ultrawide and super-ultrawide resolutions.

XCOM: Enemy Unknown does not properly handle mouse coordinates at certain aspect ratios. The game can render across the entire display while calculating mouse positions using a different aspect ratio, causing the visible cursor position and the location where the game registers clicks to become misaligned.

This fix provides resolution-specific patched executables that correct this behavior.

## Supported Resolutions

| Resolution | ConstrainedAspectRatio |
| ---------- | ---------------------: |
| 2560×1080  |              `2.37037` |
| 3440×1440  |              `2.38889` |
| 3840×1600  |              `2.40000` |
| 5120×1440  |              `3.55556` |

Each resolution requires its corresponding patched executable.

---

# Installation

## 1. Locate XComGame.exe

For a standard Steam installation, the executable is located at:

```text
C:\Program Files (x86)\Steam\steamapps\common\XCom-Enemy-Unknown\Binaries\Win32\XComGame.exe
```

If your Steam library is installed somewhere else, the beginning of this path will be different.

The important part is:

```text
steamapps\common\XCom-Enemy-Unknown\Binaries\Win32\XComGame.exe
```

### Easy way to find the folder through Steam

If you aren't sure where XCOM is installed:

1. Open **Steam**.
2. Go to your **Library**.
3. Right-click **XCOM: Enemy Unknown**.
4. Select **Properties**.
5. Select **Installed Files**.
6. Click **Browse**.

This will open the XCOM installation directory.

From there, open:

```text
Binaries
└── Win32
    └── XComGame.exe
```

## 2. Back Up XComGame.exe

**Before replacing anything, make a backup of your original `XComGame.exe`.**

For example, rename it:

```text
XComGame_original.exe
```

or copy it somewhere outside the game directory.

This makes it easy to restore the original game if something goes wrong.

## 3. Install the Patched Executable

Open the folder in this package corresponding to your desired resolution.

For example:

```text
2560x1080\
3440x1440\
3840x1600\
5120x1440\
```

Inside the appropriate folder, locate the patched:

```text
XComGame.exe
```

Copy it to:

```text
...\XCom-Enemy-Unknown\Binaries\Win32\
```

and replace the original `XComGame.exe`.

**Make sure you use the executable that matches the resolution you intend to play at.**

For example, if you are playing at **2560×1080**, use the `XComGame.exe` from the `2560x1080` folder.

---

# Configure the Aspect Ratio

The patched executable is only one part of the fix.

You must also configure XCOM to use the correct aspect ratio for your resolution.

## 4. Locate XComCamera.ini

The configuration file is normally located in your Windows Documents folder:

```text
C:\Users\<YOUR USERNAME>\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config\XComCamera.ini
```

A quick way to get there is to press **Windows Key + R** and enter:

```text
%USERPROFILE%\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config
```

Press **Enter**.

You should see:

```text
XComCamera.ini
```

If your Documents folder is managed by OneDrive, the location may instead resemble:

```text
C:\Users\<YOUR USERNAME>\OneDrive\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config\XComCamera.ini
```

**Do not edit the similarly named default configuration files inside the Steam installation directory.** The configuration used for this setting is the copy under your Documents/My Games folder.

## 5. Back Up XComCamera.ini

Before editing it, make a copy of:

```text
XComCamera.ini
```

For example:

```text
XComCamera_backup.ini
```

## 6. Edit ConstrainedAspectRatio

Open `XComCamera.ini` using Notepad or another text editor.

Look for the `[Engine.Camera]` section and the following settings:

```ini
[Engine.Camera]
DefaultAspectRatio=1.778
bConstrainAspectRatio=true
ConstrainedAspectRatio=
```

Set `ConstrainedAspectRatio` to the value corresponding to your resolution.

### 2560×1080

```ini
ConstrainedAspectRatio=2.37037
```

### 3440×1440

```ini
ConstrainedAspectRatio=2.38889
```

### 3840×1600

```ini
ConstrainedAspectRatio=2.40000
```

### 5120×1440

```ini
ConstrainedAspectRatio=3.55556
```

The value is simply:

```text
Screen Width ÷ Screen Height
```

For example:

```text
2560 ÷ 1080 = 2.37037
5120 ÷ 1440 = 3.55556
```

Save `XComCamera.ini` after making the change.

---

# 7. Launch the Game

Launch **XCOM: Enemy Unknown** normally.

Set the game's resolution to the same resolution as the patched executable you installed.

For example:

```text
2560×1080 patched XComGame.exe
        +
ConstrainedAspectRatio=2.37037
        +
Game resolution set to 2560×1080
```

All three should match.

The mouse cursor should now correctly correspond to the location where the game registers clicks.

---

# What Does This Fix?

At unsupported widescreen and ultrawide aspect ratios, XCOM: Enemy Unknown can incorrectly calculate mouse coordinates.

This can result in problems such as:

* Buttons responding when the cursor is positioned beside them
* Increasing mouse offset toward the edges of the screen
* Difficulty selecting UI elements
* Incorrect mouse interaction during tactical gameplay
* Severe cursor misalignment at very wide aspect ratios

The resolution-specific executable patches correct the game's mouse-coordinate calculations for the selected resolution.

---

# Troubleshooting

## The mouse is still offset

Make sure all three settings match:

1. The resolution of the patched `XComGame.exe`
2. The `ConstrainedAspectRatio` value in `XComCamera.ini`
3. The resolution selected in XCOM

For example, a 2560×1080 setup should use:

```text
Patched executable:     2560×1080 version
Game resolution:       2560×1080
ConstrainedAspectRatio: 2.37037
```

## I can't find XComGame.exe

For Steam, right-click the game and select:

```text
Properties → Installed Files → Browse
```

Then navigate to:

```text
Binaries\Win32\
```

The full default Steam path is:

```text
C:\Program Files (x86)\Steam\steamapps\common\XCom-Enemy-Unknown\Binaries\Win32\XComGame.exe
```

## I can't find XComCamera.ini

Check:

```text
%USERPROFILE%\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config\
```

If you use OneDrive for your Documents folder, also check:

```text
%USERPROFILE%\OneDrive\Documents\My Games\XCOM - Enemy Unknown\XComGame\Config\
```

If the configuration folder hasn't been created yet, launch the game at least once and then check again.

## The game crashes or doesn't start

Restore your backup of the original:

```text
XComGame.exe
```

The patched executable may not be compatible with every version or distribution of the game.

You can also use Steam's **Verify integrity of game files** feature to restore the original executable.

**Note:** Verifying the game files will replace the patched executable, so the fix will need to be installed again afterward.

---

# Uninstallation

To completely remove the fix:

1. Remove the patched `XComGame.exe`.
2. Restore your original `XComGame.exe`.
3. Restore your backup of `XComCamera.ini`, or change `ConstrainedAspectRatio` back to its previous value.

If you no longer have your original executable, use Steam's file verification feature to restore it.

---

# Compatibility

This fix is intended for:

**XCOM: Enemy Unknown — Windows / Steam**

The Enemy Unknown executable is:

```text
XComGame.exe
```

This should not be confused with the **Enemy Within** executable, which is:

```text
XComEW.exe
```

This package was created for **Enemy Unknown**.

Compatibility with every executable version, storefront, or modification is not guaranteed.

---

# Credits

Created by **Tim Colaneri**.

This fix was created to make XCOM: Enemy Unknown properly playable at modern ultrawide and super-ultrawide resolutions.

---

# Disclaimer

This is an unofficial community-created modification and is not affiliated with, sponsored by, or endorsed by Firaxis Games, 2K, or any other party associated with XCOM.

XCOM and related names and trademarks belong to their respective owners.

Always back up your original game files before installing modifications.

Use this modification at your own risk.


Restore the backup copy of your original XComGame.exe.

If you no longer have the original executable, use your game launcher's file-verification feature to restore it.

Disclaimer

This is an unofficial community fix and is not affiliated with or endorsed by Firaxis Games, 2K, or the XCOM developers or publishers.

Use these files at your own risk. Always keep a backup of your original game files.
