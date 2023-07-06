## Unix

Unix is an operating system.
Unix and Linux communicate through _kernel_ using _shell_(a command line interpreter that converts user commands(query) to 'language understand by kernel')
<br/>

## Unix/Linux Architecture

1. Hardware Layer **->** It consists of several hardware components like RAM, CPU, STORAGE.
2. Kernel Layer **->** The kernel is one of the core section of an operating system. It is responsible for each of the major actions of the Linux OS
3. Shell **->** Shell converts user commands (query) to 'language understand by kernel'. This program takes input from user and converts pass them to kernel.
   Some example of shells: - bourne shell - bourne-again shell (Bash) - z shell (zsh) - friendly interactive shell (fish )

4. Command and Utilities **->** it includes all the applications and commands that you use

## linux process

A linux process is a program in execution. When a program is executed in linux a process is created. As soon as a process is created it is assigned a unique id that is called process id(PID). As there are multiple processes always running in linux OS there arise the need of process management. The process are assigned number starting from 2 as PID '1' is reserved for 'init process'.
there are 4 types of process in linux.

1. Child process: when a process is created by an already running process it is called a child process. when parent process needs to execute some file it creates a child process.
   <br/>
2. Daemon process: These are process that run in the background. Daemon processes are process run by system itself and these provide resources to other process. These processes run with root permissions.
   <br/>
3. Orphan process: commonly a situation occurs when the parent process of a running child process gets terminated and now the child process has no parent, in this situation this orphan child process is taken under init process but still as the original parent of child process is terminated it is called an orphan process.
   <br/>
4. zombie process: when a child process is terminated the parent process collects all the information required, and the the process is removed from the process state table and all the resources are taken from it. when a child process has terminated but still gets listed in the process state table it is called a zombie process.

## What is linux file system?

linux file system is a built-in layer in linux OS that is used to manage the data saved in disk storage.It manages the metadata of files, like file_name, file_size, file_type etc...
<br/>

## File Structure in linux

Linux file system has hierarchal file structure as it contains a root directory and its sub-directories. All directories can be accessed from root directory.

- / **->** it is the top level directory of a directory structure.
- /bin **->** stores binaries or executables like vim,ls,gzip...etc.
- /sbin **->** stores system binaries that should only be used by root user like deluser...
- /boot **->** it includes the files needed to properly start linux OS.
- /lib **->** it includes the shared library files shared by executables in bin and sbin direcotries.
- /etc **->** stands for editable text configuration, it includes local config files for system, most files in this directory are .conf files.
- /home **->** all users have subdirectory inside home. Every user has individual files, bin, and configurations under this directory.
- /tmp **->** tmp directory stores temprory files that will be deleted between reboots.
- /usr **->** it contains the files that are non essential to the operating system and are installed by user.
  <br/>

# Inode

Inode is a data structure.

## File security

The `ls -l` command (for long listing) option will show you metadata about your Linux files, including the permissions set on the file.

```Shell
$ ls -l

OUTPUT
drwxr-xr-x. 4 root root    68 Jun 13 20:25 tuned
-rw-r--r--. 1 root root  4017 Feb 24  2022 vimrc
```

In this example, you see two different listings. The first field of the `ls -l` output is a group of metadata that includes the permissions on each file. Here are the components of the `vimrc` listing:

- File type: `-`
- Permission settings: `rw-r--r--`
- Extended attributes: dot (`.`)
- User owner: `root`
- Group owner: `root`
  File type `-` means no special type of file
  File type `d` means its a directory
  Following are the permissions assigned to diff. type of users.

### File permissions for vimrc file

`rw-r--r--` Lets understand this

r stands for read permissions
w stands for write permissions
x stands for execute permissions
\- means the permission is not given

But why is read permission defined 3 times in above vimrc example.

The above expression can be broken like this

- rw- (1st 3 letters for user)
- r-- (2nd 3 letters for group)
- r-- (last 3 letters for others)

### Octal representation of File permissions

