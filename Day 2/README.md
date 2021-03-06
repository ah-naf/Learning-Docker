# Why Do We Need Linux Command?
Docker foundation is build on basic Linux concepts. To troubleshoot issues and speed up our development process we need to know some of the basic linux command. In fact, every tutorial in online is based on linux command.

# What is Linux?
Linux is a Unix-like, open source and community-developed operating system (OS) for computers, servers, mainframes, mobile devices and embedded devices. It is supported on almost every major computer platform, including x86, ARM and SPARC, making it one of the most widely supported operating systems.

# What is Linux Distribution?
A Linux distribution is an operating system composed of the Linux kernel, GNU tools, additional software and a package manager. It may also include display server and desktop environment to be used as regular desktop operating system.

The term is Linux distribution (or distro in short form) because an entity like Debian or Ubuntu ‘distributes’ the Linux kernel along with all the necessary software and utilities (like network manager, package manager, desktop environments etc) so that it can be used as an operating system.

Your distributions also takes the responsibility of providing updates to maintain the kernel and other utilities.

So, Linux is the kernel whereas the Linux distribution is the operating system. This is the reason why they are also sometime referred as Linux-based operating systems.

# Linux is just a kernel not an operating system
You might have come across that phrase and that’s entirely correct. The kernel is at the core of an operating system and it is close to the actual hardware. You interact with it using the applications and shell.

![linux_structure](distro1.webp)

To understand that easily, think of operating systems as vehicles and kernal as engines. You cannot drive an engine directly. Similarly, you cannot use kernel directly.

![linux_kernel](distro2.png)

A Linux distribution can be seen as a vehicle manufacturer like Toyota or Ford that provides you ready to use cars just like Ubuntu or Fedora distributions provide you a ready to use operating systems based on Linux.

<details>
<summary>
Some of the linux distros are
</summary>

- Ubuntu
- Debian
- Alpine
- Fedora
- CentOS
</details>

We will use ubuntu in this section.

# Running Linux
1. Goto hub.docker.com
2. Search for Ubuntu.
3. Copy the pull command. (It might show <code>**docker pull ubuntu**</code> )

We will not use the **pull** command. Instead of using **pull** command we will use **run** command. By using **run** command, it will search for the ubuntu image and if it doesn't find it locally, then it will pull the image from docker-hub and start the container.
```
docker run ubuntu
```
After running this command, what will happen?

It ain't doing anything. We know that, after running the **run** command it will start a container. But where is it? Did the container even started?

Of course, it did run. Docker did started a container. Because we didn't interact with that container it stopped immediately.

We can confirm that the container started by executing
```sh
# List of running container
docker ps # shows nothing
# List of all container
docker ps -a # shows all containers including stopped one
```

To start a container and interact with it, we have to execute
```sh
docker run -it ubuntu
```
After running this command, we will see a shell prompt in terminal.
<details>
<summary>What is shell?</summary>

```
A shell is a program that takes our command and pass it to the operating system for execution.
```
</details>

It might show something like this
```sh
root@2fsdsnf3djk:/# 
```
The first part **root** represents the currently logged in user. Currently, we are logged in as root user which have highest privilages. After the '**@**' we have the name of the machine which is automatically generated by Docker. After the '**:**' sign we have '**/**' sign, which represents where we are in file system. '**/**' represents root directory, which is the highest directory in file system.

# Managing Packages in Ubuntu
**apt** (Advance Package Tool) is the package manager for ubuntu.
<details>
<summary>Some of the apt commands are</summary>

```sh
  list - list packages based on package names
  search - search in package descriptions
  show - show package details
  install - install packages
  reinstall - reinstall packages
  remove - remove packages
  autoremove - Remove automatically all unused packages
  update - update list of available packages
  upgrade - upgrade the system by installing/upgrading packages
  full-upgrade - upgrade the system by removing/installing/upgrading packages
  edit-sources - edit the source information file
  satisfy - satisfy dependency strings
```
</details>

Let'us install nano in ubuntu. nano is a basic text-editor for linux. If execute ""nano"", we will get an error
```sh
nano
# bash: nano: command not found
```
which means, we doesn't have nano installed in our ubuntu image. If we execute 
```sh
apt install nano
# E: Unable to locate package nano
```
Why is this happening? We have a package list in ubuntu. We can install the package if the list contains it. We can see the list by executing
```sh
apt list
```
To install a package we have to update the package list. After updating it we can install nano. 
```sh
apt update
# Then
apt install nano
```
Make sure this package is installed by executing **nano** command. If everything goes right, it will show a text-editor in terminal.

