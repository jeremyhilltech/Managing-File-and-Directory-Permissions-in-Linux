<p align="center">
<a href="https://i.imgur.com/yq1dpRx.png"><img src="https://i.imgur.com/yq1dpRx.png" title="tux" /></a>
</p>

# Managing File and Directory Permissions in Linux
This lab serves as an exploration of permissions on directories and files within Linux. We will check permissions to ensure that each is properly configured for their respective user, group, or other owners. The point here is to get a taste of the Principle of Least Privilege, which states that only the minimum amount of access for files and directories should be granted for the completion of necessary tasks related to the use of the data. 

## Context:

For a list of commands used in this lab, please see the end of the lab. For more information on these commands and their options, please refer to the 'man' page for each of them inside your linux bash shell. 

## Scenario:
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

---
## Check File and Directory Details

<a href="https://imgur.com/8s6z6U2"><img src="https://i.imgur.com/8s6z6U2.jpg" title="LC1.1" /></a>

1. We begin by establishing who we are using the `whoami` command, which returns that we are `researcher2`. 
2. Next we need to know where we are, so we use the `pwd` command, which returns our working directory as `/home/researcher2`. 
3. We will be working in the projects directory, which we locate using the `ls -a` command to confirm its presence from our current working directory. 
4. We then use the `cd projects` command to drop into that location. 
5. Our instructions are to enumerate all of the files and directories within the projects directory and investigate permissions on several files. Here we see the returned information from the system using the `ls -la` command in order to include any hidden files in our current working directory. Below is the result, where we can see all permissions. 

<a href="https://imgur.com/rdtmKvG"><img src="https://i.imgur.com/rdtmKvG.jpg" title="LC1.2" /></a>

---
## Describe the permissions string

In the above image note that there is a series of 10 character strings that begin each line. These are permission strings, and they tell us what permissions are enabled on the given file or directory, as well as who has been given these levels of access. 

In this section, we’ll first discuss the possible characters and what each means. Next we'll discuss the types of owners of files in linux, and then we will tie that into the permissions string so we can use it as a tool to understand what the permissions are on file and directories. 

As you may note on observation, each string consists of a series of letters or hyphens. The characters used are as follows:

* A `d` at the beginning of a string represents the permissions for a directory
* A `-` (hyphen) at the beginning of a string represents the permissions for a file. If located within the string, the hyphen means that the permission has been revoked. 
* An `r` means that `read` permissions are granted. 
* A `w` means that `write` permissions are granted.
* An `x` means that `execute` permissions are granted. 

Next let’s observe that there are three types of owners in Linux:

* User - the owner or creator of the file. 
* Group - every user is part of some type of group. 
* Other - this is considered to be all other users on the system. 

From here we tie all of this information to the string itself. A useful way of conceptualizing these strings is to think of them as 1 + 3 + 3 + 3. In this case, position 1 represents whether we are talking about a directory or  file (d or - respectively), and the rest are “triplets” which pertain to one of three types of owners, that is users, groups, and others. 
If all permissions were enabled for everyone, that would end up looking like: `-rwxrwxrwx`

In the example `-rwxrwxrwx`, the hyphen in position 1 tells us we’re working with the permissions of a file. The first “triplet” of characters represent user permissions, the second triplet represents group permissions, and the last triplet represents other permissions. Now let’s take a look at our results again: 

<a href="https://imgur.com/bxGt1Ox"><img src="https://i.imgur.com/bxGt1Ox.jpg" title="LC1.2" /></a>

If we take a look at the drafts directory, we see the permissions: `drwx--x---`
Read from left to right, we confirm we’re working with a directory (d). We can see that users have read, write, and execute privileges, groups only have execute privileges, and others have no privileges. 

---
## Changing File Permissions

Now that we understand what we’re looking at, we’re going to change the permissions on one of these files. In order to do this, we’re going to use the `chmod` command, which will require that we first enter which permissions we want to edit, and specify the file or directory in which to implement those changes. Let’s learn how to do that first. 

When using `chmod`, we tie which type of owner with a `+` or `-` to whether we are adding or removing the permissions from them. We then insert the file or directory we are making the changes to. 

Consider the following: `chmod g+w,o-r access.txt`

Using `chmod` we must take into consideration that `u` = user, `g` = group, and `o` = others. As you’d expect, it follows that `r` =  read, `w` = write, and `x` = execute. Knowing this, we can deduce that this command is telling `chmod` to give group the write permission, and to remove others from the read permission on this file. Said in a more literally, it might read this way: “chmod group add write, others remove read access.txt file.” While this isn’t correct, it gives you an idea of the instruction you’re giving the computer. Please note that for each permission you edit, you must insert a comma between each set of changes, and you ***cannot*** put a space after the commas. Now that we understand `chmod`, let’s look at our files again. 

Let’s say that our organization does not allow others to have write access to *any* files. If we look closely, we can see that project_k.txt is currently configured incorrectly. To fix this, we’ll use the `chmod` command to alter the permissions for others on this file. 

<a href="https://imgur.com/3IbrWEp"><img src="https://i.imgur.com/3IbrWEp.jpg" title="source: imgur.com" /></a>










