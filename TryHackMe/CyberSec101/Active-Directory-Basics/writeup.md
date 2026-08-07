# Active Directory Basics

## Overview
Microsoft's Active Directory (AD) is the backbone of the corporate world — it simplifies 
management of devices and users within a corporate environment.

## Why Active Directory Matters
- **Centralized identity management**: All users across the network can be configured from AD with minimal effort
- **Managing security policies**: Security policies can be configured directly from AD and applied to users/computers across the network as needed

## Core Concepts
The core of any Windows domain is **Active Directory Domain Services**, which acts as a 
catalogue holding information on every "object" on the network — users, groups, machines, 
printers, shares, and more.

**Machines**: For every computer that joins the AD domain, a machine object is created. 
Machines are "security principals" with an assigned account, just like a regular user. 
Machines are local admins on their assigned computer. Machine account passwords are 
automatically rotated and generally composed of 120 random characters.
- Example naming: `DC01` = machine called that = `DC01$`

## Security Groups
- **Domain Admins**: Admin privileges over the entire domain — can admin any computer, including DCs, by default
- **Server Operators**: Can admin Domain Controllers, but cannot change admin group memberships
- **Backup Operators**: Cleared to access any file (ignoring permissions) — used to perform backups
- **Account Operators**: Can create or modify other accounts in the domain
- **Domain Users**: Includes all existing user accounts in the domain
- **Domain Computers**: Includes all existing computers in the domain
- **Domain Controllers**: Includes all existing DCs in the domain
- **Enterprise Admins**: Grants a user admin privileges over ALL of an enterprise's domains (relevant for Trees/Forests)

## Delegation
Delegation allows granting specific users control over specific OUs (Organizational Units) — 
used to configure new policies for other users/OUs without giving full domain admin rights.

## AD Devices
Three main device types:
1. Workstation
2. Server
3. **Domain Controller** — manages the AD Domain

Windows manages policies through **Group Policy Objects (GPOs)** — a collection of settings 
that can be applied to OUs.

**GPO Distribution**: GPOs are distributed via a network share called **SYSVOL**, stored on 
the DC. All users in the domain should have access to sync their GPOs periodically.

## Authentication Methods
Two protocols used for network authentication in Windows domains:
- **Kerberos**: Default protocol for any recent Windows domain
- **NTLM**: Legacy protocol kept for compatibility purposes

### Kerberos Authentication Process
1. The user sends their username + a timestamp encrypted with a key derived from their password to the **KDC (Key Distribution Center)**, usually installed on the DC
2. The KDC creates and sends back a **TGT (Ticket Granting Ticket)**, allowing the user to request additional tickets without re-sending credentials each time
3. When the user wants to access a service, they use the TGT to request a **TGS (Ticket Granting Service)** ticket from the KDC
4. The KDC sends back a TGS + service session key, which the user uses to authenticate to the target service

### NTLM Authentication (Challenge-Response)
1. Client sends an authentication request to the server
2. Server generates a random number and sends it as a challenge
3. Client combines their NTLM password hash with the challenge to generate a response, sends it back
4. Server forwards the challenge + response to the Domain Controller for verification
5. DC recalculates the response and compares it to the original — match = authenticated, mismatch = access denied
6. Server forwards the result back to the client

## Trees, Forests & Domains
- **Tree**: When a company expands (e.g. to a new country with different regulations), AD supports integrating multiple domains sharing the same namespace into a tree — e.g. `thm.local` splitting into `uk.thm.local` and `us.thm.local`. This gives better control over who can access what — a UK admin can't manage US users, and vice versa
- **Forest**: When companies merge (each with their own tree, different namespace), the union of these trees is known as a Forest

## Key Takeaway
Active Directory is one of the highest-value targets in real-world VAPT and red team 
engagements — misconfigured permissions, weak Kerberos implementations, and legacy NTLM 
usage are common attack vectors for privilege escalation and lateral movement in corporate networks.
