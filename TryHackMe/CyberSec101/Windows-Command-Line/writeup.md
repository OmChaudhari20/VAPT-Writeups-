# Windows Command Line

## Overview
Covers the Command Prompt (CMD) — its benefits over GUI, and core commands for network 
configuration, troubleshooting, file/disk management, and process management.

## Benefits of Using CMD
1. **Lower resource usage**: CLI requires fewer system resources than GUI — useful on older 
   hardware, limited memory systems, or cloud computing (lower resource usage = lower cost)
2. **Automation**: CLI tasks can be automated by creating a batch file/script with the needed commands
3. **Remote management**: CLI makes it convenient to use SSH to manage a remote system 
   (server, router, IoT device) — works well on slow network speeds and limited-resource systems

## General Commands
- `set` — check your PATH from the command line
- `ver` — determine the OS version
- `systeminfo` — list various info about the system
- `driverquery` — list installed drivers
- `help` — provides help info for a specific command
- `cls` — clear the screen

## Network Configuration
- `ipconfig` — check network info
- `ipconfig /all` — more detailed configuration info

## Network Troubleshooting
- `ping` — checks network reachability by sending an ICMP packet and listening for a response
- `tracert <target name>` — traces the network route to a target, showing routers on the path
- `nslookup` — looks up a host/domain and returns its IP address
  - `nslookup example.com` — uses the default name server
  - `nslookup example.com 1.1.1.1` — uses a specified name server
- `netstat` — displays current network connections and listening ports
  - `-a` — display all connections & listening ports
  - `-b` — show the program associated with each listening port/connection
  - `-o` — reveal the process ID associated with the connection
  - `-n` — use a numerical form for address & port numbers

## File & Disk Management
- `dir` — view child directory | `dir /a` — show hidden files | `dir /s` — display files in current dir + all subdirectories
- `tree` — visually represent child directories/subdirectories
- `mkdir <name>` — create directory | `rmdir <name>` — delete directory
- `move` — move a file from one directory to another
- `del` / `erase` — remove a file
- `type` — view a file's contents
- `copy` — copy a directory or file

## Task & Process Management
- `tasklist` — view running processes | `tasklist /?` — help page
  - `tasklist /FI "imagename eq ssh.exe"` — filter processes by name
- `taskkill /PID <target-pid>` — kill a process by its specific PID

## still continue
CMD proficiency is essential for VAPT work on Windows targets — network troubleshooting 
commands (netstat, tracert) and process management are directly useful during post-exploitation 
enumeration on a compromised Windows host.
