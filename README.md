Jaga's Goomba Color fork

A fork of Goomba Color with the goal of fixing bugs and incompatibilities in the original.  Based on the 2019-05-04 source.

Some notable hacks and games that have had issues fixed:
- Donkey Kong Land: New Colors Mode, https://www.romhacking.net/hacks/6076/ (file select menu accessible)
- Faceball 2000 (menu accessible)
- Kirby's Dream Land DX Service Repair, https://www.romhacking.net/hacks/6224/ (level 2 palette issues fixed)
- Konami GB Collections 2 and 4 (boots)
- Metal Gear Solid: Ghost Babel (elevator crash fixed)
- Pokemon Crystal (graphical corruption fixed)
- Wario Land DX, https://www.romhacking.net/hacks/6683/ (boots)

Batteryless saving: This allows Goomba Color to save its SRAM data on most modern reproduction/bootleg flash cartridges that have an SRAM chip but no battery installed. This works by writing the SRAM data into Flash ROM memory and restoring the data from Flash ROM into SRAM when booting.

The Flash ROM is updated in the following instances:
- Pressing L+R to bring up the main menu (with a prompt)
- Writing a Save State or Quick Save State by pressing R+SELECT
- Deleting a Save State or SRAM
- Exiting

The batteryless Goomba Color SRAM storage area in Flash ROM is dynamically determined and depends on the maximum ROM size of the flash cartridge. In case you need to extract/inject/edit something, you will find the data at ROM address `flash_size - 0x40000` and the length is 0x10000 bytes. Emulators should also be able to extract the SRAM data into a `.sav` file from a re-dumped compilation.

If you need to manually specify the save data location in ROM, you can append the compiled ROM with `53 56 4C 43` (SVLC) followed by the address in little endian (`00 00 0C 00` would be offset `0xC0000` on the flash chip). Make sure the address is correctly aligned to your flash chip’s sector size and that it’s accessible from the GBA ROM space (max. 32 MB).

Holding SELECT+UP+B on startup will wipe the save data in case something is not working right.

Tested repro cartridge flash chips: 128W30B, 256L30B, 29LV128DT, M36L0R7050T, M36L0R8060T, GL128S, M29W128FH, MSP55LV128M


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
- Radimerry for the MGS:Ghost Babel elevator fix, Faceball menu fix, and SMLDX SRAM fix.
- Therealteamplayer for the default-to-grayscale code for GB games if no SGB palette is found.
- lesserkuma for batteryless saving mod, which you can find at https://github.com/lesserkuma/goombacolor
