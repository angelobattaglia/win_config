# First things first: Debloat Windows

- [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater)

## 3 directories

- C:\Datas: where I store my datas
- C:\Git: where I store my Git reposistories
- C:\Software: where I install most of the software

## Software to Install in C:\Software and then set it all as Environment Variable PATH

![Software Installed](./assets/SoftwareInstalled.jpg)
![Bar](./assets/Bar.jpg)

- Web Browser: Brave, [Ungoogled Chromium](https://github.com/Eloston/ungoogled-chromium), [min browser](https://minbrowser.org/)
- Terminal Emulators: Windows Terminal, cmder
- Text Editors: NeoVim, VSCode, Visual Studio, Eclipse
- Multimedia: mpv, SumatraPDF (Install it on C:\Software\ and then add it to PATH), Xournalpp, Kdenlive, GIMP, Premiere, After Effects, Photoshop, Illustrator, ardour, OBS, Draw.io, ffmpeg
- Compilers: Strawberry Perl, MinGW, tcc, git, CygWin, dotnet, MiKTeX, Julia, golang, MATLAB, Haskell, R, Python, Node.js, Rust, vlang, Ruby, Scala, Jupyter, [Java 8](https://docs.aws.amazon.com/corretto/latest/corretto-11-ug/downloads-list.html), Docker, [Visual Studio Build Tools (2019)](https://www.jaacostan.com/2019/12/rust-error-linker-linkexe-not-found.html#:~:text=While%20compiling%20Rust%20program%20in,Tools%20for%20Visual%20Studio%202019)
- Package Managers: npm, pip, nuget, winget, Scoop, [Chocolatey](https://www.youtube.com/watch?v=-5WLKu_J_AE)
- Other: WinRar, Freedom.to, Google Earth Pro, Stellarium, youtube-dl
- All datas in directories such as C:\Datas and C:\Git

## Examples

This allows me to perform certain tasks from the command line.

- Download as mp3

```powershell
youtube-dl --extract-audio --audio-format mp3 https://www.youtube.com/watch?v=VideoHash
```

- Convert from mkv to mp4 (valid for other formats as well)

```powershell
ffmpeg -i filename.mkv filename.mp4
```

## USAGE of the profile.code-profile for Visual Studio Code

Press

```keyboard
ctrl + shift + p
```

.. then digit ..

```keyboard
import settings from a profile
```

.. and just import the file "profile.code-profile" from the right location ..
to export setting instead

```keyboard
export settings ..
```
