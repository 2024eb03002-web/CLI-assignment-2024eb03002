Question 2 

You are working as a junior system administrator responsible for organizing project- related files in your home directory.
Your supervisor wants you to demonstrate your understanding of Linux file and directory management commands.

1. Project Workspace Setup

Create a directory named documents inside your home directory. This directory will store your project-related files.

through the usage of nested directory concept, i utilised the mkdir command to make a directory in the CLI-assignment directory.

command:-mkdir CLI-assignment-2024eb03002/documents

<img width="1273" height="28" alt="Screenshot 2026-01-02 003003" src="https://github.com/user-attachments/assets/028af1dc-21e5-4dda-8aa3-6e0ba85ce4ec" />


2. File Creation

Navigate into the documents directory and create a file named plan.txt.

because of my use of nested directories, i used cd command to first enter the parent directory, then the documents directory. 
after that, i used the touch command to create an empty file. 

command:- cd ~/CLI-assignment-2024eb03002
cd documents
touch plan.txt


<img width="1073" height="62" alt="Screenshot 2026-01-02 003230" src="https://github.com/user-attachments/assets/b2b41c54-d0d7-4d12-9036-d4616ca20d9b" />


3. Content Addition

Write some sample text of your choice into the plan.txt file. The content can be a short project note or reminder.

echo command usually displays text on screen, by utilising the > command, we are able to redirect the text into a txt file. 

command:-echo "This is a project plan for the system upgrade"> plan.txt
 cat plan.txt
 
output:- This is a project plan for the system upgrade



<img width="1657" height="87" alt="Screenshot 2026-01-02 003347" src="https://github.com/user-attachments/assets/de2df4b0-7a03-4393-8731-38bc26fecb66" />


4. File Metadata Verification

Display the permissions and ownership details of the plan.txt file. Ensure your username appears in the output.

ls -l is a command that shows the listing. -l acts as a command to show the long version of the listing which the question requested. 

command:- ls -l plan.txt

output:- -rw-r--r-- 1 jelly jelly 46 Jan  1 19:03 plan.txt


<img width="1039" height="62" alt="Screenshot 2026-01-02 003532" src="https://github.com/user-attachments/assets/a04bae36-6478-49e2-95d0-fb16d3322fe0" />


5. File Duplication

Create a copy of plan.txt and name it plan_copy.txt.

cp command makes a physical duplicate of the data. After this, we have two separate files. 

command:- cp plan.txt plan_copy.txt

<img width="1168" height="90" alt="Screenshot 2026-01-02 003635" src="https://github.com/user-attachments/assets/d4110a05-7d7b-4b2f-8e3d-a0875a2fa8f9" />


6. Directory Renaming

Rename the documents directory to project_documents to reflect the project scope more clearly.

i first exited from the directory to be able to rename it. this was achieved through the cd .. command which helps me go back by one directory. I then utilised the mv command which can be used to rename the directory. 

commands:- cd ..

 mv documents project_documents


<img width="1270" height="52" alt="Screenshot 2026-01-02 004351" src="https://github.com/user-attachments/assets/1e1b8f6d-fdd2-405e-8618-39a1071d3348" />


7. Archival Structure

Inside the project_documents directory, create a subdirectory named archive.

to make a nested directory/file, i utilised the mkdir command. Since my project_documents directory was already a nested directory, i went back to home directory, then used double nesting to create the archive directory inside the project-documents one.

command:- mkdir CLI-assignment-2024eb03002/project_documents/archive

<img width="1172" height="47" alt="Screenshot 2026-01-02 004417" src="https://github.com/user-attachments/assets/70e3d1c4-3160-4016-bad5-85b6c4a789db" />


8. File Organization

Move plan_copy.txt into the archive subdirectory.

to move the plan_copy.txt file, i utilised the mv command. This command helped me move directories, since my directories were nested, i had to specify the path to specify the location. 

command:- mv CLI-assignment-2024eb03002/project_documents/plan_copy.txt CLI-assignment-2024eb03002/project_documents/archive

<img width="1859" height="34" alt="Screenshot 2026-01-02 004500" src="https://github.com/user-attachments/assets/60d170fb-db51-4e42-b71f-aa6b638fbdbd" />


9. Recursive Listing

List all files and subdirectories inside project_documents recursively so that the complete directory structure is visible.

i utilised the ls -R command. the -R stands for recursive. It lists the current folder then dives into every sub folder. 

command:- s -R CLI-assignment-2024eb03002/project_documents

output:- CLI-assignment-2024eb03002/project_documents:
         archive  plan.txt

          CLI-assignment-2024eb03002/project_documents/archive:
          plan_copy.txt


<img width="1147" height="176" alt="Screenshot 2026-01-02 004538" src="https://github.com/user-attachments/assets/dd676dbf-21ae-4296-866d-ba863f81dff3" />


10. Path Verification

Display the absolute path of the plan_copy.txt file after it has been moved to the archive directory.

i utilised the readlink -f command. the -f flag tells the system to resolve the full canonical path. It ignores where i am currently and gives the path starting from the root. 

command:- readlink -f CLI-assignment-2024eb03002/project_documents/archive/plan_copy.txt

output:- /home/jelly/CLI-assignment-2024eb03002/project_documents/archive/plan_copy.txt

<img width="1419" height="59" alt="Screenshot 2026-01-02 004653" src="https://github.com/user-attachments/assets/5e810d4f-e557-4820-8485-6ff48cdf5c61" />