When Linux file permissions are represented by numbers, it's called numeric mode. In numeric mode, a three-digit value represents specific file permissions (for example, 744.) These are called octal values. The first digit is for owner permissions, the second digit is for group permissions, and the third is for other users. Each permission has a numeric value assigned to it:

- r (read): 4
- w (write): 2
- x (execute): 1

- Owner: rwx = 4+2+1 = 7
- Group: r-- = 4+0+0 = 4
- Others: r-- = 4+0+0 = 4
  `rw-r--r--` in Octal
- Owner: rw- = 4+2+0 = 6
- Group: r-- = 4+0+0 = 4
- Others: r-- = 4+0+0 = 4

#### Read (r)

Read permission is used to access the file's contents. You can use a tool like `cat` or `less` on the file to display the file contents. You could also use a text editor like Vi or `view` on the file to display the contents of the file. Read permission is required to make copies of a file, because you need to access the file's contents to make a duplicate of it.

#### Write (w)

Write permission allows you to modify or change the contents of a file. Write permission also allows you to change the contents of a file. Without write permission, changes to the file's contents are not permitted.

#### Execute (x)

Execute permission allows you to execute the contents of a file. Typically, executables would be things like commands or compiled binary applications. However, execute permission also allows someone to run Bash shell scripts, Python programs, and a variety of interpreted languages.

## soft link / hard link

**1. Hard Links**

- Each hard linked file is assigned the same Inode value as the original, therefore they reference the same physical file location. Hard links more flexible and remain linked even if the original or linked files are moved throughout the file system, although hard links are unable to cross different file systems.
- ls -l command shows all the links with the link column shows number of links.
- Links have actual file contents
- Removing any link, just reduces the link count, but doesn’t affect other links.
- Even if we change the filename of the original file then also the hard links properly work.
- We cannot create a hard link for a directory to avoid recursive loops.
- If original file is removed then the link will still show the content of the file.
- The size of any of the hard link file is same as the original file and if we change the content in any of the hard links then size of all hard link files are updated.
- The disadvantage of hard links is that it cannot be created for files on different file systems and it cannot be created for special files or directories.
- Command to create a hard link is:   


```
ln  [original filename] [link name]
```

**2. Soft Links**

- A soft link is similar to the file shortcut feature which is used in Windows Operating systems. Each soft linked file contains a separate Inode value that points to the original file. As similar to hard links, any changes to the data in either file is reflected in the other. Soft links can be linked across different file systems, although if the original file is deleted or moved, the soft linked file will not work correctly (called hanging link).
- ls -l command shows all links with first column value l? and the link points to original file.
- Soft Link contains the path for original file and not the contents.
- Removing soft link doesn’t affect anything but removing original file, the link becomes “dangling” link which points to nonexistent file.
- A soft link can link to a directory.
- The size of the soft link is equal to the length of the path of the original file we gave. E.g if we link a file like **ln -s /tmp/hello.txt /tmp/link.txt** then the size of the file will be 14bytes which is equal to the length of the “/tmp/hello.txt”.
- If we change the name of the original file then all the soft links for that file become dangling i.e. they are worthless now.
- Link across file systems: If you want to link files across the file systems, you can only use symlinks/soft links.
- Command to create a Soft link is:
  ```
   ln  -s [original filename] [link name]
  ```

### Why is linux more portable than other OS.

Software portability is **the possibility to use the same software in different environments**.

- Linux is lightweight. The requirements for running Linux are much less than other operating systems. In Linux, the memory footprint and disk space are also lower
- Linux is compatible with a large number of file formats as it supports almost all file formats.
- Almost all Linux distributions have **a Live CD/USB** option. It allows us to try or run the Linux operating system without installing it.

## Archive file

In a nutshell, an archive is **a single file that contains a collection of other files and/or directories, we compress files to use less storage space**.

### how to create archives

In linux you can use _tar_ command to create archives of files and directories.
while gzip and bzip2 are used for compression and decompression of files
syntax ->

