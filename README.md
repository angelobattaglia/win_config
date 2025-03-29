# win_config

An opinionated way to configure a Windows system with zero compromises.

- C:\Datas: storing Datas (optional)
- C:\Git: storing Git reposistories
- C:\Software: directories of installed programs

## Debloat Windows

- [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater)

As admin,

```powershell
# Check if it's restricted
Get-ExecutionPolicy 
# Execution policy
# Set-ExecutionPolicy AllSigned
Set-ExecutionPolicy Unrestricted
```

## Software to Install

![Software Installed](./assets/SoftwareInstalled.png)
![Bar](./assets/Bar.jpg)

### 🌐 Utilities
- **Windows Terminal**
- **Brave Browser**

### 📝 Editors
- **Neovim**
- **R-Studio**
- **VSCode**
- **Eclipse**

### 🎥 Multimedia
- **mpv**, **SumatraPDF** 
- [**ImageMagick**](https://imagemagick.org/index.php)
- **ffmpeg**, **pandoc**, **yt-dlp**
- [**PDFtk**](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/)
- **Xournalpp**, **OBS**, **Draw.io**, **Inkscape**, **GIMP**
- **CDBurnerXP**, **rufus**
- **qBittorrent**, **Emule**
- **7-Zip**, **Mp3tag**
- [**Ardour**](https://ardour.org/)
- [**GUITAR PRO**](https://www.guitar-pro.com/)

### 💻 Development Tools
- **Strawberry Perl**, **MinGW**, **cmake**, **tcc**
- **git**, **MiKTeX**, **Python**, **Anaconda**
- **Julia**, **golang**, **R**, **Node.js**
- **Docker**, **JDK Corretto**
- [**Build Tools for Visual Studio**](https://www.jaacostan.com/2019/12/rust-error-linker-linkexe-not-found.html#:~:text=While%20compiling%20Rust%20program%20in,Tools%20for%20Visual%20Studio%202019)

### 📦 Package Managers
- **npm**, [**pip**](https://bootstrap.pypa.io/get-pip.py)
- **nuget**, **winget**, **Scoop**, **Chocolatey**

### 🌟 Other Tools
- **MkDocs**, **Hugo**, **WinRar**
- **Google Earth Pro**, **Stellarium**, **QCAD**
- **[HWinfo (information on the system hardware and software)](https://www.hwinfo.com/download/)**
- **[Geek uninstaller (third-party uninstaller for Windows 11 that goes beyond the default Windows uninstaller by removing leftover files, registry entries, and bloat from software installations)](https://geekuninstaller.com/)**
- **[NetDisabler](https://www.NetDisabler.com)**

### 🔗 Useful Links
- [**Override Windows Store Python issue**](https://superuser.com/questions/1770299/override-windows-store-open-action-when-launching-python-in-powershell)
- [**Remove Quick Access bloat in Windows 11**](https://www.minitool.com/news/windows-11-quick-access.html)

### 🌐 Browser Extensions
- I don't care about cookies, Unhook, Shazam
- Instagram story hider, Insta feed eradicator

### Android apps
- shizuku, canta, f-droid
- [adb](https://developer.android.com/tools/releases/platform-tools)

## Other interesting scripts

- [NotCPUCores](https://github.com/rcmaehl/NotCPUCores)
- [Sophia-Script-for-Windows](https://github.com/farag2/Sophia-Script-for-Windows)
- [Activation Scripts](https://github.com/massgravel/Microsoft-Activation-Scripts)
- [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater)
- [Win11Debloat](https://github.com/Raphire/Win11Debloat)
- [tiny11](https://github.com/ntdevlabs/tiny11builder)

## Examples

This allows me to perform certain tasks from the command line.

- Download as mp3

```powershell
yt-dlp --extract-audio --audio-format mp3 https://www.youtube.com/watch?v=VideoHash
```

- Convert from mkv to mp4 (valid for other formats as well)

```powershell
ffmpeg -i filename.mkv filename.mp4
```

## BitLocker

### Windows Editions with BitLocker.
BitLocker is available only on the following editions of Windows:

1. Windows Pro
2. Windows Enterprise
3. Windows Education

Windows Home editions do not include BitLocker.

### Removing BitLocker

On cmd.exe, as administrator

Verify that all drives are decrypted. Use the status command to verify all drives are fully decrypted:

```batch
manage-bde -status
```

Each drive should show:

```
Conversion Status: Fully Decrypted
Percentage Encrypted: 0.0%
```

If not, then uncrypt them all. 
Clear Auto-Unlock Keys (If Needed). After the OS volume (C:) is fully decrypted, you can clear any remaining auto-unlock
keys associated with the data volumes (D: and E:):
```batch
manage-bde -autounlock -clearallkeys C:
```

Since C: is already decrypted after this (always check, repeatedly, with `manage-bde -status`), you no longer need to clear auto-unlock keys. 
Instead, proceed with decrypting the data drives (D: and E:).

Run these commands individually:

```batch
manage-bde -off D:
manage-bde -off E:
```

this would de-activate bitlocker, for the `C:` and `D:` drives, for example

---

## Deleting the `C:\Windows.old` repository

if on `C:\` the directories can't be deleted
```batch
takeown /f C:\Windows.old /r /d y
icacls C:\Windows.old /t /grant everyone:F
rmdir /S /Q Windows.old
```

## Some notes on Hibernation

Disable Hibernate:
1. Open Command Prompt as Administrator:
2. Search for "Command Prompt" in the Start menu, right-click it, and select Run as administrator.
3. Type the following command and press Enter:

    ```batch
    powercfg -h off
    ```
4. Run the Command to Enable Hibernation:
    ```batch
    powercfg -h on
    ```

Verify Hibernation is Enabled:
1. Pressing Win + I to open Settings.
2. Navigating to System > Power & battery > Advanced settings.
3. Checking if Hibernate is listed under power options (if not, proceed to the next section to add it to the power menu).

## Disable Sticky Keys

On Command Prompt (as admin):

1. Disable Sticky Keys: Run the following command in the command prompt:

```cmd
reg add "HKEY_CURRENT_USER\Control Panel\Accessibility\StickyKeys" /v "Flags" /t REG_DWORD /d 0 /f
```
This will disable Sticky Keys.

2. Disable the Shortcut: 
If you want to disable the shortcut (pressing Shift five times to enable Sticky Keys), use this command:

```cmd
reg add "HKEY_CURRENT_USER\Control Panel\Accessibility\HotKeys" /v "StickyKeys" /t REG_DWORD /d 0 /f
```
You can restart your computer for the changes to take effect

## make a local account

Make a local account instead of using your MS one
