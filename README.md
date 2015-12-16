# MicroArchitecture Project
Michele Burns, Michael Newton, Nick Zayatz, Charlie Adams


## What we have uploaded:
 * CSC3410-MicroArchitecture.circ - The circuit file which contains the machine itself
 * gcd.gm - Macrocode implementation of our GCD
 * gcd.mem - Precompiled version of gcd.gm
 * gmac.gm - Our microcode
 * mem1 & mem2 - ROM images ready to be loaded
 * ram-gcd & ram-gcd-2 - RAM images ready to be loaded that run GCD. The only difference is that have different starting numbers.


## How to set up the machine from scratch:
1. Compile both gmac files.
2. The microinstructon memory file should have broken the hex into 32 bits and 4 bits. Paste these values in their own respective files and remove everything that starts with an `@`.
3. For RAM/GCD, combine the hex values together into sets of 8 hex values. There should be two per line and prepend a zero to any single digits. E.g: `15 1 10 0 9f 0 26 15` -> `15011000 9f002615`.
4. Again for RAM/GCD, prepend the file with `00750000 <sp_word> <cpp_word> <lv_word> <pc_word>` where you replace each argument with the desired value. E.g: `750000 200 400 100 14`.
5. Add an appropriate number of zeros inbetween the first line and GCD depending on what you set PC as. If you set PC as 14 then no zero padding is needed since 0x14 comes directly after `<pc_word>`. 
6. Prepend these files with `v2.0 raw` on its own line.
7. Load the files into their respective modules.
8. Enter the values you would like gcd to be run on at offsets 1 and 2 of lv. The result will be put in offset 3. 
9. Run the machine. It will halt when it's completed.


## How to setup the machine, the easy way:
1. Load mem1 and mem2 into their respective ROM modules if they are not already loaded.

2. Load ram-gcd or ram-gcd-2 into the RAM module. These are preloaded to execute the bootstrap and then gcd.

3. Run the simulation. It will halt when it tries to execute opcode 'a'. Both ram images are set up to halt upon completion. The machine must be reset if you want to use it again after a halt.


## Some notes:
 * The bootstrap is executed by having its opcode (0x75) in the second byte of the first word. This allows for you to set sp, cpp, lv, and pc respectively in the next 4 words. 
 * Currently lv is set at 0x100 and our gcd program uses the values stored in offsets 1 and 2. The result is stored in offset 3. It can run at any speed.
 * Halt is at opcode 0xa



