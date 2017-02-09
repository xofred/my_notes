Linux has inherited from UNIX the concept of ownerships and permissions for files. This is basically because it was conceived as a networked system where different people would be using a variety of programs, files, etc. Obviously, there's a need to keep things organized and secure. We don't want an ordinary user using a program that could potentially trash the whole system. There are security and privacy issues here as well. Let's face it, we don't want Bill to read Bob's love letters to the Janet who works in R & D. (because Janet is Bill's fiance) In the end, it's important to know what belongs to me, to you and to everybody.

As we mentioned at the beginning of this course, the big advantage that Linux has is its multi-user concept- the fact that many different people can use the same computer or that one person can use the same computer to do different jobs. That's where the system of file permissions comes in to help out in what could be a very confusing situation. We're going to explain some basic concepts about who owns the file and who can do what with a file. We won't get into an enormous amount of detail here. We'll save that for the Linux system administration course. We will show you how to understand file permission symbols and how to modify certain files so that they're more secure.

File permission symbols

If you run the command

```
ls -l
```
in your home directory, you will get a list of files that may include something like this


```
-rw-r--r--  1  bob  users  1892  Jul 10  18:30 linux_course_notes.txt
```
This basically says, interpreting this from RIGHT to LEFT that the file, linux_course_notes.txt was created at 6:30 PM on July 10 and is 1892 bytes large. It belongs to the group users (i.e, the people who use this computer). It belongs to bob in particular and it is one (1) file. Then come the file permission symbols.

Let's look at what these symbols mean:

The dashes - separate the permissions into three types


The first part refers to the owner's (bob's) permissions.

The dash - before the rw means that this is a normal file that contains any type of data. A directory, for example, would have a d instead of a dash.

The rw that follows means that bob can read and write to (modify) his own file. That's pretty logical. If you own it, you can do what you want with it.

The second part of the these symbols after the second dash, are the permissions for the group. Linux can establish different types of groups for file access. In a one home computer environment anyone who uses the computer can read this file but cannot write to (modify) it. This is a completely normal situation. You, as a user, may want to take away the rights of others to read your file. We'll cover how to do that later.

After the two dashes (two here because there is no write permissions for the group) come the overall user permissions. Anyone who might have access to the computer from inside or outside (in the case of a network) can read this file. Once again, we can take away the possibility of people reading this file if we so choose.

Let's take a look at some other examples. An interesting place to look at different kinds of file permissions is the /bin directory. Here we have the commands that anybody can use on the Linux system. Let's look at the command for gzip, a file compression utility for Linux.

```
-rwxr-xr-x  1 root    root        53468 May  1  1999 gzip
```
As we see here, there are some differences.

The program name, date, bytes are all standard. Even though this is obviously different information, the idea is the same as before.

The changes are in the owner and group. Root owns the file and it is in the group "root". Root is actually the only member of that group.

The file is an executable (program) so that's why the letter x is among the symbols.

This file can be executed by everybody: the owner (root), the group (root) and all others that have access to the computer

As we mentioned, the file is a program, so there is no need for anybody other than root to "write" to the file, so there is no w permissions for it for anybody but root.

If we look at a file in /sbin which are files that only root can use or execute, the permissions would look like this:

```
-rwxr--r--  1 root    root        1065 Jan 14  1999 cron
```
'cron' is a program on Linux systems that allows programs to be run automatically at certain times and under certain conditions. As we can see here, only root, the owner of the file, is allowed to use this program. There are no xpermissions for the rest of the users.

We hope you enjoyed this little walk-through of file permissions in Linux. Now that we know what we're looking for, we can talk about changing certain permissions.

chmod

chmod is a Linux command that will let you \&quot;set permissions\&quot; (aka, assign who can read/write/execute) on a file.

```
chmod permissions file
```
```
chmod permission1_permission2_permission3 file
```
When using chmod, you need to be aware that there are three types of Linux users that you are setting permissions for. Therefore, when setting permissions, you are assigning them for yourself, "your group" and "everyone else" in the world. These users are technically know as:
```
Owner
Group
World
```
Therefore, when setting permissions on a file, you will want to assign all three levels of permissions, and not just one user.

Think of the chmod command actually having the following syntax...

chmod owner group world FileName

Now that you understand that you are setting permissions for THREE user levels, you just have to wrap your head around what permissions you are able to set!

There are three types of permissions that Linux allows for each file.
```
read
write
execute
```
Putting it all together:

So, in laymen terms, if you wanted a file to be readable by everyone, and writable by only you, you would write the chmod command with the following structure.

COMMAND : OWNER : GROUP : WORLD : PATH

chmod read & write read read FileName

### (Here it comes the inportant)
```
chmod 644 myDoc.txt
```
Wait! What are those numbers?!?

Computers like numbers, not words. Sorry. You will have to deal with it. Take a look at the following output of `ls -l`

```
-rw-r--r-- 1 gcawood iqnection 382 Dec 19 6:49 myDoc.txt
```
You will need to convert the word read or write or execute into the numeric equivalent (octal) based on the table below.
```
4 read (r)
2 write (w)
1 execute (x)
```
Practical Examples
```
chmod 400 mydoc.txt read by owner
chmod 040 mydoc.txt read by group
chmod 004 mydoc.txt read by anybody (other)
chmod 200 mydoc.txt write by owner
chmod 020 mydoc.txt write by group
chmod 002 mydoc.txt write by anybody
chmod 100 mydoc.txt execute by owner
chmod 010 mydoc.txt execute by group
chmod 001 mydoc.txt execute by anybody
```
Wait! I don't get it... there aren't enough permissions to do what I want!

Good call. You need to add up the numbers to get other types of permissions...

So, try wrapping your head around this!!
```
7 = 4+2+1 (read/write/execute)
6 = 4+2 (read/write)
5 = 4+1 (read/execute)
4 = 4 (read)
3 = 2+1 (write/execute)
2 = 2 (write)
1 = 1 (execute)
```
```
chmod 666 mydoc.txt read/write by anybody! (the devil loves this one!)
chmod 755 mydoc.txt rwx for owner, rx for group and rx for the world
chmod 777 mydoc.txt read, write, execute for all! (may not be the best plan in the world...)
```
Good luck! Hope this helps.