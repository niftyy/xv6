
# Adding SystemCalls

* Add Systemcall to syscall.h
* Add prototype to defs.h at PAGEBREAK: 16
* Add prototype to user.h 
* Add sys_syscall(void) definition to sysproc.c
* Add SYSCALL(syscall) to usys.S
* Add extern int sys_syscall(void) to syscall.c
* Add [SYS_syscall]     sys_syscall to syscall.c
* Add syscall() definition to proc.c for example-
```C
// inside proc.c
int 
cps()
{
  struct proc *p;

  // Enable interrupts on this processor.
  sti();

  // loop over process table looking for process with pid.
  acquire(&ptable.lock);
  cprintf("name \t pid \t state \t \n");
  int count = 0;
  for(p=ptable.proc; p<&ptable.proc[NPROC]; p++){
    if(p->state == SLEEPING){
      count++;
      cprintf("%s \t %d \t SLEEPING \t \n", p->name, p->pid);
    }
    else if(p->state == RUNNING){
      count++;
      cprintf("%s \t %d \t RUNNING \t \n", p->name, p->pid);
    }
    else if(p->state == RUNNABLE){
      count++;
      cprintf("%s \t %d \t RUNNABLE \t \n", p->name, p->pid);
    }
  }
  cprintf("Number of processes: %d\n", count);
  release(&ptable.lock);

  return 22;  // has to be same as at syscall.h
}
```
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