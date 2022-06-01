Jaga's Goomba Color fork

A fork of Goomba Color with the goal of fixing bugs and incompatibilities in the original.  Based on the 2019-05-04 source.

Some notable hacks and games that have had issues fixed:
- Donkey Kong Land: New Colors Mode, https://www.romhacking.net/hacks/6076/ (file select menu accessible)
- Kirby's Dream Land DX Service Repair, https://www.romhacking.net/hacks/6224/ (level 2 palette issues fixed)
- Konami GB Collections 2 and 4 (boots)
- Metal Gear Solid: Ghost Babel (elevator crash fixed)
- Pokemon Crystal (graphical corruption fixed)
- Wario Land DX, https://www.romhacking.net/hacks/6683/ (boots)

To build:
- Install the latest DevkitPro GBA tools
- Navigate Msys2 to this directory
- make
- Rename font.lz77.o to font.o and fontpal.bin.o to fontpal.o
- make

To test, I build a ROM with the resulting jagoombacolor.gba and the game I'm testing using goombafront.exe, then run it in mGBA.  You can find goombafront.exe as part of the Goomba Color releases.  For helpful debug symbols, take jagoombacolor.elf, put it in the same directory as the built ROM, and rename it to (ROM name).elf.  (Thanks to Endrift for the tip.)
Also included is a simple .bat file that will use gdb to dump debug symbols to a text file.

Thanks to:
- Dwedit for the Goomba Color emulator, which you can find at https://www.dwedit.org/gba/goombacolor.php.  If you'd like to incorporate my changes into Goomba Color, you're more than welcome to.
- FluBBa for the Goomba emulator before that: http://goomba.webpersona.com/
- Minucce for help with ASM and pointing me in the right direction.
- Sterophonick for code tweaks and featuring Jagoomba in the excellent Simple kernel for the EZ-Flash Omega carts: https://gbatemp.net/threads/new-theme-for-ez-flash-omega.520665/
- EZ-Flash for releasing the source to their modified Goomba Color builds, which hopefully allows this to support the Omega Definitive Edition's rumble features
- Nuvie for the code that saves the desired Game Boy type per game.
- Radimerry for the MGS:Ghost Babel elevator fix
- Therealteamplayer for the default-to-grayscale code for GB games if no SGB palette is found.