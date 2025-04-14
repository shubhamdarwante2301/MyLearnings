The `chmod` command in Linux is used to manage file and directory permissions. Permissions determine how files and directories can be accessed or modified by different users. Here's how you can use `chmod`:

---

### **Understanding File Permissions**
File permissions are divided into three groups:
1. **Owner**: The user who owns the file.
2. **Group**: Users who belong to the file's group.
3. **Others**: Everyone else.

Each group can have three types of permissions:
- **Read (r)**: Permission to view the file's contents (`4`).
- **Write (w)**: Permission to modify the file (`2`).
- **Execute (x)**: Permission to execute the file (`1`).

---

### **Syntax of `chmod`**
```bash
chmod [options] mode file
```
- **mode**: Represents the permissions to apply. It can be in symbolic or numeric format.
- **file**: Name of the file or directory whose permissions are being changed.

---

### **Using Numeric Mode**
Permissions are represented by a three-digit number:
- **Owner**, **Group**, and **Others** each get one digit (e.g., `755`).
- Combine read (`4`), write (`2`), and execute (`1`) permissions.

#### Example:
To set permissions to `rwx` for the owner, `r-x` for the group, and `r-x` for others:
```bash
chmod 755 file.txt
```

---

### **Using Symbolic Mode**
You can use letters (`u` for owner, `g` for group, `o` for others, and `a` for all) to modify permissions.

#### Examples:
1. Grant execute permission to the owner:
   ```bash
   chmod u+x file.txt
   ```
2. Remove write permission from the group:
   ```bash
   chmod g-w file.txt
   ```
3. Set read and write for all:
   ```bash
   chmod a+rw file.txt
   ```

---

### **Directory Permissions**
When dealing with directories:
- **Execute (`x`)** is needed to enter the directory.
- **Read (`r`)** is needed to list its contents.
- **Write (`w`)** is needed to create or delete files in the directory.

#### Example:
Make a directory accessible and writable by everyone:
```bash
chmod 777 directory_name
```

---

### **Options**
1. **Recursive Mode**: Apply permissions to all files and subdirectories.
   ```bash
   chmod -R 755 directory_name
   ```

2. **Verbose Mode**: Show changes being made.
   ```bash
   chmod -v 755 file.txt
   ```

The `chown` and `chgrp` commands in Red Hat (and most Linux distributions) are used for managing file and directory ownership and group associations. Here’s a brief explanation of each:

### 1. `chown` (Change Ownership)
The `chown` command is used to change the ownership of files or directories. 

**Syntax:**
```bash
chown [OPTIONS] USER[:GROUP] FILE/DIRECTORY
```

**Examples:**
- Change the owner of a file:
  ```bash
  chown john file.txt
  ```
  Here, the user `john` becomes the new owner of `file.txt`.

- Change the owner and group of a file:
  ```bash
  chown john:developers file.txt
  ```
  This sets `john` as the owner and `developers` as the group.

- Change ownership recursively (for all files within a directory):
  ```bash
  chown -R john /path/to/directory
  ```

---

### 2. `chgrp` (Change Group)
The `chgrp` command changes the group associated with a file or directory. 

**Syntax:**
```bash
chgrp [OPTIONS] GROUP FILE/DIRECTORY
```

**Examples:**
- Change the group of a file:
  ```bash
  chgrp developers file.txt
  ```
  Here, the file `file.txt` is now associated with the `developers` group.

- Change group recursively:
  ```bash
  chgrp -R developers /path/to/directory
  ```

---

### Key Options for Both Commands:
- `-R`: Applies the changes recursively.
- `--verbose`: Displays detailed information about changes made.


# Access Control List (ACL)

**What is ACL?**

*   Access control list (ACL) provides an additional, more flexible permission mechanism for file systems. It is designed to assist with UNIX file permissions. ACL allows you to give permissions for any user or group to any disc resource.

**Use of ACL:**

*   Think of a scenario in which a particular user is not a member of group created by you but still you want to give some read or write access, how can you do it without making user a member of group, here comes in picture Access Control Lists, ACL helps us to do this trick
*   Basically, ACLs are used to make a flexible permission mechanism in Linux.
*   From Linux man pages, ACLs are used to define more fine-grained discretionary access rights for files and directories.
*   Commands to assign and remove ACL permissions are: `setfacl` and `getfacl`

List of commands for setting up ACL :

1.  **To add permission for user**
    `setfacl -m u:user:rwx /path/to/file`

2.  **To add permissions for a group**
    `setfacl -m g:group:rw /path/to/file`

3.  **To allow all files or directories to inherit ACL entries from the directory it is within**
    `setfacl -Rm "entry" /path/to/dir`

4.  **To remove a specific entry**
    `setfacl -x u:user /path/to/file` *(For a specific user)*

5.  **To remove all entries**
    `setfacl -b path/to/file` *(For all users)*

**Note:**

*   As you assign the ACL permission to a file/directory it adds + sign at the end of the permission
*   Setting w permission with ACL does not allow to remove a file

## Help Commands

*   There are 3 types of help commands

*   `whatis` command
*   `command --help`
*   `man` command

Linux input/output redirection is a powerful feature that allows you to control how data flows between programs, files, and devices. Here’s an overview of the main concepts:

### **1. Standard Input, Output, and Error**
- **Standard Input (`stdin`)**: The input stream (keyboard by default) for a program.
- **Standard Output (`stdout`)**: The output stream where a program writes results (terminal by default).
- **Standard Error (`stderr`)**: The stream where error messages are displayed (also the terminal by default).

### **2. Types of Redirection**
#### **Redirecting Output**
- Redirect output to a file:
  ```bash
  command > file.txt
  ```
  This replaces the file’s content.
- Append output to a file:
  ```bash
  command >> file.txt
  ```
  This adds the output to the end of the file without overwriting.

#### **Redirecting Input**
- Redirect input from a file:
  ```bash
  command < file.txt
  ```

#### **Redirecting Errors**
- Redirect error messages to a file:
  ```bash
  command 2> errors.txt
  ```
  Append error messages to a file:
  ```bash
  command 2>> errors.txt
  ```

#### **Combining Output and Errors**
- Redirect both output and errors to the same file:
  ```bash
  command > file.txt 2>&1
  ```
- Send both to `/dev/null` (discard them):
  ```bash
  command > /dev/null 2>&1
  ```

### **3. Pipes**
Use pipes (`|`) to send the output of one command as the input to another:
```bash
command1 | command2
```

### **4. Here Documents**
Provide input directly within the script:
```bash
command << EOF
Input data
EOF
```

### **5. Tee Command**
Write output to a file and the terminal simultaneously:
```bash
command | tee file.txt
```
