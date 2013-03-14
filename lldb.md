View registers
--------------

    (lldb) register read --format binary
    (lldb) register read rbp --format decimal

View current instructions/step-through
--------------------------------------

    (lldb) disassemble
    sandbox`main + 11 at main.c:6:
    -> 0x100000f5b:  movl   $8, -8(%rbp)
       0x100000f62:  movl   $6, -12(%rbp)
       0x100000f69:  movl   -8(%rbp), %eax
       0x100000f6c:  addl   -12(%rbp), %eax

    (lldb) thread step-inst


View the stack
--------------

Note stack is growing down, hence -64.

    (lldb) register read rbp --format hex
         rbp = 0x00007fff5fbff820
    (lldb) memory read --size `sizeof(int)` --format x --count 16 `0x00007fff5fbff820-64`

Find the code section and disassemble
-------------------------------------

Note that 'sandbox' is a string matching project name.

    (lldb) target modules dump sections sandbox
    Sections for '/Users/ahorne/Library/Developer/Xcode/DerivedData/sandbox-bfzibxhizuhggjglkcnupiofkaks/Build/Products/Debug/sandbox' (x86_64):
      SectID     Type             Load Address                             File Off.  File Size  Flags      Section Name
      ---------- ---------------- ---------------------------------------  ---------- ---------- ---------- ----------------------------
      0x00000100 container        [0x0000000000000000-0x0000000100000000)* 0x00000000 0x00000000 0x00000000 sandbox.__PAGEZERO
      0x00000200 container        [0x0000000100000000-0x0000000100001000)  0x00000000 0x00001000 0x00000000 sandbox.__TEXT
      0x00000001 code             [0x0000000100000f50-0x0000000100000f71)  0x00000f50 0x00000021 0x80000400 sandbox.__TEXT.__text
      0x00000002 code             [0x0000000100000f71-0x0000000100000fb9)  0x00000f71 0x00000048 0x00000000 sandbox.__TEXT.__unwind_info
      0x00000003 eh-frame         [0x0000000100000fc0-0x0000000100001000)  0x00000fc0 0x00000040 0x00000000 sandbox.__TEXT.__eh_frame
      0x00000300 container        [0x0000000100001000-0x0000000100002000)  0x00001000 0x0000023c 0x00000000 sandbox.__LINKEDIT

    (lldb) memory read --size `sizeof(int)` --format x --count 16 0x0000000100000f50
    0x100000f50: 0xe5894855 0x00fc45c7 0xc7000000 0x0008f845
    0x100000f60: 0x45c70000 0x000006f4 0xf8458b00 0x5df44503
    0x100000f70: 0x000001c3 0x00001c00 0x00000000 0x00001c00
    0x100000f80: 0x00000000 0x00001c00 0x00000200 0x000f5000
    
    (lldb) di -s 0x100000f50
    sandbox`main at main.c:2:
       0x100000f50:  pushq  %rbp
       0x100000f51:  movq   %rsp, %rbp
       0x100000f54:  movl   $0, -4(%rbp)
    -> 0x100000f5b:  movl   $8, -8(%rbp)
       0x100000f62:  movl   $6, -12(%rbp)
       0x100000f69:  movl   -8(%rbp), %eax
       0x100000f6c:  addl   -12(%rbp), %eax
       0x100000f6f:  popq   %rbp

Dump the symbol table
---------------------

    (lldb) image dump symtab sandbox
    ...
    [    2]      4 D   Code         0x0000000100000f50 0x0000000100000f50 0x0000000000000021 0x000f0000 main
    ...

Viewing variables in current frame
-------------------------------

    //Locals
    (lldb) frame variable

    //Globals
    (lldb) local variable

View a backtrace
----------------

    (lldb) thread backtrace

Disassembly
-----------

    //Hybrid mode (C+asm)
    (lldb) di -m

    //Current frame
    (lldb) di -f

    //Current line
    (lldb) di -l

