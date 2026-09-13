# Day 1

* [x] Learned basic Linux filesystem navigation
* [x] Used the Ubuntu terminal through WSL
* [x] Learned how to create and remove files
* [x] Learned how to create and remove directories
* [x] Learned `ls` and `ls -la`
* [x] Learned `pwd`
* [x] Learned `cd`
* [x] Learned `mkdir`
* [x] Learned `touch`
* [x] Learned `rm`
* [x] Learned `rmdir`
* [x] Learned `cp`
* [x] Learned `mv`
* [x] Learned `find`
* [x] Learned `sudo`
* [x] Learned `history`
* [x] Practiced file and directory operations

## What I learned

Today I practiced the basic Linux terminal commands using Ubuntu 24.04 on WSL 2.

### Navigation

```bash
pwd
```

Shows the current working directory.

```bash
ls
```

Lists files and directories.

```bash
ls -la
```

Lists all files and directories, including hidden files, with detailed information.

```bash
cd folder
```

Moves into a directory.

```bash
cd ..
```

Moves to the parent directory.

### Creating files and directories

```bash
mkdir folder
```

Creates a directory.

```bash
touch file.txt
```

Creates an empty file.

### Removing files and directories

```bash
rm file.txt
```

Removes a file.

```bash
rmdir folder
```

Removes an empty directory.

I learned that `rm folder` does not remove a directory because `rm` without options is intended for files.

### Copying files

```bash
cp source.txt destination.txt
```

Copies a file and can also be used to rename it while copying.

```bash
cp file.txt backup/
```

Copies a file into another directory.

### Moving and renaming

```bash
mv file.txt backup/
```

Moves a file into another directory.

```bash
mv old.txt new.txt
```

Renames a file.

```bash
mv ap.txt backup/note.txt
```

Moves a file into `backup` and renames it at the same time.

### Finding files and directories

```bash
find linux-learning
```

Searches/traverses the specified directory and displays its contents.

I also learned that:

```bash
find a
```

produces an error if the specified path does not exist.

### Permissions

```bash
sudo -v
```

I learned that `sudo` allows commands to be executed with elevated privileges and that Linux may ask for the user's password.

I also learned that `sudo` does not change what a command does. For example:

```bash
sudo rm linux
```

still cannot remove a directory without the appropriate recursive option.

### Command history

```bash
history
```

Displays previously executed commands in the terminal.

## What was difficult

* Understanding why `rm linux` did not remove a directory.Because it is used to remove files not directory.
* Understanding the difference between `rm` and `rmdir`.rmdir works when that directory is empty.
* Understanding why `sudo rm linux` still gave the same error.
* Initially using `cd linux learning` and learning that spaces separate command arguments.
* Understanding that `cd Desktop` only works when a `Desktop` directory exists inside the current directory.
* Making sure the source and destination paths are correct when using `cp` and `mv`.
* Typing directory names correctly (`backup` vs `bacakup`).

## Important commands learned

| Command   | Purpose                                  |
| --------- | ---------------------------------------- |
| `pwd`     | Show current directory                   |
| `ls`      | List files and directories               |
| `ls -la`  | List all files with detailed information |
| `cd`      | Change directory                         |
| `cd ..`   | Go to parent directory                   |
| `mkdir`   | Create directory                         |
| `touch`   | Create file                              |
| `rm`      | Remove file                              |
| `rmdir`   | Remove empty directory                   |
| `cp`      | Copy files/directories                   |
| `mv`      | Move or rename files/directories         |
| `find`    | Search for files/directories             |
| `sudo`    | Execute command with elevated privileges |
| `history` | Show command history                     |
|  `/mnt/d` | To navigate from C-Drive to D-Drive      |

## Practice

I created a `linux-learning` directory and practiced:

```bash
mkdir linux-learning
cd linux-learning

touch ap.txt
cp ap.txt as.txt

mkdir backup
cp ap.txt backup/

mv as.txt backup/

mv ap.txt backup/note.txt

cd backup
ls
```

Final structure:

```text
linux-learning/
└── backup/
    ├── ap.txt
    ├── as.txt
    └── note.txt
```

## Questions

* Why rm doesn't work for a directory even with sudo?
* why rmdir works only when a directory is empty?
* What command is used for remove a directory which is not empty?
