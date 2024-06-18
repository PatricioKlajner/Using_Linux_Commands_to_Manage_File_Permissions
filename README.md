<h1>Using Linux Commands to Manage File Permissions</h1>

<h2>Description</h2>
In this project, I will use Linux commands to configure authorization. The research team at my organization needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. I will check the permissions for all files in the directory, including any hidden files, to make sure that permissions align with the authorization that should be given. If they do not align, I will modify the permissions to authorize the appropriate users and remove any unauthorized access. Checking and updating these permissions will help keep their system secure.

<h2>Project Walkthrough</h2>

<h3>Checking File and Directory Details</h3>
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.

<p align="center">
<img src="https://i.imgur.com/pmMOzNl.png" height="70%" width="70%" alt="Linux 1"/> </p>

The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the projects directory. I used the ls command with the -la option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named drafts, one hidden file named .project_x.txt, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory. 

<h3>Describing the Permissions String</h3>
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
<br />
<br />
<strong>1st Character: </strong> This character indicates the file type. The character can either be a d or a hyphen (-). If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
<br />
<br />
<strong>2nd-4th Characters: </strong> These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
<br />
<br />
<strong>5th-7th Characters: </strong>These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the group.
<br />
<br />
<strong>8th-10th Characters: </strong> These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.
<br />
<br />
For example, the file permissions for project_k.txt are -rw-rw-rw-. Since the first character is a hyphen (-), this indicates that project_k.txt is a file, not a directory. The second, fifth, and eighth characters are all r, which indicates that user, group, and other all have read permissions. The third, sixth, and ninth characters are w, which indicates that user, group, and other all have write permissions. The fourth, seventh, and tenth characters are all hyphen (-), which indicates that no one has execute permissions for project_k.txt.

<h3>Changing File Permissions</h3>
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined project_k.txt must have the write access removed for other.
<br />
<br />
The following code demonstrates how I used Linux commands to do this:
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/ikocxq3.png" height="70%" width="70%" alt="Linux 2"/> </p>

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The chmod command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other (o-w) for the project_k.txt file. After this, I used ls -la to review the updates I made.

<h3>Changing File Permissions on a Hidden File</h3>
The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access.
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions:
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/StB3HOk.png" height="70%" width="70%" alt="Linux 3"/> </p>

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r.

<h3>Changing Directory Permissions</h3>
My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions:
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/6Y8dM8U.png" height="70%" width="70%" alt="Linux 4"/> </p>

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. In this example, I used the chmod command to remove execute permissions from the group with g-x. The researcher2 user already had execute permissions, so they did not need to be added. In the output, we can see that line 4 is the directory (drafts) with restricted permissions and that only researcher2 has execute permissions.

<h2>Summary</h2>
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.
