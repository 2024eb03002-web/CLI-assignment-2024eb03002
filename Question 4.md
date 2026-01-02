Question 4 

You must perform all operations without making any configuration changes to the system.

These tasks should be executed within your own user account. Since uptime, processes, memory usage,disk usage, and background jobs vary across systems and users, each student’s output will be unique.

1. System Uptime Verification

Display the time elapsed since the system was last booted.

i utilised the uptime command which tells us how long a computer has been running. i proceeded to utilise the -p flag which makes the time easier to read by showing it in hours and minutes 

    command:- uptime -p

output:- up 1 hour, 9 minutes


<img width="853" height="57" alt="Screenshot 2026-01-02 011004" src="https://github.com/user-attachments/assets/a74d2ece-785e-434f-8d20-08905be0108d" />


2. User Process Listing

List all processes currently running under your user account.

the ps command is like a snapshot of what the computer is doing right now. using -u $user filters the list to showcase only the programs started by me aka the user acc. 

    command:-  ps -u $USER

output:- PID TTY          TIME CMD
    486 ?        00:00:00 systemd
    488 ?        00:00:00 (sd-pam)
    511 pts/1    00:00:00 bash
    607 pts/2    00:00:00 bash
    754 pts/2    00:00:00 ps



<img width="907" height="197" alt="Screenshot 2026-01-02 011044" src="https://github.com/user-attachments/assets/bb4baed9-fece-4db6-a8a6-921375b16041" />


3. CPU Usage Analysis

Identify the process that is consuming the highest CPU usage among your running processes.

the top command provides a real time, dynamic view of ur system's resources. It lists processes by how much brain power they are using, which helps me identify "zombie" processes or programs that are slowing down the computer.  

    command:- top -o %CPU -n 1 -b | head -n 20
     
top - 19:41:22 up  1:12,  1 user,  load average: 0.00, 0.00, 0.00
     Tasks:  24 total,   1 running,  23 sleeping,   0 stopped,   0 zombie
     %Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
     MiB Mem :   7775.2 total,   7278.0 free,    497.4 used,    150.0 buff/cache
     MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   7277.8 avail Mem

PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0   21772  12400   9328 S   0.0   0.2   0:00.59 systemd
      2 root      20   0    3120   1920   1920 S   0.0   0.0   0:00.03 init-sy+
      6 root      20   0    3136   1844   1792 S   0.0   0.0   0:00.00 init
     52 root      19  -1   50428  15616  14720 S   0.0   0.2   0:00.29 systemd+
    109 root      20   0   25268   6272   4864 S   0.0   0.1   0:00.13 systemd+
    119 systemd+  20   0   21456  11776   9856 S   0.0   0.1   0:00.09 systemd+
    123 systemd+  20   0   91024   7680   6912 S   0.0   0.1   0:00.14 systemd+
    184 root      20   0    4236   2304   2176 S   0.0   0.0   0:00.01 cron
    185 message+  20   0    9588   4608   4224 S   0.0   0.1   0:00.14 dbus-da+
    192 root      20   0   17960   8320   7424 S   0.0   0.1   0:00.10 systemd+
    195 root      20   0 1755840  12544  10240 S   0.0   0.2   0:00.22 wsl-pro+
    200 root      20   0    3160   1920   1792 S   0.0   0.0   0:00.00 agetty
    213 syslog    20   0  222508   5120   4352 S   0.0   0.1   0:00.11 rsyslogd


<img width="1423" height="598" alt="Screenshot 2026-01-02 011151" src="https://github.com/user-attachments/assets/af86c126-44e2-42df-88cf-a21e303704f6" />


4. Background Process Execution

Start a command in the background and verify that it is running.

in linux, adding an ampersand(&) to the end of the command tells the shell to run it in the background. 
using the jobs command, i verified if it was still active

    sleep 100 &
output -[2] 758

    jobs
output-[1]-  Running                 sleep 100 &
[2]+  Running                 sleep 100 &


<img width="1101" height="141" alt="Screenshot 2026-01-02 112403" src="https://github.com/user-attachments/assets/147b05e7-416f-4c03-a307-dc52310c7ae4" />



5. Process Priority Management

Change the priority (niceness) of one of your running processes and display the updated priority.

i first created a dummy command called sleep that ran in the background, next i found the PID for the command. after checking the current nice value
i used the renice command to change the priority of the running process,
by utilising the -p flag, we are able to see the current and old nice value. 

    sleep 1000 &
output:- [1] 3516

      ps -o pid,ni,comm -p 3516
output:-PID  NI COMMAND
   3516   0 sleep

    renice +10 -p 3516
output:- 3516 (process ID) old priority 0, new priority 10

<img width="1106" height="195" alt="Screenshot 2026-01-02 120029" src="https://github.com/user-attachments/assets/8ec1f0d8-1080-4a2c-810c-909614a69e0d" />


6. Memory Usage Monitoring

Display memory usage information in a human-readable format.

the free command checks the system's RAM and the -h flag used converts it into a human readable form. 

    free -h

output:-               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       500Mi       7.1Gi       3.5Mi       150Mi       7.1Gi
Swap:          2.0Gi          0B       2.0Gi
[2]+  Done                    sleep 100


<img width="1176" height="148" alt="Screenshot 2026-01-02 011539" src="https://github.com/user-attachments/assets/550a0782-504b-4139-9c81-ad90ce9db888" />


7. Disk Space Inspection

Display the disk space usage of the filesystem where your home directory resides.

df command checks entire hard drive partition. by utilising the -h flag, we convert it into a human readable format. the . tells it to specifically report on the disk where the current directory is loaded

    df -h .
    
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd       1007G  1.3G  955G   1% /


<img width="804" height="93" alt="Screenshot 2026-01-02 011623" src="https://github.com/user-attachments/assets/5453a273-078e-4275-8cec-7f00515447dd" />


8. Shell Identification

Display the name of the shell currently in use.

the shell is the environment where we type our commands. by pairing the echo commands which displays smth on screen with the $SHELL variable, which stores the path to our current command line interface, we are able to identify our shell. 

    echo $SHELL
output:- /bin/bash

<img width="815" height="55" alt="Screenshot 2026-01-02 011715" src="https://github.com/user-attachments/assets/f27208a3-cd33-4896-b44e-66a8949c263b" />


9. Output Redirection

Redirect the output of a system information command of your choice into a file named system_report.txt.

using the > redirection command, we catch the output of our choice and redirect to a specific file as specified

    uname -a > system_report.tx

<img width="1157" height="42" alt="Screenshot 2026-01-02 012052" src="https://github.com/user-attachments/assets/d74a4ff6-d8dd-4193-a198-f05409caafce" />


10. Disk Usage Visualization

Demonstrate the usage of the ncdu tool using appropriate options and briefly explain what it shows.

the ncdu tool is a useful tool which provides a clickable, navigable interface right in your terminal to help u find space hogs quickly.
using this tool, we can sort through alphabetically, delete files, open selected directory to explore any subdirectories etc. 

    ncdu 

 
<img width="719" height="37" alt="Screenshot 2026-01-02 115058" src="https://github.com/user-attachments/assets/2ebf8e52-58af-4d30-aa8a-f204af6de505" />

<img width="1519" height="405" alt="Screenshot 2026-01-02 115044" src="https://github.com/user-attachments/assets/dc669a17-46c9-4f01-af80-285ca637a641" />



