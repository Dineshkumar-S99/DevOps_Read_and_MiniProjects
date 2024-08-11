1. [Intro to Linux](notion://www.notion.so/Linux-4f346b3c0e1f4743ac66bb98e07b5cad#Intro-to-Linux)
2. [Basic CLI commands](notion://www.notion.so/Linux-4f346b3c0e1f4743ac66bb98e07b5cad#Basic-CLI-commands)
3. [Understanding Files in Linux](notion://www.notion.so/Linux-4f346b3c0e1f4743ac66bb98e07b5cad#Understanding-files-in-linux)
4. [Filters and IO Redirection](notion://www.notion.so/Filters-and-IO-Redirection)
5. [Users and Groups](notion://www.notion.so/users-and-groups)
6. [Sudo](notion://www.notion.so/sudo)
7. Software management
8. Services and Processes
9. extra commands
10. server management

## Intro to Linux

1984: GNU Project and the free software foundation creates open source version of UNIX utilities under General Public License(GPL - software license enforcing open source principles)
1991: Linux Torvalds creates UNIX like kernel and released under GPL and ports some GNU utilities and solicits assistance online
today: Linux kernel + GNU utilities = complete open source Unix like OS and packaged for targeted audiences as distributions

### Open Source

```
Open Source software is software where anyone can inspect the source code, modify and enhance them.
(i.e: only the code is freely available but the software might sometimes be paid)

```

### Linux Principles:

- Everything is a file in Linux - including the hardware
- mostly we have small single purpose programs
- ability to chain programs together for complex operations
- avoid captive users Interface
- configuration data stored in text file

### why linux?

- It's open source and supports wide variety of Hardware
- has great community support
- have more customization and many servers runs on Linux
- Automation is easy in Linux and higly secure at the same time

### Linux distros

- for Desktop
    - ubuntu (debian based)
    - mint
    - fedora (RPM based)
    - open suse (RPM based)
- for servers
    - RHEL (Red Hat Enterprise Linux)
    - Ubuntu server
    - CentIOS (same as RHEL but open sourse)
    - SUSE Enterprise Linux
    
    based comes like
    
    - RPM based
        - CentOS or RHEL
        - Fedora
        - Open SUSE
        - Oracle Linux
        - Amzon Linux
    - Debian
        - Ubuntu
        - Kali Linux
    - Pacman based
    
    These where are different families called because they all have different pacakaging methods. i.e: like exe,msi,deb
    
    so mostly we choose RHEL for servers (so it will be stable) and to learn automation and others we use Ubuntu so we have latest packages
    
    > note : here we don't have just software differences but also command differences
    > 
- RedHat:
    - .rpm
    - installing packages named google-chrome-stable-57.0.29-1.x86_64.rpm
        - rpm -ivh google-chrome-stable-57.0.29-1.x86_64.rpm
- debian :
    - .deb
    - installing package named google-chrome-stable-57.0.29-1.x86_64.deb
        - deb -i google-chrome-stable-57.0.29-1.x86_64.deb

### Directory Structures in Linux

> Directories are nothing but folders
> 
- Home Directories:
    - /root
    - /home/username
- User Executable:
    - /bin (contains every commands that user could execute)
    - /usr/bin
    - /usr/local/bin
- System Executables:
    - /sbin
    - /usr/sbin
    - /usr/local/sbin
- mountpoints:
    - /media
    - /mnt
- configuration:
    - /etc
- temporary files:
    - /tmp (have the temporary files mostly use when we automate some tasks)
- kernals and bootloaders:
    - /boot (we have our image and grub directories(used for configuration for booting) in it)
- Server data:
    - /var
    - /srv
- system Information:
    - /proc (mostly these are dynamic files changes based on system information eg: uptime -> shows how long the system been up and running)
    - /sys
- Shared Libraries:
    - /lib
    - /usr/lib
    - /usr/local/lib

## Basic CLI commands

here we have commands options arguments
i.e: cp -r devops backupdev/
here cp - command
-r - option
devops backupdev/ - arguments

| command | description |
| --- | --- |
| pwd | print working directory i.e:where are you in dir |
| whoami | shows the user names |
| command --help | to know the options available and to open manual for that command |
| ls | list all the contents in the directory |
| ls -l | list in long format that is every info like file type, time and permissions note: this will show files list in alphabetical order |
| ls -lt | this will short them according to the time stamp i.e: recently created to old |
| ls -ltr | now this will short them in reverse |
| ls -a | list all the contents including system and hidden files |
| cat filename.extension | to read the file contents |
| sudo -i | to switch to the super user do or admin |
| exit | to logout from sudo -i and back to normal user |
| mkdir foldername | to create a directory |
| mkdir -p f1/f2/f3/f4 | this can be used to create folders recursively thought the folders are crated before or not |
| touch filename.extension | to create files with extension to exact file format |
| cp source destination | to copy file from one place to another |
| cp -r | to copy files recursively |
| mv source destination | to move a file or to rename file or dir |
| mv star.extension | to move files only with the particular extension |
| rm | to remove the file |
| rm -r | to remove the dir |
| rm -rf | to remove everything forcefully i.e: here there is no recovery straight only disk restoration |
| rm -r /star | to remove only directories |
| rmdir | to remove the empty dir |
| history | to see all the commands we have executed |
| vim filename.extension | to open a file in vim editor |
| vi filename.extension | to open a file in vi editor |
| ln -s source destination | to create a soft link |
| unlink filewanttounlink | this one is used to unlink the file that is linked before |
| file filepath | to know the file type like text, binary etc |
|  |  |

> one hiphen for single letter options and
-- two hiphens for whole word options
> 

> star means everything
. -> dot means current
.. -> before or parent dir
> 

> we can also read the prompt and know what user you are like
e.g: vagrant@localhost - normal user (~)
root@localhost - root user (#)
> 

> to change the hostname -> vim/etc/host  and change thyhe name and save it then
cmd -> hostname newNamewegave
now logout and login we can see the new hostname
> 

> absolute path -> the one start with root directory
e.g: /bin/ -> if we move in and give ls we can see all the commands we have
relative path  -> path from where we are
e.g: bin/
> 

> cd -> just cd without location or dir will move us to home directory. or cd ~
> 

> to create multiple files with same name we can use
touch filename{n..n}.extension
eg: touch file{1..10}.txt -> now txt files named file1,file2 till file10 will be created
> 

> vim editor is an enhanced vi editor which is an text based editor. defaultly we don't have vi editor we have to install it (for centOS) ubuntu it is defaultly installed.
cmd -> sudo yum install vim -y -> in centOS
> 

```
it has three modes :
1. command mode -> esc
	1. /searchingwords -> to search the word is present or not and it is case sensitive.
	2. gg To go to the beginning of the page
	3. G To go to end of the page
	4. w To move the cursor forward, word by word
	5. b To move the cursor backward, word by word
	6. nw To move the cursor forward to n words (SW)
	7. nb To move the cursor backward to n words {SB)
	8. u To undo last change (word)
	9. U To undo the previous changes (entire line)
	10. Ctrl+R To redo the changes
	11. VY To copy a line
	12. nyy To copy n lines (Syy or 4yy)
	13. p To paste line below the cursor position
	14. P To paste line above the cursor position
	15. dw To delete the word letter by letter {likeBackspace}
	16. x To delete the world letter by letter (like DEL Key)
	17. dd To delete entire line
	18. ndd To delete n no. of lines from cursor position{Sdd)
	19. / To search a word in the file.
2. Insert mode (edit mode) -> press i to insert or o -> it will drop one level down that is to next line
3. extended command mode -> :wq to write and quit or :w to write and :q to quit and :q! -> means forcefully quiting it without saving
:se nu -> set numbers now it will show the line numbers
Esc+:w To Save the changes
Esc+:q To quit (Without saving)
Esc+:wq To save and quit
Esc+:w! To save forcefully
Esc+wq! To save and quit forcefully
Esc+:x To save and quit
Esc+:X To give passw or d to the file and remove password
Esc+:20(n) To go to line no 20 or n
Esc+: se nu To set the line numbers to the file
Esc+:se nonu To Remove the set line numbers

```

## Understanding files in linux

- regular files (like text, data or executable files)
- d directory
- l link (shortcut that points to the location of actual file)
- c special files(character files mechanism used for input and output such as files in /dev like keyboards,mouse )
- b block file (like our ssd, storages etc)
- s socket (a special file that rpovides inner-process networking protected by the file system access control)
- p pipe (a special file that allows processes to communicate with each other without using network socket semantics)

## Fileters and IO redirection

grep command is used to find the particular pattern in the file. i.e: to look for a file

| command | description |
| --- | --- |