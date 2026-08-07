# Linux Fundamentals (Part 1–3)

## Overview
Core Linux command-line skills — navigating the file system, managing files/permissions, 
using SSH, text editors, downloading/transferring files, and process management.

## Interacting with the File System
- `ls`, `cd`, `pwd`, `cat` — basic navigation and viewing commands
- `find . -name <filename>` — locate a file's full path
- `&` — run a command in the background of the terminal
- `&&` — combine multiple commands into one line
- `>` — redirect output (overwrite a file)
- `>>` — same as `>` but appends instead of replacing
  - Example: `echo key > dell` then `echo lock >> dell` → `dell` now contains both `key` and `lock`

## SSH (Secure Shell)
SSH is an encrypted protocol between devices. Any input sent in human-readable format is 
encrypted before travelling over the network, and decrypted at the destination.
- Allows remote command execution on another device
- All data sent between devices is encrypted in transit

## Core File Commands
- `ls -a` — show hidden files | `ls --help` — show more options
- `man` — access command documentation
- `touch` — create a file | `mkdir` — create a directory
- `cp` — copy a file/folder | `mv` — move a file/folder
- `rm <file>` — remove a file | `rm -R <folder>` — remove a folder recursively
- `file <filename>` — determine a file's type

## File Permissions
Symbolic format: `rwx rwx rwx` (Owner / Group / Others)

Numeric values: Read = 4, Write = 2, Execute = 1

| Symbolic | Numeric | Meaning |
|---|---|---|
| `rwxrwxrwx` | 777 | Owner can do everything |
| `rw-r--r--` | 644 | Owner can read/write, others can only read |
| `rwx------` | 700 | Only the owner has access |

## Key Directories
- **/etc** — root directory, commonplace where all system files are stored by the OS
- **/var** — "variable data," stores data frequently accessed/written by services (e.g. logs)
- **/root** — home directory for the root system user
- **/tmp** — volatile, unique directory used to store data only needed once or twice

## Text Editors
- **Nano**: `nano <filename>` — simple editor; supports searching text, copy/paste, jumping to line numbers
- **Vim**: More advanced, customizable keyboard shortcuts, syntax highlighting (popular with developers) — steeper learning curve but works on all terminals

## Downloading & Transferring Files
- `wget <url>` — download files from the web via HTTP without a browser
- **SCP (Secure Copy)**: Securely transfers files between two computers using the SSH protocol (auth + encryption)
  - `scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt` — copy local → remote
  - `scp ubuntu@192.168.1.30:/home/ubuntu/document.txt notes.txt` — copy remote → local

## Serving Files from Your Host (Web)
- `python3 -m http.server` — turns your machine into a quick HTTP server
- On another machine: `wget http://<ip-address>:8000/<filename>` to download

## Viewing & Managing Processes
- `ps` — view your own processes | `ps aux` — view processes from all users
- `top` — view processes in real-time
- `kill <PID>` — stop a process by its Process ID
  - `SIGTERM` — kill gracefully, allows cleanup before termination
  - `SIGKILL` — force kill, no cleanup
  - `SIGTOP` — stop/suspend a process

## Starting Processes/Services at Boot
- `systemctl` — interact with the systemd process/daemon
  - Format: `systemctl [option] [service]`
  - Example: `systemctl start apache2`
  - Five actions: Start, Stop, Enable, Disable, Status

## Background & Foreground Processes
- Processes can run in the background or foreground (e.g. `echo` runs in the foreground and shows output immediately)
- **Cron**: A process started at boot responsible for facilitating and managing scheduled jobs (cron jobs)
  - `MIN HOUR DOM MON DOW CMD` — minute, hour, day of month, month, day of week, and the command to execute


These Linux fundamentals — file permissions, SSH, process management, and cron — form 
the operational backbone for penetration testing, since most VAPT tooling and target 
enumeration happens through the Linux command line.