We can remove nano from ubuntu by executing
```
apt remove nano
```

# Linux Commands
## Basic Commands
---
| Command | Description |
| ------- | ----------- |
| ***ls***| Lists all files and directories in the present working directory |
| ***ls -R***| 	Lists files in sub-directories as well |
| ***ls -a***| 	Lists hidden files as well |
| ***cd ~***| 	Navigate to HOME directory |
| ***cd ..***| 	Move one level up |
| ***cd /***| 	Navigate to root directory |
| ***history***| 	Gives a list of all past commands typed in the current terminal session |
| ***mkdir directoryname***| Creates a new directory in the present working directory or a at the specified path |
| ***mv filename new_file_name***| Renames the file to a new filename |
| ***mv file filepath***| Moves the files to the new location |
| ***rm filename***| Deletes a file |
| ***rm -r directory***| Recursively deletes a directory that contains inner file |
| ***touch filename***| Create a new empty file |
| ***cat filename***| Displays the file content |
| ***more filename***| Displays and paginate file content. Can only scroll down. |
| ***less filename***| Displays and paginate file content. We have to install it first. |
| ***head filename***| Show first 10 lines of file content |
| ***tail filename***| Show last 10 lines of file content |

## Redirection
---
One of the important concept in linux is the concept of standard input and output. Standard input represents the keyboard and standard output represents the screen. We can always change the source of input and output which is known as **redirection**.

***> and <*** is known  as redirection operator. ***>*** is used to redirect standard output and ***<*** is used to redirect standard input.

| Command | Description |
| ------- | ----------- |
| ***cat file1 file2 > file3***| Joins two files (file1, file2) and stores the output in a new file (file3) |
| ***echo hello > file1***| Instead of printing hello in terminal, it will store the output in file1 |
| ***ls -a > file1***| Store all the filelist in file1 |

## Search File
---
| Command | Description |
| ------- | ----------- |
| ***grep pattern filename***| Search for pattern in files |
| ***grep -i pattern filename***| Case insensitive search |
| ***grep -i -r pattern directory***| Recursively search pattern in the directory |
| ***grep -i pattern filename***| Case insensitive search |
| ***find root***| It will show all the files and directory that are inside of root directory |
| ***find home -type d***| It will show all the directories that are inside of home directory |
| ***find home -type f***| It will show all the files that are inside of home directory |
| ***find home -type f -name 'file.txt'***| Find file by name in home directory |
| ***find home -type f -iname 'file.txt'***| Find file by name in home directory (case-insensitive) |

## Chaining Commands
---
- ### Ampersand Operator (&)
  The ampersand operator (&) is used to run commands in the background. When you append "&" at the end of any command, the command will be executed in the background. You can even use "&" to run multiple commands in the background.

  Run a single command with “&”:
  ```sh
  sleep 10 &
  ```
  Run multiple commands simultaneously using “&”:
  ```sh
  command1 & command2 & command3 &
  ```

- ### Logical And Operator (&&)
  When you use the “&&” operator, you're instructing the system to run the second command only if the first command runs successfully. Thus, if the exit code of the first command doesn’t return “0”, then the second command won’t run.
  ```sh
  command1 && command2
  ```
  If command 1 returns a “0” error code, then command 2 will run; otherwise, the script stops.

- ### Logical OR Operator (||)
  This operator is used when you aren't sure that the first command will execute successfully. Thus, the OR command can be used for the second command to instruct it to perform what the first command couldn’t do. If the first command get execute, then the second command won't execute
  ```sh
  mkdir hello || echo hello
  ```

- ### Semicolon Operator (;)
  It is used to run multiple commands sequentially in a single go. But it is important to note that the commands chained by (;) operator always executes sequentially. If two commands are separated by the operator, then the second command will always execute independently of the exit status of the first command. Unlike the ampersand operator, the execution of the second command is independent of the exit status of the first command. Even if the first command does not get successfully executed i.e, the exit status is non-zero, the second command will always execute.
  ```sh
  who;pwd;ls
  ```

- ### Piping (|) Operator
  This operator sends the output of the first command to the input of the second command.
  ```sh
  ls -l | wc -l
  ```
  In the above command wc -l displays the number of lines. ls -l displays the lists the files in the system.  The first command displays the number of files in the directory. ls – l lists the names of the files and this output is sent to the next command which counts the number of lines in the input. As a result, by using pipe we get the number of files in the directory.