# Windows Fundamentals

## Overview
Core Windows concepts covering the NTFS file system, permissions, Alternate Data Streams, 
and Command Prompt basics.

## File System — NTFS
Windows uses **NTFS (New Technology File System)**, succeeding older systems like FAT16/FAT32 
and HPFS. NTFS is a "journaling" file system — in case of failure, it can automatically repair 
files/folders using information stored in a log file.

**NTFS improvements over older file systems:**
- Supports files larger than 4GB
- Set specific permissions on folders & files
- Folder and file compression
- Encryption

## File Permissions
- Full Control
- Modify
- Read & Execute
- List Folder Contents
- Read
- Write

## Alternate Data Streams (ADS)
A file attribute specific to Windows NTFS. Every file has at least one data stream (`$DATA`), 
and ADS allows a file to contain more than one stream of data. Windows Explorer doesn't 
natively display ADS — third-party executables (or PowerShell) can be used to view it.

**Security note**: Malware writers have used ADS to hide data. `System32` holds important system files.

## Registry & Regedit
The Registry contains information Windows uses continually during operation:
- Profile settings for each user
- Applications installed and file types each can create
- Property sheet settings for folders/application icons
- Hardware present on the system, and ports being used
- `regedit` — shortcut to access the Registry

## BitLocker
Microsoft's **BitLocker Drive Encryption** is a data protection feature integrated with the 
OS that addresses the threat of data theft/exposure from lost or stolen devices. Provides 
the most protection when used with a **TPM (Trusted Platform Module)** version 1.2+ — a 
hardware component in many newer computers that helps ensure the device hasn't been tampered with.

## Windows Command Prompt (CMD) Basics
- `ipconfig /?` — help
- `netstat` — displays protocol statistics and current TCP/IP network connections
- `netstat /?` — help
- `net` — manage network resources
- `net help` — command help
- `net help use` — usage details


Understanding NTFS permissions, ADS, and the registry matters directly for VAPT work — 
ADS abuse and registry manipulation are common persistence/evasion techniques used by 
attackers on Windows systems, and are worth recognizing during assessments.
