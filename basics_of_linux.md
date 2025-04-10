# Linux basics
## Important Things to Remember in Linux
1. Linux has super-user account called root
 - root is the most powerful account that can create , modify, delete accounts and make changes to system configuraton files.
2. Linux is case-sensitive system.
 - ABC is NOT same as abc
3. Avoid using spaces when creating files and directories.
4. Linux kernel is not an operating system. It is a small software whithin linux operating system that takes commands from usrs and pass them to system hardware and peripherals.
5. linux is mostly CLI not GUI.

### Command to connect to linux machine from linux machine
ssh -l <user_name> <remote_machine_ip_addres>

## File System Structure and its Description
/boot  Contains file that is used by tge boot loader (grub.cfg)
/root  root user home directory. it is not same as /
/dev   System devices (e.g. disk, cdrom, speakers, flashdrives, keyboard etc.)
/etc   Configuration files
/bin -> /usr/bin everyday user commands
/sbin -> /usr/sbin System/Filesystem commands
/opt   Optional add-on applications (not part of OS apps)
/proc  Running processes (only exist in memory)
/lib -> usr/lib C programming library files needed by commands and apps (strace -e open pwd)
/tmp   Directory for temporary files.
/home  Directory for user.
/var   System logs
/run   System daemons that start very early (e.g systemd and udev) to store temporary rutime files like PID files.
/mnt   To mount external filesystem. (e.g. NFS)
/media  For cdrom mounts.


## Linux supports several file types, each serving a specific purpose. Here’s an overview:

    Regular Files (-):

        These are the most common files and store data like text, binary, or executable content.

        Example: myfile.txt or script.sh.

    Directory Files (d):

        These files act as containers for other files and directories.

        Example: /home/username.

    Symbolic Links (l):

        A shortcut or reference to another file or directory.

        Example: myshortcut -> /path/to/file.

    Block Device Files (b):

        Represent hardware devices that deal with data in blocks, like hard drives or USB drives.

        Example: /dev/sda.

    Character Device Files (c):

        Represent devices that handle data as a stream of characters, such as keyboards or mice.

        Example: /dev/tty.

    Socket Files (s):

        Used for inter-process communication (IPC), enabling data exchange between programs.

        Example: /var/run/docker.sock.

    FIFO (Named Pipe) Files (p):

        Special files used for IPC, enabling data flow in a "first in, first out" manner.

        Example: my_pipe.

## What is Root ?
*. There are three types of root on Linux System
1. Root Account: root is an account or a username on linux machine and it is the most powerful account which has access to all commands and files.

2. Root as /: the very first directory in Linux is also referred as root directory.

3. Root home directory: the root user account also has a directory located in /root which is called root home directory.

## changing password
*. passwd <username> - if you are logged in as a root user, if you want to change a password for yourself then just type cpmmand "passwd".

*. if you logged in as a root user and type command "passwd" it will change root user password.

## File System Path

### Absolute Path

    An absolute path starts from the root directory (/) and provides the complete location of a file or directory.

    It does not depend on the current working directory.

    Example:

        /home/shubham/documents/file.txt

        /usr/bin/python

    Always begins with a /.

### Relative Path

    A relative path is based on your current working directory. It provides the location of a file or directory relative to where you are.

    It does not start with a /.

    Example (if your current directory is /home/shubham):

        documents/file.txt

        ../shared/file.txt (Here .. refers to the parent directory.)

    You can use . for the current directory, and .. for the parent directory.

### Here’s a comprehensive list of common commands related to the **vi editor** in Linux, categorized for ease of use:

---

### **Basic Commands**
- `vi filename`: Open a file in the vi editor.
- `:q`: Quit (when there are no changes).
- `:q!`: Quit without saving.
- `:w`: Save the file.
- `:wq`: Save and quit.

---

### **Navigation**
- `h`: Move cursor left.
- `l`: Move cursor right.
- `j`: Move cursor down.
- `k`: Move cursor up.
- `G`: Go to the end of the file.
- `gg`: Go to the beginning of the file.
- `w`: Jump forward to the next word.
- `b`: Move backward to the previous word.
- `$`: Move to the end of the line.
- `0`: Move to the beginning of the line.
- `CTRL-d`: Scroll down half a screen.
- `CTRL-u`: Scroll up half a screen.

---

### **Editing Commands**
- `i`: Enter **insert mode** to start editing before the cursor.
- `a`: Enter **insert mode** and start editing after the cursor.
- `o`: Create a new line below and enter **insert mode**.
- `dd`: Delete the current line.
- `yy`: Copy the current line.
- `p`: Paste the copied or deleted text.
- `x`: Delete a single character.

---

### **Search**
- `/text`: Search for **text** forward.
- `?text`: Search for **text** backward.
- `n`: Repeat the search forward.
- `N`: Repeat the search backward.

---

### **Replace**
- `:%s/old/new/g`: Replace all occurrences of "old" with "new" in the file.
- `:s/old/new/`: Replace "old" with "new" on the current line.

---

### **Undo/Redo**
- `u`: Undo the last action.
- `CTRL-r`: Redo the undone action.

---

### **Visual Mode**
- `v`: Start **visual mode** for selecting text.
- `V`: Start **visual line mode** for selecting lines.
- `CTRL-v`: Start **visual block mode** for selecting blocks of text.

