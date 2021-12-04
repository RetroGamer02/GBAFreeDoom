## GBAFreedoom

The Freedoom IWAD was made thanks to [the Freedoom team](https://freedoom.github.io), a [free and open-source](https://github.com/freedoom/freedoom/blob/master/COPYING.adoc) game based on the [Doom engine](https://doomwiki.org/wiki/Doom_engine).

A port of [prBoom](https://doomwiki.org/wiki/PrBoom) to the GBA.

This is a result of me, Devin "RetroGamer02", messing around, it works but it's not great. With some help maybe it could be.

**What's hot?**

- Supports Freedoom IWAD.

- Renderer is largely intact. Z-Depth lighting is gone and there is mip-mapping but it's otherwise complete.

- Monster behaviour is all intact. (i.e. sound propagation etc.)

- Framerate is pretty variable. Simple areas run at ~35FPS. Complex areas (e.g.: C4M2) chug along at about 10 FPS. It's running around the same as the original GBA Doom I and Doom II ports. Doom I Episodes 1-3 are all completely playable. Episode 4 chugs.

- Sound and music support. Big thanks to BloodShedder for his Chiptune Doom MOD files.

**What's not?**

- My Markdown skills.

- Demo compatibility is broken.

- General optimisation. We're never going to get a perfect 35FPS, but I think there is still another 25% left without changing the visual quality/correctness/game behaviour. For reference, the first time I ran a build under the emulator it ran at about 3FPS.

- Although it is based on prBoom, most of the engine enhancements (DeHackEd, limit removing etc) have been reverted back to vanilla. This is either for memory or performance reasons. Sadly, [NUTS.wad](https://doomwiki.org/wiki/Joke_WAD#nuts.wad_and_derivatives) and [Okuplok](https://doomwiki.org/wiki/Okuplok_Slaughter_Map) are right out!

- No multiplayer. 



KippyKip is maintaining an upstream fork of DoomHacks GBADoom with new features and fixes. [KippyKip GBA fork](https://github.com/Kippykip/GBADoom)


## Cheats:
**Chainsaw:** L, UP, UP, LEFT, L, SELECT, SELECT, UP  
**God mode:** UP, UP, DOWN, DOWN, LEFT, LEFT, RIGHT, RIGHT  
**Ammo & Keys:** L, LEFT, R, RIGHT, SELECT,UP, SELECT, UP  
**Ammo:** R, R, SELECT,R, SELECT,UP, UP, LEFT  
**No Clipping:** UP, DOWN, LEFT, RIGHT, UP, DOWN, LEFT, RIGHT  
**Invincibility:** A, B, L, R, L, R, SELECT, SELECT  
**Berserk:** B, B, R, UP, A, A, R, B  
**Invisibility:** A, A, SELECT,B, A, SELECT, L, B  
**Auto-map:** L, SELECT,R, B, A, R, L, UP  
**Lite-Amp Goggles:** DOWN,LEFT, R, LEFT, R, L, L, SELECT  
**Exit Level:** LEFT,R, LEFT, L, B, LEFT, RIGHT, A  
**Enemy Rockets (Goldeneye):** A, B, L, R, R, L, B, A  
**Toggle FPS counter:** A, B, L, UP, DOWN, B, LEFT, LEFT  

## Controls:  
**Fire:** B  
**Use / Sprint:** A  
**Walk:** D-Pad  
**Strafe:** L & R  
**Automap:** SELECT  
**Weapon up:** A + R  
**Weapon down:** A + L  
**Menu:** Start  

## Building:

To build the GBA version, you will need DevKitArm. The easiest way to get up and running for Windows users is to download the installer [from here](https://github.com/devkitPro/installer/releases) and install the GBA dev components.

You will also need to use GBAWadUtil, included in the "GBAWadUtil\" directory. Alternatively, download the latest build from [the main source](https://github.com/doomhack/GbaWadUtil) Windows (x64) users can download the binary release from the releases page.

1) Download or Clone GBAFreedoom source code.
Extract the contents to a folder: (e.g.: C:\DevKitPro\Projects\GBAFreedoom)

2) Use GBAWadUtil to create a header file with the WAD data.
Open a command prompt.
Type the following:
```GbaWadUtil.exe -in Freedoom1.wad -cfile Freedoom.wad.c```
And copy it to the ```source\\iwad\\``` directory.
Alternatively, just run the ```build_XXXX.bat``` files and it'll create it in the source\iwad\ path.

3) Open C:\DevKitPro\Projects\GBADoom\source\doom_iwad.h in text editor or code editor of your choice.
4) Change the first line to #include "iwad/**yourfile**.c" e.g.
#include "iwad/Freedoom1.c"
#include "iwad/Freedoom2.c"

5) Run msys2.bat and type ```make```
You may need to edit the msys2.bat with notepad and change the path to go to your real ```msys2\msys2_shell.bat``` file within it if it doesn't work.

6) The project should build GBAFreedoom.gba and GBAFreedoom.elf. You may see a lot of warning messages on the screen. These are normal.

7) Copy GBAFreedoom.gba (this is the ROM file) to your flash cart or run in an emulator.


## Developers:

For development, this project also builds for Windows with Qt. Use the MingW 32bit version or MSVC 32bit. The .pro file at the root of the source tree can be opened in Qt Creator.
