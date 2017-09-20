# Privileged Access Suite for Unix Requirements Summary
The is a summary of the requirements of a typical PASU lab environment, but can easily be applied to production when the time is right.

**Mike Carroll, cissp**
**Chief Solutions Architect, Safer Strategy, LLC**
mike@saferstrategy.com
469-667-9016

Privileged Access Suite is a bundle of software that includes the following:

- Authentication Services (VAS)
 - Bridge AD users and management to Unix
 - Authentication
 - Group Policy
- Privilege Manager for sudo (PMsudo)
 - Centralized management of sudoers policy
 - Centralized Logging
 - Automatic encryption
 - Keystroke and Session Recording
- Management Console for Unix (MCU)
 - Java based Unix administration tool
 - Installs and Configures agents
 - Real-time reporting of Unix access and privileges

## Product Download Locations
To download the latest product versions, you will first need to register for an account with One Identity Support. If you have trouble registering, your One Identity salesperson can help.

http://support.oneidentity.com

Once registered, the following are direct links to the download pages for the various components of the PASU suite.

[MCU download](https://support.oneidentity.com/download-install-detail/6077581)
[QAS download](https://support.oneidentity.com/download-install-detail/6081307)
[QPM4sudo 6.0.0.61 Hotfix](https://support.oneidentity.com/download-install-detail/6077118)
[PMsudo 6.0.0.50](https://support.oneidentity.com/download-install-detail/6061756)


## VAS, PMsudo and MCU Lab Requirements Summary
This document describes the lab requirements to test PASU including VAS, and PMsudo.

* AD Domain Requirements
  * Enterprise Admin level access
    * Required Once to create the configuration container in AD during QAS install.
  * Domain Admin level access
    * Join Computers, Create and Modify users and groups, Edit Group Policy
* Windows "Tools Server"
  * VAS Control Center
  * ADUC, Active Directory Users & Computers
    * Including VAS snap-in
  * GPMC, Group Policy Management Console
    * Including VAS Snap-in
  * PowerShell
  * JRE 1.6.X
  * .Net Framework 4.0 or higher
  * Local Administrator Access
* Linux "MCU Host"
  * sudo 1.8.1 or above
  * root level access
  * VAS client
  * PMsudo Plugin(s)
* Linux Privilege Manager Policy Server(s)
  * sudo 1.8.1 or above
  * root level access
  * VAS client
  * PMsudo Policy Server (Primary|Secondary)
  * PMsudo Plugin(s)
* Unix / Linux Client(s)
  * sudo 1.8.1 or above
  * root level access
  * VAS client
  * PMsudo Plugin(s)

## POC Requirements
### Active Directory
Although any version of Active Directory is supported, it’s suggested to use version 2003 R2 or higher.

### Active Directory DNS or Equivalent
Unix systems joining Active Directory will need to resolve Active Directory DNS SRV records to properly support “sites” failover.

### Permissions
Permissions can be much more granular for production, but for POC we recommend the following to insure things go smoothly.
* AD Enterprise Administrator equivalent account (one-time install of display specifiers).
* AD Administrator equivalent account (one-time install of QAS central configuration).
* AD Administrator equivalent account (for managing users, groups, creating and editing Group Policy).
* Local Windows Administrator equivalent (Management console and snap-ins install).
* Unix root (Client and sudo plugin install).

### Windows "Tools Server"
* The Windows host should have Active Directory Users and Computers and Group Policy Management installed.
* P4 3.0 GHz or better
* 2 GB RAM or better  (8GB+ recommended)
* Windows 7 or better (probably should be Windows Server)
* Winzip or 7zip to open .tar.gz compressed files on Windows
* JRE 1.6.X (To Connect to the MCU with all features)

### Linux "MCU Host"
* Preferably RHEL or CentOS 6, 7
* 2 GB RAM
* sudo 1.8.1+
* VAS client
* 64-bit Java 1.6 JRE (JRE 1.7 is NOT Supported)
* Ensure that each host on your network knows the names and IP addresses of all other hosts preferably from DNS.
* Ensure hostname is not configured to the loopback IP address 127.0.0.1 in the /etc/hosts file.
* SSH (ssh-keyscan binary) for hosts running the Privilege Manager for Sudo client

### Linux Privilege Manager Policy Server(s)
* Any Supported Unix/Linux Platform
* 2 GB RAM
* 250 GB Disk for IO Logging
* Ensure that each host on your network knows the names and IP addresses of all other hosts preferably from DNS.
* Ensure hostname is not configured to the loopback IP address 127.0.0.1 in the /etc/hosts file.
* SSH (ssh-keyscan binary) for hosts running the Privilege Manager for Sudo client
* Ensure sudo version 1.8.1 or greater is installed for Privilege Manager for Sudo testing.

### Unix / Linux Client(s)
* Any supported Unix/Linux platform
* Ensure that each host on your network knows the names and IP addresses of all other hosts preferably from DNS.
* Ensure hostname is not configured to the loopback IP address 127.0.0.1 in the /etc/hosts file.
* SSH (ssh-keyscan binary) for hosts running the Privilege Manager for Sudo client
* Ensure sudo version 1.8.1 or greater is installed for Privilege Manager for Sudo testing.

### Unix Patch Requirements
| Platform | Patch Level |
| :-------- | :----------- |
| Solaris 8 SPARC |  108993-55 or greater |
| Solaris 8 X86 |  108994-01 or greater |
| Solaris 9 SPARC  |  112874-37 or greater |
|   | 112960-14 or greater  |
|   |  113319-22 or greater |
| Solaris 9 X86   | 114432-37 or greater  |
|Solaris 10 x86| 127128-11 or greater |
|AIX 5.3 |OS level 5300-05 or greater|
|HPUX 11.11|GOLDQPK11i - GOLDBASE11i|
| |GOLDAPPS11i quality packs|
| |BUNDLE11i - Patch bundle|
| |linker tools cumulative patch (PHSS_30970 or greater)|
|HPUX 11.23 |MAINTPACK E0306 or greater|

### TCP/IP configuration
It is essential that you have TCP/IP correctly configured before installing the Dell components. If you cannot use programs such as ssh and ping to communicate between your computers, then TCP/IP is not working properly; consult your system administrator to find out why and make appropriate changes.
