## CIFS-over-SSH 
Sometimes there is a need to mount a remote Windows/Samba directory, but all you have is
an SSH connection to a remote server close to the fileserver. 
This tutorial tries to explain how you can set up these Windows shares on Windows 10.

The concept behind mounting shares using SSH is this:

- The SSH protocol has a feature known as port-forwarding. This feature allows you to forward all 
  traffic from a TCP/IP network port on your local computer to another port on another computer at
  the "other" side of the SSH connection.
- The Windows File Sharing protocol, a.k.a.CIFS, uses TCP/IP port 445 to communicate between the
  client and the server. Older versions of Windows also allowed the use of TCP/IP port 139 to 
  communicate between the client and the server.
- Unfortunately, it turns out to be quite hard to redirect local port 445 to another computer, as
  the OS also wants this port all for itself. However, with some special portproxy rules it is
  still possible to grab port 445 before the OS does.
- Thus, by configuring SSH in just the right way, we can redirect all traffic from the TCP/IP port 445
  on your local computer to the remote Windows file server.
- The result is that this will magically allow you to create a network share to view the remote directory
  on your home computer.

This tutorial has been tested on Windows 2000, XP, Vista, 7, 8 and 10.

**Note** This tutorial does not work on Windows Server 2016 or 2019. If someone finds a way to make
  it work for Windows Server editions please let me know!

### Types of access
For Windows 10+, the tutorial is now split into multiple parts, depending on the type of remote server
access that is required:

- [Access to a single remote host, no Kerberos](https://github.com/jjkeijser/cifs-over-ssh/blob/main/Win10/Singlehost.md)
- [Access to multiple remote hosts, no Kerberos](https://github.com/jjkeijser/cifs-over-ssh/blob/main/Win10/Multihost.md)
- [Access to multiple remote hosts, including DFS and Kerberos](https://github.com/jjkeijser/cifs-over-ssh/blob/main    /Win10/MultihostKerberos.md)

### Legacy tutorials
The following legacy tutorial pages are also available as single HTML pages:

- [Windows 10 with the built-in OpenSSH client](Win10/Win10Loopback.html)
- [Windows 10 with the PuTTY SSH client](Win10/Win10PuTTYLoopback.html)
- [Windows 8](Win8/)
- [Windows 7](Win7/)
- [Windows Vista](WinVista/)
- [Windows XP/2000](WinXP/)

