# FTP Client in Python

A minimal FTP client implemented directly on top of Python's socket interface. It supports directory operations, file transfers, and passive-mode data channels without relying on external FTP libraries.

Usage:

```
$ ./ftp operation params [params ...]
```

## Overview

This client establishes an FTP control connection, authenticates with a username and password, issues FTP commands, and for data-transfer operations opens a separate passive-mode data channel.

Supported operations:

-   `ls <URL>`  
    List remote directory contents.

-   `mkdir <URL>`  
    Create a directory at the remote path.

-   `rmdir <URL>`  
    Remove a directory at the remote path.

-   `rm <URL>`  
    Remove a file at the remote path.

-   `cp <ARG1> <ARG2>`  
    Copy files between the local machine and an FTP server.  
    If `ARG1` is local and `ARG2` is an FTP URL, the file is uploaded.  
    If `ARG1` is an FTP URL and `ARG2` is local, the file is downloaded.

-   `mv <ARG1> <ARG2>`  
    Move local-to-remote or remote-to-local by performing a copy followed by a delete.
