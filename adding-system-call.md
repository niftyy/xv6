
# Adding SystemCalls

* Add Systemcall to syscall.h
* Add prototype to defs.h
* Add prototype to user.h
* Add sys_syscall(void) definition to sysproc.c
* Add SYSCALL(syscall) to usys.S
* Add extern int sys_syscall(void) to syscall.c
* Add [SYS_syscall]     sys_syscall to syscall.c
* Add syscall() definition to proc.c
* Create a C file with the desired command name and call the systemcall there as follows - 
```C
#include "types.h"
#include "stat.h"
#include "user.h"
#include "fcntl.h"

int
main(int argc, char *argv[])
{
    cps();
    exit();
}
```
* Finally update makefile for your newly created C file by adding the filename at UPROGS and EXTRAS respectively