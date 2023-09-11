# Linux Commands

## cat - To display content of file
**cat -b [fileName]** - to add line number to non empty lines.
**cat -n** - To add line number to all lines.
**cat -e** - To add dollar at end of line.
--------------------------------------
**man** - This command is used to get the details of other commands.
Ex- man ls ,This is show the syntax and description of ls command
.

**clear** - To clear terminal.

**pwd** - To show the current working directory.

**cd** - To change working directory

**echo** - To prints anything on terminal. Ex- echo "Hello, world"

**whoami** - To show the current user.

**su or sudo bash** - To switch to root user.

**su [specific user name]** - To switch to specific user.

**sudo** - It can be used to run any command which needs a special permission.For example:- sudo useradd [name of user]. to add user

**useradd** - To add user. Ex- sudo useradd sameer

**passwd** - To add password to user.Ex- sudo passwd sameer

**userdel** - To delete the user. Ex- sudo userdel sameer.

**touch** - To create a file. Ex- touch index.js

**cp** - To copy a file. Ex- cp [flags] [source path] [target path].
**Flags for cp**
-n - To avoid overwriting if the file is present with that name it will not copy that file again.
-u - To copy file only if it is different from target destination.
-R
