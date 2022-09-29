


FTP client for listing, copying, moving, and deleting files and directories on remote FTP servers.

Usage:

```
$ ./3700ftp operation params [params ...]
```

where the operation is one of: 

```
ls <URL>                 Print out the directory listing from the FTP server at the given URL
mkdir <URL>              Create a new directory on the FTP server at the given URL
rm <URL>                 Delete the file on the FTP server at the given URL
rmdir <URL>              Delete the directory on the FTP server at the given URL
cp <ARG1> <ARG2>         Copy the file given by ARG1 to the file given by
                          ARG2. If ARG1 is a local file, then ARG2 must be a URL, and vice-versa.
mv <ARG1> <ARG2>         Move the file given by ARG1 to the file given by
                          ARG2. If ARG1 is a local file, then ARG2 must be a URL, and vice-versa.
```

High level approach:
For this project, I followed the order of items in the "Suggested Implementation Approach" of the 
project spec (command line parsing, then connection establishment, then mkdir and rmdir, then understanding pasv and implementing the commands which require a data channel). I was able to reuse some logic for sending and receiving bytes from the previous assignment, which was helpful.

A challenge:
I had a bit of a hard time understanding what occurs on the data channel vs. the control channel. Once I understood that
the data channel is only for data, and all command sending occurs on the control channel, I could figure out what to send where and the order of how to send.

Overview of testing:
I used the command line to test throughout (testing params, testing different operations, testing changes to the elements
at the remote server). It was very helpful to have "ls" implemented, because then after a given operation, I could verify
the remote changes. One test-- uploading a binary-- was working on my command line but not passing remotely, so in this case I had to test by submitting to gradescope.

