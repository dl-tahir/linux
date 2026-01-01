Changing the Permissions of a Directory
Changing permissions for directories works similarly to changing permissions for files. Let's practice by creating a new directory and modifying its permissions. Directory permissions control who can list the directory's contents, create new files within the directory, and access files already in the directory.

First, let's create a new directory and set some non-standard permissions:

```
mkdir ~/test-dir
chmod 700 ~/test-dir
```

Now, let's check the current permissions:

```
ls -ld ~/test-dir
```

The -d option in ls -l tells ls to list the directory itself, rather than its contents. Without -d, ls would list the files and subdirectories inside test-dir, which is empty right now. You should see:

```
drwx------ 2 labex labex 4096 Jul 29 15:45 /home/labex/test-dir
```

The d at the beginning indicates that it's a directory. The rwx------ indicates that the owner has read, write, and execute permissions, while the group and others have no permissions. For directories:

Read permission (r) allows you to list the contents of the directory using ls.
Write permission (w) allows you to create new files and subdirectories within the directory.
Execute permission (x) allows you to access files and subdirectories within the directory (i.e., cd into it).
Now, let's change the permissions:

```
chmod -R 755 ~/test-dir
```

In this command:

-R applies the change recursively to all files and subdirectories (though our directory is empty in this case). It's good practice to include it when dealing with directories, even if they're currently empty, in case you add files later.
755 gives read, write, and execute permissions to the owner, and read and execute permissions to group and others.
Let's break down 755:

Owner (7): Read (4) + Write (2) + Execute (1) = 7
Group (5): Read (4) + Execute (1) = 5
Others (5): Read (4) + Execute (1) = 5
Let's verify the change:

```
ls -ld ~/test-dir
```

You should now see:

```
drwxr-xr-x 2 labex labex 4096 Jul 29 15:45 /home/labex/test-dir
```

This clearly shows the change in permissions, from only the owner having access (700) to the owner having full access while others can read and execute (755). 
Now, anyone can list the contents of test-dir and access files within it, but only the owner can create new files or modify existing ones.
