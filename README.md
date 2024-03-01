# Most used Linux commands for day-to-day tasks of DevOps engineer

DevOps professionals often rely on a set of essential Linux commands to manage systems, automate tasks, and ensure the smooth operation of infrastructure. These commands are foundational for DevOps tasks and are used in various contexts, from system administration to deployment automation. Each command is accompanied with an explanation and practical examples to help deepen Linux proficiency.

## System Info Commands:

 **`hostname` - shows the name of the system host.**
    ```bash
    hostname
    localhost
    ```

 **`hostid` - shows the host id of the system assigned by the OS.**
    ```bash
    hostid
    0a123456
    ```

 **`date` - shows the current date and time in UTC format.**
    ```bash
    date
    Wed Jan 19 12:34:56 UTC 2024
    ```

 **`uptime` - shows the elapsed time duration since the machine logged in.**
    ```bash
    uptime
    13:32:48 up 1 day, 3:45, 2 users, load average: 0.25, 0.20, 0.18
    ```

 **`uname` - unix name.**
    ```bash
    uname
    Linux
    ```

 **`clear` - clears the screen.**
    ```bash
    clear
    ```

 **`history` - lists all the commands executed until now.**
    ```bash
    history
    1  ls
    2  cd Documents
    3  nano file.txt
    4  gcc program.c -o program
    5  ./program
    6  history
    ```

 **`sudo` - Super User Do.**
    ```bash
    sudo su - USERNAME
    ```

 **`echo $?` - shows the exit status of the last executed command (0 - success, 1-255 - error/failure).**
    ```bash
    echo $?
    127
    ```

 **`shutdown` - restart the machine immediately (-r restart).**
    ```bash
    sudo shutdown -r now
    ```

    Broadcast message from user@hostname
        (/dev/pts/0) at 12:34 ...

    The system is going down for reboot NOW!

 **`printenv` - displays all the environment variables of the Linux system.**
    ```bash
    printenv
    TERM=xterm-256color
    SHELL=/bin/bash
    USER=your_username
    ...
    ```

 **`last` - shows previous logins in the Linux system.**
    ```bash
    last
    root  pts/0        Fri Mar 01  13:35   still logged in
    reboot   system boot  5.4.0-96-generic Fri Mar 01  13:35  still running
    ```
    
**`systemctl` — System Control: Manage system services using systemd.**
    ```bash
    systemctl status sshd
    ```

    ```plaintext
    ● sshd.service - OpenBSD Secure Shell server
         Loaded: loaded (/lib/systemd/system/sshd.service; enabled; vendor preset: enabled)
         Active: active (running) since Fri 2024-03-01 13:37:36 UTC; 1 day 3h ago
           Docs: man:sshd(8)
                 man:sshd_config(5)
        Process: 1234 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
       Main PID: 5678 (sshd)
          Tasks: 1 (limit: 1234)
         Memory: 2.3M
            CPU: 12ms
         CGroup: /system.slice/sshd.service
                 └─5678 /usr/sbin/sshd -D

    Mar 01 13:37:36 hostname systemd[1]: Starting OpenBSD Secure Shell server...
    Mar 01 13:37:36 hostname sshd[5678]: Server listening on 0.0.0.0 port 22.
    Mar 01 13:37:36 hostname sshd[5678]: Server listening on :: port 22.
    Mar 01 13:37:36 hostname systemd[1]: Started OpenBSD Secure Shell server.
    ```
## File Commands

**`touch` - creates an empty file or updates timestamp of the existing file.**
- `touch <fileName>` - creates a single empty file.
- `touch <file1> <file2>` - creates file1, file2 empty files.

**`cat` - concatenates and displays the contents of files.**
- `cat <fileName>` - displays the contents of the file.
- `cat > <fileName>` - creates a new file, allows input content interactively and redirects inputted content to the created file (`>` redirection operator).

**`head` - displays first 10 lines of the file by default.**
- `head <fileName>` - displays first 10 lines of the file by default.
- `head -n 5 <fileName>` - displays first 5 lines of the file (`-n number`).
    ```bash
      ~ head -n 5  help.txt
    1. Commands shortcut
    ....
    5. huddle - Connect to Syncup Call
    ```

