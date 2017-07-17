# linux-0.00

using linux-0.00-050613

## boot.s


## head.s

### head.s:59: Error: invalid instruction suffix for `pushf'

these codes were supposed to run in a 32-bits machine
but your computer is 64-bits

* add .code32 to the beginning of head.s

### head.s:106: Warning: using "%ebx" instead of "%bx" due to "l" suffix

since it's a 32-bits register command, you should

* change **"%bx"** to **"%ebx"**

### head.s:185: Error: alignment not a power of 2

.align is the indicator of assembly language
, which means align the border of memory address.  
Now GNU as uses the align value instead of power form.

* change **.align 2** to **.align 4**
* change **.align 3** to **.align 8**

### head.s:243: Error: "%al" not allowed with "movl"

al is an 8-bit register hence you cannot use movl.  

* change **movl** to **movb**

## Makefile

### make: gas: Command not found</br>

commands gas, gld were outdated, 
now the name of GNU assembler is as

* change **AS=gas** to **AS=as**  
* change **LD=gld** to **LD=ld**  


### ld: warning: cannot find entry symbol _start; defaulting to 0000000000400078 head.o: In function "startup_32":

cannot find entry symbol

* add **-Ttext 0 -e startup_32** to the end of ld

------


