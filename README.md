# Managing-Permissions-in-Linux
This lab serves as an exploration of permissions on directories and files within Linux. We will check permissions to ensure that each is properly configured for their respective user, group, or other owners. The point here is to get a taste of the Principle of Least Privilege, which states that only the minimum amount of access for files and directories should be granted for the completion of necessary tasks related to the use of the data. 

## Context:

For a list of commands used in this lab, please see the end of the lab. For more information on these commands and their options, please refer to the 'man' page for each of them inside your linux bash shell. 

## Scenario:
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

---
## Check File and Directory Details

<img src="https://imgur.com/n7Aj3yK" alt="LC1.1"/>

1. We begin by establishing who we are using the whoami command, which returns that we are researcher2. 
2. Next we need to know where we are, so we use the pwd command, which returns our working directory as /home/researcher2. 
3. We will be working in the projects directory, which we locate using the ls -a command to confirm its presence from our current working directory. 
4. We then use the cd projects command to drop into that location. 
5. Our instructions are to enumerate all of the files and directories within the projects and investigate permissions on several files. Here we see the returned information from the system using the ls -la command in order to include any hidden files in our current working directory. Below is the result, where we will dive into permissions. 
