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
          
2.  How processes are created and managed
   -  Process is a running instance of a program which has PID, PPID, state and memory usage.
   -  How process are created:
        -   A process creates another process using fork()
        -   The child process gets a new PID
        -   Often followed by exec() to run a new program
   -   Process States
        -   Running (R): current using CPU
        -   Sleeping (S): Waiting for something (I/O, input)
        -   Stopping(T): Suspended
        -   Zombie (Z): Finished execution but parent hasn't cleaned it
        -   orphan - Parent died before child
       
3.  What systemd does and why it matters
   -   Th systemd starts service at boot, restart failed services, manges service dependencies, collects logs, handled targets (like runlevels)
   -   The systemd can auto-restart crashed services, makes troubleshooting easier, centralized logs using journalctl, and it is used in almost all modern Linux distros.

4. 5 Commands
   -   ps: view running process
     <img width="383" height="57" alt="Screenshot from 2026-02-13 16-03-41" src="https://github.com/user-attachments/assets/6a69795e-773f-4b70-9289-2d431532bbc4" />

   -   htop or top: Monitor CPU and memory usage
   -   systemctl status --servicename--: check service status
   <img width="1115" height="425" alt="image" src="https://github.com/user-attachments/assets/ed2c0ed6-e3e8-4463-a898-697b93564d12" />

   -   jourmalctl: view system logs
   -   kill --PID--: kill the process 
