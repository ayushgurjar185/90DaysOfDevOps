# Week 2: Linux System Administration & Automation

Welcome to **Week 2** of the **90 Days of DevOps - 2025 Edition**! This week, we dive into **Linux system administration and automation**, covering essential topics such as **user management, file permissions, log analysis, process control, volume mounts, and shell scripting**.

---

## 🚀 Project: DevOps Linux Server Monitoring & Automation
Imagine you're managing a **Linux-based production server** and need to ensure that **users, logs, and processes** are well-managed. You will perform real-world tasks such as **log analysis, volume management, and automation** to enhance your DevOps skills.

---

## 📌 Tasks

### **1️⃣ User & Group Management**
- Learn about Linux **users, groups, and permissions** (`/etc/passwd`, `/etc/group`).

Answer : 

- Users: A user in Linux is an account that can log in and interact with the system.Each user has a unique username and a User ID (UID).Users can own files and run programs.

- Groups: A group is a collection of users.Groups make it easier to manage permissions for multiple users at once.Each group has a unique Group Name and a Group ID (GID).A user can belong to one primary group and multiple secondary groups.

- Permissions: Permissions control what users and groups can do with files and directories. Every file and directory has three types of permissions:

   - 1.Read (r): View the contents of a file or list files in a directory.

   - 2.Write (w): Modify a file or add/remove files in a directory.

   - 3.Execute (x): Run a file as a program or enter a directory.

- **Task:**  
  - Create a user `devops_user` and add them to a group `devops_team`.
  - Set a password and grant **sudo** access.
  - Restrict SSH login for certain users in `/etc/ssh/sshd_config`.

Solution :

 <image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/8c383776ca02906b0649a75c3f229bd1877e107b/2025/Images/LinuxImg/img1.PNG">

 <image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/8c383776ca02906b0649a75c3f229bd1877e107b/2025/Images/LinuxImg/img2.PNG">

 <image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/8c383776ca02906b0649a75c3f229bd1877e107b/2025/Images/LinuxImg/img3.PNG">

- Restrict SSH login for specific users (in /etc/ssh/sshd_config):

Edit the file: sudo vim /etc/ssh/sshd_config

Add the following line to restrict access:
      DenyUsers user1 user2 user3

** Explanation: **

- DenyUsers: Specifies a list of usernames that are explicitly denied SSH access.
      Restart the SSH service to apply changes:
      sudo systemctl restart sshd


---

### **2️⃣ File & Directory Permissions**
- **Task:**  
  - Create `/devops_workspace` and a file `project_notes.txt`.
  
  Solution:
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/img4.PNG">

  - Set permissions:
    - **Owner can edit**, **group can read**, **others have no access**.
  - Use `ls -l` to verify permissions.

Solution :

<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/img5.PNG ">
---

### **3️⃣ Log File Analysis with AWK, Grep & Sed**
Logs are crucial in DevOps! You’ll analyze logs using the **Linux_2k.log** file from **LogHub** ([GitHub Repo](https://github.com/logpai/loghub/blob/master/Linux/Linux_2k.log)).

- **Task:**  
    - **Download the log file** from the repository.
    - **Extract insights using commands:**
    - Use `grep` to find all occurrences of the word **"error"**.
Solution:
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/grep.PNG">

   - Use `awk` to extract **timestamps and log levels**.
Solution :
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/awk.PNG">

   - Use `sed` to replace all IP addresses with **[REDACTED]** for security.
Solution :
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/sed.PNG">

   - **Bonus:** Find the most frequent log entry using `awk` or `sort | uniq -c | sort -nr | head -10`.
Solution :
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/9d7fd56722a538c3b657777358bc8bfa16520615/2025/Images/LinuxImg/uniq.PNG">


---

### **4️⃣ Volume Management & Disk Usage**
- **Task:**  
  - Create a directory `/mnt/devops_data`.

Solution:
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/6d1a105f34ba97ab404ae24cc3e65261f1e4b704/2025/Images/LinuxImg/vol1.PNG">

  - Mount a new volume (or loop device for local practice).

Solution:
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/6d1a105f34ba97ab404ae24cc3e65261f1e4b704/2025/Images/LinuxImg/vol2.PNG">

  - Verify using `df -h` and `mount | grep devops_data`.

Solution:
<image src = "https://github.com/ayushgurjar185/90DaysOfDevOps/blob/6d1a105f34ba97ab404ae24cc3e65261f1e4b704/2025/Images/LinuxImg/volu3.PNG">

---

### **5️⃣ Process Management & Monitoring**
- **Task:**  
  - Start a background process (`ping google.com > ping_test.log &`).
  - Use `ps`, `top`, and `htop` to monitor it.
  - Kill the process and verify it's gone.

Solution:

<image src = "90DaysOfDevOps\2025\Images\LinuxImg">

---

### **6️⃣ Automate Backups with Shell Scripting**
- **Task:**  
  - Write a shell script to back up `/devops_workspace` as `backup_$(date +%F).tar.gz`.
  - Save it in `/backups` and schedule it using `cron`.
  - Make the script display a success message in **green text** using `echo -e`.

---

## 🎯 Bonus Tasks (Optional 🚀)
1. Find the **top 5 most common log messages** in `Linux_2k.log` using `awk` and `sort`.
2. Use `find` to list **all files modified in the last 7 days**.
3. Write a script that extracts and displays only **ERROR and WARNING logs** from `Linux_2k.log`.

---

## 📢 How to Submit
- **Write a LinkedIn post** summarizing your Week 2 experience.
- Include screenshots or logs of your tasks.
- **Use hashtags**: `#90DaysOfDevOps` `#LinuxAdmin` `#DevOps`
- Share any blog posts, GitHub repos, or articles you create.

---

## 📚 Resources to Get Started
- [Linux In One Shot](https://youtu.be/e01GGTKmtpc?si=FSVNFRwdNC0NZeba)
- [Linux_2k.log (LogHub)](https://github.com/logpai/loghub/blob/master/Linux/Linux_2k.log)

---

## 📝 Example Submission Post
```markdown
Week 2 of #90DaysOfDevOps2025 done! 🏆

✅ Managed users & SSH access  
✅ Set up permissions & volumes  
✅ Analyzed logs using AWK & grep  
✅ Automated backups with a shell script  

Check out my blog here: [Your Blog/GitHub Link]  

#Linux #SysAdmin #DevOps
```

---

Happy learning, and see you in **Week 3**! 🚀

