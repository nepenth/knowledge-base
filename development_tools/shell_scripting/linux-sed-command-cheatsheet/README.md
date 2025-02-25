The Linux `sed` command is a powerful text processing tool that allows system administrators to manipulate and transform text files. This cheatsheet provides a comprehensive overview of the `sed` command's functionality, including its various options, flags, and examples.

#### Technical Content
##### Sed Commands
The `sed` command has several options available for manipulating text files. These include:

* `q`: Exit without processing any more commands or input.
* `d`: Delete the pattern space immediately after the current cycle.
* `p`: Print out the pattern space (to the standard output).
* `a`: Append text after a line.
* `i`: Insert text before a line.
* `c`: Replace the contents of the file with the contents of the pattern space.
* `w`: Write the pattern space to the specified file name.
* `D`: Delete the first line that matches the pattern.

Example:
```bash
# Delete the second input line
sed '2d' input.txt

# Print only the second input line
sed -n '2p' input.txt
```

##### Command Options
The `sed` command also has several options available for customizing its behavior. These include:

* `-n`: Suppress automatic printing of pattern space.
* `-1`: Add the contents of script-file to the commands to be executed.
* `e`: Execute multiple `sed` commands.
* `s`: Use extended regular expressions (supports '+', '?', and '*').

Example:
```bash
# Replace all occurrences of a string with another string
sed -e 's/old_string/new_string/g' input.txt

# Execute multiple sed commands
sed -e 's/old_string1/new_string1/g' -e 's/old_string2/new_string2/g' input.txt
```

##### Command Flags
The `sed` command has several flags available for modifying its behavior. These include:

* `-i`: Edit files in place (make backup if SUFFIX supplied).
* `-l`: Suppress automatic printing of pattern space.
* `--help`: Display a help message and exit.

Example:
```bash
# Edit file in place with backup
sed -i.bak 's/old_string/new_string/g' input.txt

# Suppress automatic printing of pattern space
sed -n 'p' input.txt
```

##### Basic Examples
Here are some basic examples of using the `sed` command:

* Delete the second input line: `sed '2d' input.txt`
* Print only the second input line: `sed -n '2p' input.txt`
* Replace all occurrences of a string with another string: `sed 's/old_string/new_string/g' input.txt`

##### Replacing Text
The `sed` command can be used to replace text in a file. Here are some examples:

* Replace all occurrences of a string with another string: `sed 's/old_string/new_string/g' input.txt`
* Replace the first occurrence of a string with another string: `sed 's/old_string/new_string/' input.txt`

##### Appending and Prepending Text
The `sed` command can be used to append or prepend text to a file. Here are some examples:

* Append text at the end of each line: `sed 's/$/appended_text/' input.txt`
* Prepend text before each line: `sed 's/^/prepended_text/' input.txt`

##### Deleting Lines
The `sed` command can be used to delete lines from a file. Here are some examples:

* Delete every 4th line starting with line 6: `sed '6~4d' input.txt`
* Delete all empty lines: `sed '/^$/d' input.txt`

#### Key Takeaways and Best Practices
Here are some key takeaways and best practices for using the `sed` command:

* Always test your `sed` commands on a sample file before running them on a production file.
* Use the `-n` option to suppress automatic printing of pattern space when you don't want to print the entire file.
* Use the `-i` option to edit files in place, but make sure to specify a backup suffix to avoid losing data.
* Use extended regular expressions with the `s` option to match complex patterns.

#### References
The following tools and technologies are mentioned in this article:

* `sed`: A powerful text processing tool for Linux and Unix systems.
* Linux: An open-source operating system.
* Unix: A family of multi-user, multi-tasking operating systems.

Note: The infographic "Linux SED Command Cheatsheet" is available at [sysxplore.com](http://sysxplore.com) and provides a comprehensive guide to the `sed` command and its various options, flags, and examples.
## Source

- Original Tweet: [https://twitter.com/i/web/status/1881322615945777273](https://twitter.com/i/web/status/1881322615945777273)
- Date: 2025-02-25 15:15:00


## Media

### Media 1
![media_0](./media_0.jpg)
**Description:** The infographic, titled "Linux SED Command Cheatsheet," provides a comprehensive overview of the Sed command's functionality. The title is displayed at the top in white text against a black background, accompanied by the website URL "sysxplore.com" and its logo on either side.

**Sed Commands**

*   This section lists various options available for the Sed command, including:
    *   `q`: Exit without processing any more commands or input.
    *   `d`: Delete the pattern space immediately after the current cycle.
    *   `p`: Print out the pattern space (to the standard output).
    *   `a`: Append text after a line.
    *   `i`: Insert text before a line.
    *   `c`: Replace the contents of the file with the contents of the pattern space.
    *   `w`: Write the pattern space to the specified file name.
    *   `D`: Delete the first line that matches the pattern.

**Command Options**

*   This section explains the different command options available for Sed, including:
    *   `-n`: Suppress automatic printing of pattern space.
    *   `-1`: Add the contents of script-file to the commands to be executed.
    *   `e`: Execute multiple Sed commands.
    *   `s`: Use extended regular expressions (supports '+', '?', and '*').

**Command Flags**

*   This section lists various flags that can be used with Sed, including:
    *   `-i`: Edit files in place (make backup if SUFFIX supplied).
    *   `-l`: Suppress automatic printing of pattern space.
    *   `--help`: Display a help message and exit.

**Basic Examples**

*   This section provides examples of basic Sed commands, including:
    *   Deleting the second input line.
    *   Printing only the second input line.
    *   Replacing all occurrences of a string with another string.

**Replacing Text**

*   This section explains how to replace text using Sed, including:
    *   Replacing all occurrences of a string with another string.
    *   Replacing the first occurrence of a string with another string.

**Appending and Prepending Text**

*   This section describes how to append or prepend text to a file using Sed, including:
    *   Appending text at the end of each line.
    *   Preferring text before each line.

**Deleting Lines**

*   This section explains how to delete lines from a file using Sed, including:
    *   Deleting every 4th line starting with line 6.
    *   Deleting all empty lines.

Overall, this infographic provides a comprehensive guide to the Sed command and its various options, flags, and examples. It is an essential resource for anyone looking to learn more about this powerful text processing tool.

*Last updated: 2025-02-25 15:15:00*