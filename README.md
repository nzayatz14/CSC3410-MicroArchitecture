# MicroArchitecture Project
Michele Burns, Michael Newton, Nick Zayatz, Charlie Adams


## What we have uploaded:
 * CSC3410-MicroArchitecture.circ - The circuit file which contains the machine itself
 * gcd.gm - Macrocode implementation of our GCD
 * gcd.mem - Precompiled version of gcd.gm
 * gmac.gm - Our microcode
 * mem1 & mem2 - ROM images ready to be loaded
 * ram-gcd & ram-gcd-2 - RAM images ready to be loaded that run GCD. The only difference is that have different starting numbers.


## How to run the the machine:
1. Load mem1 and mem2 into their respective ROM modules if they are not already loaded.

2. Load ram-gcd or ram-gcd-2 into the RAM module. These are preloaded to execute the bootstrap and then gcd.

3. Run the simulation. It will halt when it tries to execute opcode 'a'. Both ram images are set up to halt upon completion. The machine must be reset if you want to use it again after a halt.


## Some notes:
 * The bootstrap is executed by having its opcode (75) in the second byte of the first word. This allows for you to set sp, cpp, lv, and pc respectively in the next 4 words. 
 * Currently lv is set at 0x100 and our gcd program uses the values stored in offsets 1 and 2. The result is stored in offset 3. It should take ~20 seconds to run and can be run at any speed.



