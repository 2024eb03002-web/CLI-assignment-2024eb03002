Question 1
You have just joined IxD Systems as a junior systems engineer. On your first day, the Linux administrator asks you to perform a basic environment verification on the lab machine using your own login account.

1. User Identity Verification
   Display your currently logged-in username and all groups your user account belongs to.
   Your name or login ID must appear in the output.
i used the command the id to display all groups my user account belomgs to, along with my unique user id
command:-id
output:-uid=1000(jelly) gid=1000(jelly) groups=1000(jelly),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users)

<img width="1581" height="58" alt="Screenshot 2026-01-02 000650" src="https://github.com/user-attachments/assets/e23c7617-c6f5-49e8-bce9-80ab6c0b8571" />



2. Workspace Validation
Display the current working directory and list all files and directories in that location using long format listing.
i used the command pwd to show the preset working directory.
then i proceeded to use the command ls -l. which prompted the directories in that location along with long format listing. the -l command is added to ask for the long form of the listing. 
command:-pwd 
output:-/home/jelly/CLI-assignment-2024eb03002
command:-ls -l

<img width="880" height="258" alt="Screenshot 2026-01-02 000900" src="https://github.com/user-attachments/assets/97aa6851-a0e8-4053-93c6-74115cead5dc" />


3. Environment Confirmation File
Create a file named user_info.txt and write the line:
&quot;Linux user environment verified&quot;
i used the command echo which prints text to the terminal and redirected it to the file info_text.txt.
Linux creates a new file and adds the text to the file. 
command:- echo "Linux user environment verified"> user_info.txt
to verify, 
command;-cat user_info.txt
output:-Linux user environment verified

<img width="1416" height="88" alt="Screenshot 2026-01-02 001437" src="https://github.com/user-attachments/assets/b5e9584c-ae0e-4554-9e31-2be8dbede63c" />

4. File Integrity Check
Display the number of characters present in user_info.txt.
the command wc -c was used. wc stands for word count.
by using the -c flag, we instruct the linux terminal to count only the characters in the file. 
command:- wc -c user_info.txt
output:-32 user_info.txt

<img width="1095" height="51" alt="Screenshot 2026-01-02 001448" src="https://github.com/user-attachments/assets/8cff76b9-79ec-43f1-b3fd-5be22665b3b1" />


5. Learning the Tools
Access the manual page of the mkdir command. Identify one useful option and briefly explain what it does.
i used the command man to access the manual page of the mkdir command.
this resulted in the manual page of mkdir opening up. mkdir is used to make directories. through the man command i was able to learn about the mkdir command properly. 
command:- man mkdir

<img width="803" height="32" alt="Screenshot 2026-01-02 001627" src="https://github.com/user-attachments/assets/5a3bcec2-230f-4f91-878e-64a2cec30cda" />

<img width="1846" height="880" alt="Screenshot 2026-01-02 001602" src="https://github.com/user-attachments/assets/5815c23b-9a83-4462-907a-c1f776b33edc" />


6. Home Directory Inspection
List the contents of your home directory sorted alphabetically.
i used the ld ~ command to inspect my home directory. 
command:- ls ~
CLI-assignment-2024eb03002

<img width="755" height="57" alt="Screenshot 2026-01-02 001703" src="https://github.com/user-attachments/assets/3a86f6d5-16cd-4559-8f99-0d1971141d74" />


7. Log Investigation
Search for the word &quot;admin&quot; inside a file named log.txt and display only the matching lines.
i first made a file known as log.txt and filled it with a sentence.
grep is a powerful tool, through its utilization, i was able to clearly scan the file line-by-line and only display the lines that contain the specific word. 
command:- grep "admin" log.txt
output:- this is an admin file
<img width="1276" height="84" alt="Screenshot 2026-01-02 001831" src="https://github.com/user-attachments/assets/6a1e1471-07fa-47c5-acd6-8988b83cd38c" />


8. System Information Check
Display the Linux kernel version currently running.
the uname command provides system information. the -r flag specifically asks for the kernel release version. 
command:-uname -r
output:-6.6.87.2-microsoft-standard-WSL2
<img width="835" height="61" alt="Screenshot 2026-01-02 001920" src="https://github.com/user-attachments/assets/89756511-53bb-41fb-a5d9-fbf8b4546baa" />


9. Network Connectivity Test
Verify network connectivity by sending ICMP packets to www.google.com.
the ping command sends ICMP Echo Request packets to a server. If the server "replies" back, we know the internet connection is working and that the server is online. 
command:- ping -c 4 www.google.com
output:- PING www.google.com (142.251.221.100) 56(84) bytes of data.
64 bytes from cgk03s03-in-f4.1e100.net (142.251.221.100): icmp_seq=1 ttl=117 time=96.8 ms
64 bytes from cgk03s03-in-f4.1e100.net (142.251.221.100): icmp_seq=2 ttl=117 time=467 ms
64 bytes from cgk03s03-in-f4.1e100.net (142.251.221.100): icmp_seq=3 ttl=117 time=169 ms
64 bytes from cgk03s03-in-f4.1e100.net (142.251.221.100): icmp_seq=4 ttl=117 time=81.4 ms

--- www.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 81.446/203.479/466.639/155.488 ms
<img width="1304" height="279" alt="Screenshot 2026-01-02 001952" src="https://github.com/user-attachments/assets/c142c828-1e8b-407a-a3c7-3c5e220ba58b" />


10. System Health Awareness
Display the command used to check system uptime and briefly explain its output (uptime duration, number of users, load average).
this provides a snapshot of how hard the system is working.
the three numbers of load average represent the system demand over the last 5, 10, 15 minutes. 
 command:-uptime
 output:-18:50:22 up 21 min,  1 user,  load average: 0.04, 0.01, 0.00
<img width="936" height="57" alt="Screenshot 2026-01-02 002102" src="https://github.com/user-attachments/assets/3a058f57-b833-4236-9217-3907b0fe2339" />