**`tail` - displays the last 10 lines of the file by default.**
- `tail <fileName>` - displays the last 10 lines of the file by default.
- `tail -F <fileName>` - displays contents of the file in real-time even when the file is rotated or replaced (used for log file monitoring).
    ```bash
     ~ tail -F mySystem.logs
    echo "DevOps is the best"
    echo "I know Linux commands"
   ```

**`less` - used to view large files (log files) in a paginated manner.**

**`rm` - remove command.**
- `rm <fileName>` - removes the file.
- `rm -r <dirName>` - removes files & folders of directory recursively (`-r recursive`).
- `rm -rf <dirName>` - force remove the files & folders of directory recursively (`-f force`).
    - Example: `rm -r ./test`

**`cp` - copy command.**
- `cp <source> <destination>` - copy the files and folders from source to destination.
- `cp -r <dir1> <dir2>` - copy dir1 directory to dir2 directory recursively (`-r recursive`).
    - Example: `cp -r ./sourceDir ./destiDir`

## File Permission Commands

 **`ls -l <pathOfFileName>` - shows the permissions of the file.**
    ```bash
      ~ ls -l .
    total 1
    -rw-r--r--   1 dmitry  admin   Mar 01 14:06   mytext.txt
      ```

 **`ls -ld <dirNamePath>` - shows the permissions of the directory.**
    ```bash
      ~ ls -ld Downloads
    -rw-r--r--   1 dmitry  admin   Mar 01 14:06   Downloads
    ```

 **`chmod <octalNumber> <fileName>` - changes mode/permissions of the file.**
    - Example: `chmod 742 test.txt`

 **`chmod <octalNumber> -R <dirName>` - changes mode/permissions of the directory recursively.**
 
 **`chown <newUser> <fileName>` - changes the user ownership of a file.**
    - Example: `chown rocky test.txt`

 **`chown <newUser>:<newGroup> <fileName>` - changes the user & group ownerships of a file.**

 **`chgrp <groupName> <fileName/dirName>` - updates the group name for file/directory.**
    - Example: `chgrp mygroup ./test`

