---

##  WEEK ASSIGNMENT

### *1️⃣ User & Group Management*
- Learn about Linux *users, groups, and permissions* (/etc/passwd, /etc/group).

- *Users*
A user in Linux is an account that can log in and interact with the system.Each user has a unique username and a User ID (UID).Users can own files and run programs.

- *Groups*
A group is a collection of users.Groups make it easier to manage permissions for multiple users at once.Each group has a unique Group Name and a Group ID (GID).A user can belong to one primary group and multiple secondary groups.

- *Permissions*
Permissions control what users and groups can do with files and directories.

Every file and directory has three types of permissions:

1.Read (r): View the contents of a file or list files in a directory.

2.Write (w): Modify a file or add/remove files in a directory.

3.Execute (x): Run a file as a program or enter a directory.

- *Task:*
  - Create a user devops_user and add them to a group devops_team.
  - Set a password and grant *sudo* access.
  - Restrict SSH login for certain users in /etc/ssh/sshd_config.

1. Create the user and add to group:
sudo useradd -m -g devops_team devops_user

*Explanation:*

useradd: Creates a new user account.
-m: Creates a home directory for the user.
-g devops_team: Assigns the user to the "devops_team" group.
2. Set a password for the user:
sudo passwd devops_user
*Explanation:*
passwd: Prompts you to enter a new password for the specified user.
3. Grant sudo access:
sudo usermod -aG sudo devops_user
*Explanation:*
usermod: Modifies an existing user account.
-aG sudo: Adds the user to the "sudo" group, allowing them to execute commands with root privileges.
4. Restrict SSH login for specific users (in /etc/ssh/sshd_config):
Edit the file:
sudo nano /etc/ssh/sshd_config
Add the following line to restrict access:
DenyUsers user1 user2 user3
*Explanation:*
DenyUsers: Specifies a list of usernames that are explicitly denied SSH access.
Restart the SSH service to apply changes:
sudo systemctl restart sshd
---
