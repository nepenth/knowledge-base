**Source:** [https://twitter.com/i/web/status/1942516778502095107](https://twitter.com/i/web/status/1942516778502095107)
**Original Post Date:** 2025-07-14 20:33:13

# Linux File Permissions: A Comprehensive Guide

## Introduction
Linux file permissions are a fundamental aspect of Unix-like operating systems, controlling access to files and directories. This guide provides an in-depth explanation of how permissions work, including their representation in both symbolic and octal formats, as well as special permissions like SUID, SGID, and Sticky Bit.

## Understanding `ls -l` Command Output

The `ls -l` command displays detailed information about files and directories. The output includes columns for file type, permissions, number of links, owner, group, file size, modification date/time, and file name.

File types are indicated by symbols like `-` (file), `d` (directory), or `l` (symbolic link). Permissions are represented as a string of nine characters, divided into three groups for user, group, and other permissions.

- File Type: Indicates whether the entry is a file (`-`), directory (`d`), symbolic link (`l`), etc.
- Permissions: Represented as `rwxrwxrwx` (read, write, execute permissions for user, group, and others).
- Number of Links: The number of hard links pointing to the file.
- Owner: The user who owns the file.
- Group: The group that owns the file.
- File Size: Size of the file in bytes.
- Modification Date and Time: When the file was last modified.
- File Name: Name of the file or directory.

## Permission Representation

Permissions are broken down into three groups: User (Owner), Group, and Other. Each group has three permissions: Read (`r`), Write (`w`), and Execute (`x`).

Permissions can be represented in both symbolic (`rwx`) and octal (`421`) formats. Symbolic notation uses `r`, `w`, and `x` to denote read, write, and execute permissions respectively.

- Read (`r`): Allows viewing the file contents.
- Write (`w`): Allows modifying the file.
- Execute (`x`): Allows running the file (if it's a script or executable).

> **Note/Tip:** Permissions are represented in both symbolic (`rwx`) and octal (`421`) formats.

## Special Permissions

Linux supports special permissions that extend beyond the standard read, write, and execute permissions. These include SUID (Set User ID), SGID (Set Group ID), and Sticky Bit.

SUID is used on executable files to run with the permissions of the file owner rather than the user who executed it. SGID is used on directories to ensure new files inherit the group of the directory.

_Commands to set SUID, SGID, and Sticky Bit permissions respectively._

```bash
chmod u+s file_name
chmod g+s directory_name
chmod +t directory_name
```

- SUID (Set User ID): When set on an executable file, the file runs with the permissions of the file owner.
- SGID (Set Group ID): When set on a directory, new files created in the directory inherit the group of the directory.
- Sticky Bit: When set on a directory, only the owner of a file can delete or rename it.

## Permission Tables

The infographic includes a table that maps binary, octal, and symbolic representations of permissions. For example, `000` (binary) corresponds to `0` (octal) and `---` (symbolic).

Another table shows the permissions for each group (Owner, Group, Other) and how they combine. For instance, `755` means Owner has full permissions (`rwx`), while Group and Others have read and execute permissions (`r-x`).

- Binary: `000` to `111` (8 combinations).
- Octal: `0` to `7`.
- Symbolic: `---` to `rwx`.

## Visual Layout and Color Coding

The infographic uses a dark background with bright colors to highlight different sections. Blue is used for file types and owner/group information, green for group permissions, red for other permissions, and orange for special permissions.

Arrows and lines connect related concepts, making the flow of information clear.

## Additional Notes

The infographic includes notes about errors. For example, a capital `S` appears if you set the SUID or SGID bit on a file that is not executable. A capital `T` appears if you set the Sticky Bit on a file that is not executable.

## Key Takeaways

- Understanding `ls -l` command output and its columns.
- Permission representation in symbolic (`rwx`) and octal formats.
- Special permissions (SUID, SGID, Sticky Bit) and their use cases.
- Mapping binary, octal, and symbolic representations of permissions using tables.
- Visual layout and color coding for better understanding.

## Conclusion
This comprehensive guide on Linux file permissions covers essential concepts such as user/group/other permissions, special permissions (SUID, SGID, Sticky Bit), and permission representations. It provides a clear and detailed explanation with visual aids to enhance understanding.

## External References

- [Linux File Permissions Explained](https://www.linux.com/tutorials/linux-file-permissions-explained/)
- [Understanding Linux Permissions](https://www.digitalocean.com/community/tutorials/understanding-linux-file-permissions)


## Media

**Image Description:** This image is a detailed infographic explaining **Linux file permissions**, a fundamental concept in Unix-like operating systems. The infographic is visually organized and uses color coding, arrows, and tables to break down the concepts into digestible sections. Below is a detailed description of the main elements and technical details:

---

### **1. Title and Overview**
- The title at the top reads: **"Linux File Permissions"**.
- The infographic is designed to explain how file and directory permissions work in Linux, including user, group, and other permissions, as well as special permissions like SUID, SGID, and Sticky Bit.

---

### **2. `ls -l` Command Output**
- The infographic starts with an example of the `ls -l` command output, which is used to display detailed information about files and directories.
- The output is annotated with explanations for each column:
  - **File Type**: Indicates whether the entry is a file (`-`), directory (`d`), symbolic link (`l`), etc.
  - **Permissions**: Represented as `rwxrwxrwx` (read, write, execute permissions for user, group, and others).
  - **Number of Links**: The number of hard links pointing to the file.
  - **Owner**: The user who owns the file.
  - **Group**: The group that owns the file.
  - **File Size**: Size of the file in bytes.
  - **Modification Date and Time**: When the file was last modified.
  - **File Name**: Name of the file or directory.

---

### **3. Permission Representation**
- The permissions are broken down into three groups:
  - **User (Owner)**: Permissions for the file owner.
  - **Group**: Permissions for users in the same group as the file.
  - **Other**: Permissions for all other users on the system.
- Each group has three permissions:
  - **Read (`r`)**: Allows viewing the file contents.
  - **Write (`w`)**: Allows modifying the file.
  - **Execute (`x`)**: Allows running the file (if it's a script or executable).
- Permissions are represented in both symbolic (`rwx`) and octal (`421`) formats:
  - **Symbolic Notation**: `rwx` for read, write, and execute.
  - **Octal Notation**: Each permission has a numerical value:
    - `r` = 4
    - `w` = 2
    - `x` = 1
  - The total permission for a group is the sum of these values. For example:
    - `rwx` = 4 + 2 + 1 = 7
    - `rw-` = 4 + 2 + 0 = 6
    - `r--` = 4 + 0 + 0 = 4

---

### **4. Special Permissions**
- The infographic explains three special permissions:
  - **SUID (Set User ID)**:
    - When set on an executable file, the file runs with the permissions of the file owner, not the user who executed it.
    - Symbolic notation: `u+s` or `u+S` (capital `S` indicates the file is not executable).
    - Command: `chmod u+s file_name`.
  - **SGID (Set Group ID)**:
    - When set on a directory, new files created in the directory inherit the group of the directory.
    - Symbolic notation: `g+s` or `g+S` (capital `S` indicates the file is not executable).
    - Command: `chmod g+s directory_name`.
  - **Sticky Bit**:
    - When set on a directory, only the owner of a file can delete or rename it, even if they have write permissions.
    - Symbolic notation: `t` or `T` (capital `T` indicates the file is not executable).
    - Command: `chmod +t directory_name`.

---

### **5. Permission Tables**
- The infographic includes a table that maps binary, octal, and symbolic representations of permissions:
  - **Binary**: `000` to `111` (8 combinations).
  - **Octal**: `0` to `7`.
  - **Symbolic**: `---` to `rwx`.
  - For example:
    - `000` → `0` → `---` (no permissions).
    - `111` → `7` → `rwx` (full permissions).
- Another table shows the permissions for each group (Owner, Group, Other) and how they combine:
  - For example, `755` means:
    - Owner: `rwx` (7)
    - Group: `r-x` (5)
    - Other: `r-x` (5)

---

### **6. Visual Layout and Color Coding**
- The infographic uses a dark background with bright colors to highlight different sections:
  - **Blue**: Used for file types and owner/group information.
  - **Green**: Used for group permissions.
  - **Red**: Used for other permissions.
  - **Orange**: Used for special permissions (SUID, SGID, Sticky Bit).
- Arrows and lines connect related concepts, making the flow of information clear.

---

### **7. Additional Notes**
- The infographic includes notes about errors:
  - **Capital `S`**: Appears if you set the SUID or SGID bit on a file that is not executable.
  - **Capital `T`**: Appears if you set the Sticky Bit on a file that is not executable.

---

### **8. Footer**
- The infographic is credited to **@sysxplore** with a website link: `sysxplore.com`.

---

### **Summary**
This infographic is a comprehensive guide to understanding Linux file permissions, covering:
- The `ls -l` command output.
- Symbolic and octal permission representations.
- Special permissions (SUID, SGID, Sticky Bit).
- Permission tables for quick reference.
The use of color coding, arrows, and clear explanations makes it an effective educational resource for both beginners and advanced users.
![This image is a detailed infographic explaining **Linux file permissions**, a fundamental concept in...](./media/image_1.jpg)