**`getfacl <fileName/dirName>` - shows the file/directory access control list.**
    ```bash
      ~ getfacl filename.txt
     
    # file: filename.txt
    # owner: user1
    # group: group1
    user::rw-
    group::r--
    other::r--
   
**`setfacl -m u:<userName>:rwx <fileName/dirName>` - modifies the current acl of the file/directory.**

**`setfacl -x u:<userName>: <fileName/dirName>` - removes the acl permissions for the file/directory.**

**`setfacl -m g:<groupName>:rwx <fileName/dirName>` - modifies the group acls for the file/directory.**

 **`setfacl -x g:<groupName>: <fileName/dirName>` - removes the group acl permissions for the file/directory.**

### File Permission Octal Numbers

- Read (r) — 4
- Write (w) — 2
- Execute (x) — 1

Sum the numbers to generate an octal number for setting permissions on a file or directory.

## User Management Commands

 **`ac` — Total connect time for all users or specified users.**

    The `ac` command reads the `/var/log/wtmp` file, which contains binary data about every login, logout, system event, and current status on the system. It gets its data from the `wtmp` file.
    - Display total login time of a specific user.
        ```bash
        ac john
        ```

    - Display total login time for each user.
        ```bash
        ac -p
        ```

    - Display total login time for each day.
        ```bash
        ac -d
        ```

    - Display total login time for the current day.
        ```bash
        ac -d -p
        ```

    - Display login time from a specific log file.
        ```bash
        ac -f /var/log/wtmp
        ```

 **`useradd` - Creates a user account.**

    - Creates user account without home & mail spool directories.
        ```bash
        useradd <userName>
        ```
        Example: `useradd bot`

    - Creates user account with home & mail spool directories.
        ```bash
        useradd -m <userName>
        ```
        Example: `useradd -m bot`

 **`passwd` - The system generates a password for the user and then stores it in the `/etc/shadow` file.**

 **`userdel` - Deletes User Account.**

    - Deletes the user from the system.
        ```bash
        userdel <userName>
        ```

    - Deletes the user from the system along with home and mail spool directories.
        ```bash
        userdel -r <userName>
        ```
        Example: `userdel -r bot`

 **`/etc/passwd` - Stores information about user accounts.**

    - Displays the complete list of users on that machine.
        ```bash
        cat /etc/passwd
        ```

 **`/etc/shadow` - Stores the password for users in an encrypted format.**

    - Displays the complete list of user passwords on that machine.
        ```bash
        cat /etc/shadow
        ```

 **`su` - Substitute user.**

    - Switches to the user mentioned.
        ```bash
        su <userName>
        ```

 **`exit` - To logout from that user.**

    - Example: `su - ram`

 **`usermod` - Modify user.**

    - Adds the user to another group (-aG append the user to the group without removing from other groups).
        ```bash
        usermod -aG <groupName> <userName>
        ```
        Example: `usermod -aG mygroup ram`

 **`chsh` - Change shell.**

    - Changes the shell to bash for the user.
        ```bash
        chsh -s /bin/bash <user>
        ```

    - Changes the shell to sh for the user.
        ```bash
        chsh -s /bin/sh <user>
        ```
        Example: `chsh -s /bin/sh ubuntu`

## Group Management Commands

 **`groupadd` - Creates the group.**
    ```bash
    groupadd <groupName>
    ```

 **`groupdel` - Deletes the group.**
    ```bash
    groupdel <groupName>
    ```

 **`/etc/group` - Stores the information of the groups.**
    ```bash
    cat /etc/group
    ```

    - Displays the complete list of groups on that machine.

 **`gpasswd` - Creates a password for the group.**
    ```bash
    gpasswd <groupName>
    ```

 **`gpasswd` - Adds the user to the group.**
    ```bash
    gpasswd -a <userName> <groupName>
    ```

 **`gpasswd` - Removes the user from the group.**
    ```bash
    gpasswd -d <userName> <groupName>
    ```

 **`gpasswd` - Adds multiple users to the group and removes the existing ones of the group.**
    ```bash
    gpasswd -M <userName1>,<userName2>,<userName3> <groupName>
    ```

## Searching Commands

 **`find` — Search for files/directories based on their names.**
    ```bash
    find . -name <fileName>
    ```

    - Finds the mentioned file if available in the current directory (`.` represents the current directory).

 **`find` - Finds the mentioned file in the directory.**
    ```bash
    find <dirName> -name <fileName>
    ```

 **`find` - Finds the files in the directory having 754 permission.**
    ```bash
    find <dirName> -perm 754
    ```

 **`locate` - Search for files/directories based on their names.**
    - `locate` is faster for finding files by name due to its pre-built database, while `find` is more versatile, allowing complex searches based on various criteria in real-time.

 **`locate` - Locates the file/directory and displays the path.**
    ```bash
    locate <fileName/dirName>
    ```
    Example: `locate crazy.txt`

## GREP Command — Global Regular Expression Print

 **`grep` - Used to find text patterns within files.**
    ```bash
    grep <textToSearch> <fileName>
    ```

 **`grep` - Used to find text patterns within the file ignoring the case (-i ignore case).**
    ```bash
    grep -i <textToSearch> <fileName>
    ```

 **`grep` - Used to find non-matching lines of text patterns (-v invert-match).**
    ```bash
    grep -v <textToSearch> <fileName>
    ```

 **`grep` - Used to display the matching string file names.**
    ```bash
    grep -l <textToSearch> <fileNames>
    ```
    Example: `grep -l welcome crazy.txt`

 **Additional commands related to grep:**
    - `egrep` (or `grep -E`)
    - `fgrep` (or `grep -F`)
    - `zgrep` (for compressed files)
    - `zegrep` (or `zgrep -E` for compressed files)
    - `bzgrep` (for compressed files)
    - `ack-grep` (Ack)

## Hardware Information Commands

 **`free -h` - Display system memory information in human-readable format (-h).**
    ```bash
    free -h
    ```

 **`df -h` - Displays the disk space usage of mounted file systems.**
    ```bash
    df -h
    ```

 **`du` - Disk usage.**
    - Display disk usage information in human-readable format.
    ```bash
    du -h
    ```

 **`du` - Display the total size of the directory in human-readable format, summarizing the size instead of listing individual file sizes.**
    ```bash
    du -sh
    ```

 **`du` - Displays the total size of the file/directory.**
    ```bash
    du -sh <fileName/dirName>
    ```

## Connection To Remote System

 **`ssh` - Secure Shell: Connect to a remote server securely.**
    ```bash
    ssh user@remote_host
    ```

 **`scp` - Securely Copy Files: Copy files between local and remote systems using SSH.**
    ```bash
    scp file.txt user@remote_host:/path
    ```

 **`rsync` - Remote Sync: Synchronize files and directories between systems.**
    ```bash
    rsync -avz local_folder/ user@remote_host:remote_folder/
    ```

## Network Commands

 **`nc` — Simple tcp proxy, network daemon testing.**
    ```bash
    nc -vz google.com 443
    ```

 **`ping` - Tests the reachability & responsiveness of the remote host.**
    ```bash
    ping google.com -c 2
    ```

 **`dig` - Shows DNS information of the domain.**
    ```bash
    dig medium.com
    ```

 **`wget` - Used to retrieve/download files from the internet.**
    ```bash
    wget <url>
    ```

 **`curl` - Client URL.**
    ```bash
    curl <url>
    ```

 **`ifconfig` - Displays available network interfaces.**
    ```bash
    ifconfig
    ```

 **`ip addr` - Displays and manipulates network interface info.**
    ```bash
    ip addr
    ```

 **`curl` - Shows the public IP address of the machine.**
    ```bash
    curl ifconfig.me
    ```

 **`netstat` - Shows all TCP open ports (-a all, t-tcp, n-active, p protocol).**
    ```bash
    netstat -antp
    ```

 **`traceroute` - Traces the route using packets from source to destination host.**
    ```bash
    traceroute <url>
    ```

## Process Information Commands

 **`ps` - Process status.**
    - Displays the currently running process.
    ```bash
    ps
    ```

 **`ps` - Displays the process of the username.**
    ```bash
    ps -u <userName>
    ```

 **`ps` - Displays all the processes of the system.**
    ```bash
    ps -ef
    ```

 **`top` - Shows the real-time, dynamic view of the running processes of a system.**
    ```bash
    top
    ```

 **`kill` - Gracefully terminates the process pid (-9 forceful).**
    ```bash
    kill <pid>
    ```

 **`pgrep` - Shows process id of processes based on name/other criteria.**
    ```bash
    pgrep <processName>
    ```

 **`bg` - Sends the process to the background & continues execution without interruption.**
    ```bash
    bg
    ```

 **`fg` - Brings the process to the foreground and makes it an active process.**
    ```bash
    fg
    ```

 **`nohup` - Runs command/script in the background even after the terminal is closed or the user logs out.**
    - Example: `nohup ./script.sh`

 **`<command> &` — Using at the end of a command runs it in the background.**
    - Example: `./script.sh &`


## Archiving File Commands

 **`tar` - Tape archive.**
    - Creates the tar file with the fileName for the directory mentioned (-c create, -v verbose, -f output file name).
    ```bash
    tar -cvf <fileName> <directory>
    ```

 **`tar` - Puts the extracted files into the destination directory (-x extract, -v verbose, -f source tar file name, -C change the folder and download to destination dir).**
    ```bash
    tar -xvf <sourceTarFileName> -C <destinationDir>
    ```

## Ubuntu Package Related Commands

 **`apt` - Package Manager for Debian-based Linux distributions (e.g., Ubuntu).**
    - A newer version of the package manager with colorized output, progress bar, and additional functions.
    ```bash
    apt
    ```

 **`apt-get` - Older version and basic package manager.**
    ```bash
    apt-get
    ```

 **`apt update` - Updates the package list.**
    ```bash
    apt update
    ```

 **`apt list --installed` - Lists all the installed packages.**
    ```bash
    apt list --installed
    ```

 **`apt list --installed <packageName>` - Shows the package name if it's installed.**
    ```bash
    apt list --installed <packageName>
    ```

 **`apt show <packageName>` - Shows information about a package mentioned.**
    ```bash
    apt show <packageName>
    ```

 **`apt search <packageName>` - Searches and shows the list of packages.**
    ```bash
    apt search <packageName>
    ```

 **`apt install <packageName>` - Installs the required package.**
    ```bash
    apt install <packageName>
    ```

 **`apt remove <packageName>` - Removes the required package.**
    ```bash
    apt remove <packageName>
    ```

 **`apt purge <packageName>` - Removes the required package along with its config files.**
    ```bash
    apt purge <packageName>
    ```

**Note:** For other package managers, replace "apt" with the appropriate package manager.


## Directory Commands

 **`pwd` - Shows the present working directory (abbr. Print Working Directory).**
    ```bash
    pwd
    ```

 **`cd` - Change directory.**
    - Changes to its parent directory (i.e., one level up).
    ```bash
    cd ..
    ```

 **`cd` - Change to the directory mentioned.**
    ```bash
    cd <dirName>
    ```

 **`cd` - Changes to the currently logged-in user's home directory.**
    ```bash
    cd ~
    ```

 **`cd` - Changes the directory two levels up.**
    ```bash
    cd ../..
    ```

 **`cd` - Changes to the last working directory.**
    ```bash
    cd -
    ```

 **`mkdir` - Make directory.**
    - Creates the directory.
    ```bash
    mkdir <dirName>
    ```

 **`mkdir` - Creates directory with its parent directories if it does not exist (-p parent).**
    ```bash
    mkdir -p <pathOftheDir>
    ```

 **`ls` - Lists the files & folders of the directory you are in.**
    - Lists all files & folders along with hidden files (-a all).
    ```bash
    ls -a
    ```

 **`ls` - Lists all files & folders along with hidden files in a formatted manner (-l long listing format).**
    ```bash
    ls -al
    ```

## Misc Commands

 **`man` - Displays the manual page for a specific command.**
    - Provides detailed information and usage instructions.
    ```bash
    man <commandName>
    ```

 **`sed` - Edits a stream of text by substituting occurrences of a pattern with another.**
    ```bash
    sed 's/pattern/replacement/g' <fileName>
    ```

 **`awk` - A powerful programming language for text processing.**
    ```bash
    awk '<pattern> {print}' <fileName>
    ```

 **`wc` - Word Count.**
    ```bash
    wc <fileName>
    ```

 **`ln` - Create Links.**
    ```bash
    ln -s <source> <linkName>
    ```

 **`stat` - Shows detailed information about the file or directory.**
    ```bash
    stat <fileName/dirName>
    ```

 **`cron` - System daemon for managing scheduled tasks.**
    ```bash
    cron
    ```

 **`crontab` - Used to create, edit, and manage cron jobs.**
    ```bash
    crontab -e
    ```

 **`tree` - Representation of files and directories of a specific directory.**
    ```bash
    tree <directoryName>
    ```

 **`echo "sample text" | grep text` - The output of the first command is passed as input to the second command using the pipe (|) symbol.**
    ```bash
    echo "sample text" | grep text
    ```

 **`ls -l | tee file.txt` - Redirects the list to the file.txt and simultaneously displays it in the terminal.**
    ```bash
    ls -l | tee file.txt
    ```

 **`echo "sample text" > <fileName>` - Writes the content to the file mentioned by overwriting the existing content (> redirection operator).**
    ```bash
    echo "sample text" > <fileName>
    ```

 **`echo "new sample text" >> <fileName>` - Appends the contents to the file mentioned without overwriting the existing content (>> redirection operation).**
    ```bash
    echo "new sample text" >> <fileName>
    ```
