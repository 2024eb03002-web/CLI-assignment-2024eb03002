Question 3 [5 points]

You have been asked to understand how Linux manages files using links and disk usage information.As part of your role, you will perform the following operations within your own user space.

1. File Creation

Create a file named sample_data.txt in your home directory and add some sample text to it.

used the echo command to display text and the > command to redirect it to the file sample_data.txt

    echo "Sample text for testing links">sample_data.txt

 <img width="1112" height="31" alt="Screenshot 2026-01-02 121930" src="https://github.com/user-attachments/assets/e2820a1c-b3ef-43c6-b58b-84bbad890226" />



2. Hard Link Creation

Create a hard link to sample_data.txt named sample_hard.txt.

a hard link is a direct pointer to the data on a physical disk. It doesn't create a copy of the data. By using ln command, i was able to create such a hard link for the sample file

    ln sample_data.txt sample_hard.txt

<img width="988" height="30" alt="Screenshot 2026-01-02 121939" src="https://github.com/user-attachments/assets/ffbf088a-8c7d-481d-9a56-4de41726a3cd" />


3. Symbolic Link Creation

Create a symbolic (soft) link to sample_data.txt named sample_soft.txt.

A soft link is like a shortcut in widnows. It is a separate tiny file that contains the text path to the original file. 
to create this soft link, i utilised the ln -s command.

    ln -s sample_data.txt sample_soft.txt

<img width="786" height="36" alt="Screenshot 2026-01-02 122028" src="https://github.com/user-attachments/assets/4a7f1d6a-7998-4065-9da1-d2dd15c418e2" />


4. Inode Verification

Display the inode numbers of sample_data.txt, sample_hard.txt, and sample_soft.txt.

the -i flag reveals the inode number. An inode is a unique id for the physical data stores in the disk.

    ls -i sample_data.txt sample_hard.txt sample_soft.

  output:- 46492 sample_data.txt  46492 sample_hard.txt  46493 sample_soft.txt

<img width="1018" height="62" alt="Screenshot 2026-01-02 122041" src="https://github.com/user-attachments/assets/e322eed6-d445-4d54-85d2-4708c945f4dd" />


5. Inode Analysis

Identify which files share the same inode number and briefly explain the reason.

the files sample_data.txt and sample_hard.txt share the same inode number of 46492. This occurse because they essentially create a second name for the same file.

the file sample_soft.txt shares a different inode number because they are a separate file themselves which contains the text path to the original file

6. File Metadata Inspection

Display detailed file information (permissions, ownership, size, timestamps) of sample_data.txt.

the stat command used orvides a much deeper look at file metadata. It shows exact timestamps.
i thus utilised this command for the file sample-data.txt

    stat sample_data.txt
    
output:- File: sample_data.txt
  Size: 30              Blocks: 8          IO Block: 4096   regular file
Device: 8,48    Inode: 46492       Links: 2
Access: (0644/-rw-r--r--)  Uid: ( 1000/   jelly)   Gid: ( 1000/   jelly)
Access: 2026-01-01 19:19:01.382051160 +0000
Modify: 2026-01-02 06:46:11.859110157 +0000
Change: 2026-01-02 06:46:11.859110157 +0000
 Birth: 2026-01-01 19:19:01.382051160 +0000

<img width="1150" height="256" alt="Screenshot 2026-01-02 122050" src="https://github.com/user-attachments/assets/8d4b74bf-debc-40d8-b369-fc5f1e751e56" />


7. Disk Usage Check

Display the disk usage of your home directory in a human-readable format.

the du command calculates the size of files and directories.
the -s flag is the summary flag that only shows the total size of the folder, not every file inside,
the -h flag is the human readable flag that converts bytes into readable formats like KB

     du -sh ~
     
  output:- 292K    /home/jelly

<img width="546" height="64" alt="Screenshot 2026-01-02 122059" src="https://github.com/user-attachments/assets/702bc838-1c1d-44a6-a0ab-67f2d0580356" />


8. File Size Overview

Display the size of each file present in your home directory in a human-readable format.

i utilised the command ls -lh, it shows the logical size of the file in a list format. 
the -lh flag used gives us the long and human readable version.

      ls -lh
      
output:- total 12K
drwxr-xr-x 8 jelly jelly 4.0K Jan  1 19:47 CLI-assignment-2024eb03002
-rw-r--r-- 2 jelly jelly   30 Jan  2 06:46 sample_data.txt
-rw-r--r-- 2 jelly jelly   30 Jan  2 06:46 sample_hard.txt
lrwxrwxrwx 1 jelly jelly   27 Jan  1 19:21 sample_soft.txt -> /home/jelly/sample_data.txt
<img width="1278" height="176" alt="Screenshot 2026-01-02 122109" src="https://github.com/user-attachments/assets/29ebbbb4-f4f4-49b9-816b-a6b1eb52d81a" />


9. Link Deletion Test

Delete the symbolic link sample_soft.txt and verify that the original file sample_data.txt is  unaffected.

the rm command deletes the sample_soft.txt which serves as a soft link
by utilising the ls command we are able to view if the original file has been affected, it hasn't.
this in turn proves that the soft link is just a pointer and doesn't affect the file.

    rm sample_soft.txt
    ls -l sample_data.txt
    
output:- -rw-r--r-- 2 jelly jelly 30 Jan  2 06:46 sample_data.txt

<img width="1156" height="89" alt="Screenshot 2026-01-02 122123" src="https://github.com/user-attachments/assets/7c7451b5-0fe9-4aeb-a331-2137aa8d4a8b" />


10. Disk Utility Demonstration

Demonstrate the usage of du and df commands using various useful options and briefly explain the output.

the df command (disk free) reports on the entire filesystem. It shows how much total space is available on the hard drive partitions, which is vital for system admins to ensure the server doesn't run out of storage. 

    df -h
    
output:- Filesystem      Size  Used Avail Use% Mounted on
none            3.8G     0  3.8G   0% /usr/lib/modules/6.6.87.2-microsoft-standard-WSL2
none            3.8G  4.0K  3.8G   1% /mnt/wsl
drivers         476G   93G  383G  20% /usr/lib/wsl/drivers
/dev/sdd       1007G  1.5G  955G   1% /
none            3.8G  132K  3.8G   1% /mnt/wslg
none            3.8G     0  3.8G   0% /usr/lib/wsl/lib
rootfs          3.8G  2.7M  3.8G   1% /init
none            3.8G  536K  3.8G   1% /run
none            3.8G     0  3.8G   0% /run/lock
none            3.8G     0  3.8G   0% /run/shm
none            3.8G   76K  3.8G   1% /mnt/wslg/versions.txt
none            3.8G   76K  3.8G   1% /mnt/wslg/doc
C:\             476G   93G  383G  20% /mnt/c
tmpfs           778M   20K  778M   1% /run/user/1000

the du(disk usage) command calculates the size of files and directories. 
i paired it with the -sh flag to show a human readable summary of this disk usage which is occuring. 

    du -sh .
    
output:- 292K    .


<img width="1386" height="452" alt="Screenshot 2026-01-02 122133" src="https://github.com/user-attachments/assets/0e15b405-2e34-47f2-9616-5c60de41ce25" />

<img width="558" height="60" alt="Screenshot 2026-01-02 122141" src="https://github.com/user-attachments/assets/6c59e8f9-d83f-4b4a-8228-73c5578c4cc1" />

