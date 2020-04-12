# Mega Man Xtreme 2 Xtreme Mode from start
This patch for Mega Man Xtreme on the Gameboy Color enables Xtreme and Bossrush mode from the start without earlier save data.
A detailed description can be found [on the RomHacking page of this hack](http://www.romhacking.net/hacks/5021/), as well as an alternative download link.
In this README you will find further information on how this patch was made and reference material.

## Tools
- [The BGB emulator](http://bgb.bircd.org/#downloads), for disassembly, hex editing, memory viewing, testing and even breakpoints.
- [LunarIPS](https://www.romhacking.net/utilities/240/), to create a patch file.
- [HxD](https://mh-nexus.de/en/hxd/), a clean hex editor used to study the save files with.

## Process
This was the first of the two games on which the extra modes were made available from start.
Firstly the save data was carefully explored with a hex editor.
The effects on the game were observed and notes were taken.
By comparing full savings were all actual slots were deleted in-game and a new clean file it was found out which byte is checked to activate the extra modes.
By tracing to which RAM offset this was written (0xC000, interestingly enough the very first offset) and then using access breakpoints on it, all the code that checks it was found. It was then decided to fool the checks by replacing the loading of the offset with loading a fixed value (0x03, turned out to be the value for the extra modes). This kept most game code intact, instead of making awkward gaps all over the place.

## References
The same references as the other Xtreme 2 project:
- [A visual opcode map for the gameboy Z80.](http://pastraiser.com/cpu/gameboy/gameboy_opcodes.html)
- [Detailed descriptions for the opcodes, which were confusing to me without it.](https://raw.githubusercontent.com/gb-archive/salvage/master/txt-files/gb-instructions.txt)
- [The full gameboy memory map explanation.](http://gameboy.mongenel.com/dmg/asmmemmap.html)
