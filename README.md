# zCPU_assembler
An assembler for zCPU, written in HL-ZASM
For use inside the game Garry's Mod, modded with "wiremod", "wire-CPU", and "Advanced Duplicator 2" addons.

# Usage
Download the files and put them in your garrysmod/data folder. Start a game and then use the Advanced Duplicator to paste the "assembler_27" contraption.

![screenshot of the Adv Dupe](https://github.com/Zondartul/zCPU_assembler/blob/main/docs/screenshot_explained.jpg)

Adjust the speed on the assembler CPU down to prevent lag when it finishes. Press Use on the on/off switch and wait for the Assembler to complete it's work. Then turn off the assembler and turn on the target machine. Press Use on the target machine's keyboard and type something. Press F1 for help.

# How it works
The assembler is written as a HL-ZASM program for a zCPU with 64kb RAM/ROM. There are subroutines for string formatting, stream i/o, basic memory allocation, error handling. Several external RAMs (implemented as empty zCPUs) are connected via an address bus with hard-coded offsets. Disk1 is used as input for the assembly text; Disk2 can be filled with a compiled binary, so the assembler compares it's output to this disk for verification (this is currently turned off but can be turned on by changing assemble(stdin_disk1, 0, stdout_disk3) to assemble(stdin_disk1, stdin_disk2, stdout_disk3).

The main program file is assembler_1.txt. Open this file in the zCPU tool and click verify at the bottom of the editor. Once the file is verified, shoot the zCPU with the tool and wait for the file to be uploaded. The main program consists of a library of various utility subroutines, and the assembler propper. The latter consists of a tokenizer, parser, and code emitter.

The example program is a basic text editor that can, in theory, be used to write assembly. The output of the target machine is currently connected to a blank disk, but you can switch this wire to the assembler input instead.

# Future work
I plan to eventually integrate this assembler into the Cyclone Operating System and/or add multi-processor communication so that the assembler zCPU can be used as an external module.