```shell
tar [options] [filename]
```

### gzip bzip2

gzip and bzip2 are used for archiving and compressing files in linux.

- They both are free and open-source softwares, that use lossless data compression algorithm.
- A lossless compression algorithm means the compressed data is the same after decompressing.
- Gzip uses DEFLATE algorithm and is faster than bzip2

# Vi Editor

Vi is a popular text editor that is commonly used in Unix-based operating systems. It has three main modes: Normal mode, Insert mode, and Command-line mode.

1.  Normal mode: This is the default mode when you open Vi. In Normal mode, you can navigate through the text and perform various operations on it without actually editing the text itself. You can move the cursor using the navigation keys (such as h, j, k, l), perform operations like copying(yanking in vim lang), cutting, pasting, and deleting text using single-character commands, and perform other tasks like searching, replacing, and undoing/redoing changes. Normal mode is used for navigating and managing the text.
2.  Insert mode: In Insert mode, you can directly edit the text in the file by typing characters on the keyboard. You can add, modify, and delete text just like you would in any other text editor. To enter Insert mode from Normal mode, press the "i" key. To exit Insert mode and return to Normal mode, press the "Esc" key or "ctrl + c", well there are many ways to enter normal mode.
3.  Command-line mode: Command-line mode allows you to execute various commands in Vi. This mode is also called "last line mode" as it puts you in the last line of the file when active. You can access Command-line mode from Normal mode by pressing the ":" key. In Command-line mode, you can perform actions like saving changes(:w) to the file, quitting Vi (:q), searching for text, and setting various options. After entering a command, press "Enter" to execute it, and then you will return to Normal mode.

Overall, the three modes of Vi provide different functionalities for navigating, editing, and managing text, making it a powerful text editor for experienced users. It may take some time to get used to the different modes, but with practice, you can become proficient in using Vi for editing text files efficiently.

# Commands

## whoami command

The whoami command **allows Linux users to see the currently logged-in user**.
<br/>

## bc command

**bc** command is used for command line calculator. It is similar to basic calculator by using which we can do basic mathematical calculations.

```shell
echo '25+5'| bc

OUTPUT
30
```

<br/>

## man command

***man*** command in Linux is used to display the user manual of any command that we can run on the terminal. It provides a detailed view of the command which includes `NAME, SYNOPSIS, DESCRIPTION, OPTIONS, EXIT STATUS, RETURN VALUES, ERRORS, FILES, VERSIONS, EXAMPLES, AUTHORS` and `SEE ALSO.`
<br/>

## Info command

**info** command reads documentation in the *info* format. It will give detailed information for a command when compared with the man page. The pages are made using the *texinfo* tools because of which it can link with other pages, create menus and easy navigation.

### difference b/w man and info

1. Info contains a lot more information than Man
2. Man is older and is slowly being replaced by Info
3. Man is displayed when there is no Info documentation found
4. Man is typically a single page while Info is spread across multiple pages
5. Info allows navigation while Man does not
   <br/>

## mv command

**mv** stands for **move**. mv is used to move one or more files or directories from one place to another in a file system like UNIX. It has two distinct functions:

- It renames a file or folder.
- moves a group of files to a different directory.

No additional space is consumed on a disk during renaming. This command normally **works silently** means no prompt for confirmation.

```shell
mv a.txt shivam.txt
```

If the destination file **doesn’t exist**, it will be created. In the above command **mv** simply replaces the source filename in the directory with the destination filename(new name). If the destination file **exist**, then it will be **overwrite** and the source file will be deleted. By default, **mv** doesn’t prompt for overwriting the existing file, So be careful !!

### flags

- -f flag forcefull overrides
  <br/>

## cat command

cat command is used to

- create a file.
- print the content of a file.
- copy the content of a file to another file.
- concatenate content of two files.
  <br/>

## who command

who command is **a tool print information about users who are currently logged in**. who command only see a real user who logged in.
