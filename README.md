## To rollback the firmware of your 4650 printer

start ollydbg2 as admin
load the EnterpriseDU.exe executable.

assuming a pe base address of 0x00FE0000

place a breakpoint on 0xfe5613
run the program until it hits.
run again to let it search for your usb connected printer.
replace the byte at ESI+2AE from 0 to 1.

place a breakpoint on 0xfe8cc5
run the program until it hits.
change ecx to 1 (from maybe 9 or 8 or whatever origninally)

place breakpoint on 0xff6bb4
run the program until it hits.
change arg1 on the stack to point to the name of the .ful firmware file. You might have to do a unicode search around the original ptr for the file.
Not sure why this is wrong as is.

execute and enjoy!