---

### **Advanced**
- `:set number`: Show line numbers.
- `:set nu!`: Hide line numbers.
- `:syntax on`: Enable syntax highlighting.
- `:syntax off`: Disable syntax highlighting.

These commands cover a wide range of tasks in **vi**, from basic operations to advanced editing features. If you're tackling a 
specific use case, let me know—I can guide you further! 😊

## Find and locate

The `find` and `locate` commands are powerful tools in Linux for searching files and directories, but they work in distinct ways:

---

### **1. Find Command**
The `find` command searches for files and directories **in real-time** within a specified directory. It is versatile and allows complex search criteria.

#### Syntax:
```bash
find [path] [options] [expression]
```

#### Examples:
- **Find a file by name:**
  ```bash
  find /home -name "filename.txt"
  ```
  Searches for `filename.txt` in the `/home` directory.
  
- **Find all directories:**
  ```bash
  find /home -type d
  ```
  Lists all directories in `/home`.

- **Find files modified in the last 3 days:**
  ```bash
  find /home -mtime -3
  ```
  Finds files modified less than 3 days ago.

- **Find files larger than 100MB:**
  ```bash
  find /home -size +100M
  ```
  Finds files larger than 100 megabytes.

---

### **2. Locate Command**
The `locate` command searches for files using a **pre-built database** instead of scanning the filesystem in real-time, making it faster but less up-to-date.

#### Syntax:
```bash
locate [options] [filename]
```

#### Examples:
- **Locate a file by name:**
  ```bash
  locate filename.txt
  ```
  Quickly finds all occurrences of `filename.txt`.

- **Locate files containing a specific pattern:**
  ```bash
  locate '*.log'
  ```
  Finds all files with `.log` extension.

#### Important Note:
To ensure the `locate` database is up-to-date, run:
```bash
sudo updatedb
```

## Wildcard caracters in linux 
Wildcards in Linux are special characters used in commands to represent multiple files, directories, or patterns. They are especially helpful when dealing with a large number of files. Here's a breakdown of common wildcard characters and their usage:

---

### **1. Asterisk (`*`)**
- Represents **zero or more characters**.
- Example:
  ```bash
  ls *.txt
  ```
  Lists all files ending with `.txt` (e.g., `file.txt`, `notes.txt`).

---

### **2. Question Mark (`?`)**
- Represents **exactly one character**.
- Example:
  ```bash
  ls file?.txt
  ```
  Matches files like `file1.txt` or `fileA.txt` but not `file10.txt`.

---

### **3. Square Brackets (`[]`)**
- Represents **a range or set of characters**.
- Example:
  ```bash
  ls file[1-3].txt
  ```
  Matches files `file1.txt`, `file2.txt`, and `file3.txt`.

- **Set of characters**:
  ```bash
  ls file[a,b,c].txt
  ```
  Matches `filea.txt`, `fileb.txt`, and `filec.txt`.

---

### **4. Negation in Square Brackets (`[^]`)**
- Represents anything **not matching the characters in the brackets**.
- Example:
  ```bash
  ls file[!1-3].txt
  ```
  Matches files like `file4.txt` and `file5.txt`, but not `file1.txt` through `file3.txt`.

---

### **5. Curly Braces (`{}`)**
- Used for specifying **lists or ranges of strings**.
- Example:
  ```bash
  mkdir {dir1,dir2,dir3}
  ```
  Creates directories `dir1`, `dir2`, and `dir3`.

- Example with ranges:
  ```bash
  touch file{1..5}.txt
  ```
  Creates files `file1.txt`, `file2.txt`, ..., `file5.txt`.

---

### **6. Tilde (`~`)**
- Represents the **home directory**.
- Example:
  ```bash
  cd ~
  ```
  Changes the directory to your home directory.

---

Wildcards are commonly used in commands like `ls`, `rm`, `cp`, and `mv` to simplify file handling tasks. Let me know if you'd like to try specific examples or need more clarification! 🚀

In Linux, both **soft links** (also known as symbolic links) and **hard links** are methods to reference files, but they work in different ways:

### **Soft Link (Symbolic Link)**
- **How It Works**: A soft link is like a shortcut that points to another file or directory. It simply contains a path to the target file.
- **Characteristics**:
  - It can link to files across different file systems or partitions.
  - If the original file is deleted, the soft link becomes broken because it no longer has a valid target.
  - Soft links can point to directories as well as files.
- **Use Case**: Useful for creating shortcuts to files and directories.

#### Command to create:
```bash
ln -s <target> <link_name>
```
For example:
```bash
ln -s /home/user/file.txt /home/user/soft_link.txt
```

### **Hard Link**
- **How It Works**: A hard link is a direct reference to the file's inode (its identity on the file system). Essentially, the file gets a second name.
- **Characteristics**:
  - Hard links share the same inode, so they are indistinguishable from the original file.
  - If the original file is deleted, the hard link still remains functional as it refers directly to the data.
  - Hard links cannot span across different file systems or link to directories.
- **Use Case**: Useful for ensuring data redundancy.

#### Command to create:
```bash
ln <target> <link_name>
```
For example:
```bash
ln /home/user/file.txt /home/user/hard_link.txt
```