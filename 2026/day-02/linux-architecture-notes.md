# Day 02 – Linux Architecture, Processes, and systemd

1. The core components of Linux (kernel, user space, init/systemd)
   -  Kernel:
       -  It is a heart of Linux which directly interact with hardware(CPU, RAM, disk).
       -  Its responsibilities are: Process management, Memory management, Device drivers, File systems, Networking.
   -  User Space:
       -  The is the space where user application(ngnix, Bash, Docker, Vim) actually runs.
       -  Application can not access hardware directly, they request resources from the kernel using system calls.
   -  Init/Sysemd
       -  This is the first process started by kernel and it has PID 1.
       -  it is used for starting the services, managing background processes and handling system boot.
          
3.  How processes are created and managed
4.  What systemd does and why it matters
