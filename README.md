# Personal Developer Workspace

This is my personal Linux-based developer workspace where I organize my projects, learning materials, notes, scripts, and backups.

The goal of this workspace is to keep my development and learning activities organized while practicing Linux filesystem and terminal skills.

## Workspace Structure

```text
developer-workspace/
│
├── projects/
│   ├── frontend/
│   ├── backend/
│   └── machine-learning/
│
├── learnings/
│   ├── linux/
│   │   └── linux-note.md
│   ├── dsa/
│   └── machine-learning/
│
├── notes/
│   ├── commands.md
│   └── ideas.md
│
├── scripts/
│
├── backups/
│
└── README.md
```

## What I Practiced

### Linux Filesystem

* [x] Created directories using `mkdir`
* [x] Created files using `touch`
* [x] Navigated directories using `cd`
* [x] Checked the current location using `pwd`
* [x] Listed files using `ls`
* [x] Used `ls -la` to view hidden files
* [x] Moved files using `mv`
* [x] Renamed files using `mv`
* [x] Deleted files using `rm`
* [x] Found files using `find`

### File Management

I practiced the complete workflow:

```text
Create → Rename → Move → Find
```

For example:

```bash
touch temp.md
mv temp.md linux-note.md
mv linux-note.md ../learnings/linux
find . -name "*.md"
```

## Important Commands Learned

| Command | Purpose                      |
| ------- | ---------------------------- |
| `pwd`   | Show current directory       |
| `ls`    | List files and directories   |
| `cd`    | Change directory             |
| `mkdir` | Create directory             |
| `touch` | Create an empty file         |
| `cp`    | Copy files/directories       |
| `mv`    | Move or rename files         |
| `rm`    | Delete files                 |
| `rmdir` | Remove empty directories     |
| `find`  | Search for files/directories |
| `nano`  | Edit files from the terminal |
| `cat`   | Display file contents        |

## Mistakes I Encountered

### 1. Incorrect `find` syntax

I initially used:

```bash
find .name "*.md"
```

This was incorrect.

The correct syntax is:

```bash
find . -name "*.md"
```

The `.` tells `find` to start searching from the current directory.

### 2. Moving a file into the wrong location

I accidentally moved `linux-note.md` into:

```text
notes/learnings
```

instead of:

```text
learnings/linux
```

I fixed it by removing the incorrectly created file/directory and then using:

```bash
mv linux-note.md ../learnings/linux
```

This helped me understand relative paths better.

### 3. `cd` only works with directories

I tried:

```bash
cd learnings
```

when `learnings` was actually a file.

The terminal returned:

```text
Not a directory
```

This helped me understand the difference between files and directories.

## What I Learned

The main thing I learned from this project is how Linux organizes files and directories and how I can navigate and manipulate them entirely from the terminal.

I also learned that relative paths such as:

```bash
.
..
../learnings/linux
```

are extremely useful when working inside a project.

## Goal

I want to become a strong software engineer by building real projects and continuously improving my skills in:

* Linux
* Backend Development
* Frontend Development
* DSA
* Machine Learning
* Git & GitHub
* Cloud & DevOps

## Next Steps

* [ ] Learn Linux file permissions
* [ ] Learn `chmod`
* [ ] Learn `chown`
* [ ] Understand `rwx`
* [ ] Learn environment variables
* [ ] Practice shell commands
* [ ] Learn Bash scripting
* [ ] Connect this workspace with GitHub
* [ ] Continue building projects

