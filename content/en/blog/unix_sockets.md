---
title: "Sockets"
date: 2022-03-04T10:44:43-06:00
draft: false
tags:
- C
- Unix
---

## Summary

If you've ever used `netstat`, or gone to a website on OSX or Linux (or Windows for that matter) without a background in C (or perhaps systems programming), you may have struggled to fully appreciate the content there in. Or maybe you are just curious to know how `sockets` work in *nix.

`sockets` are a form of `IPC`, or inter process communication, allowing processes to bidirectionally share information with other processes. See other kinds of IPC in [Beej's Guide to Unix IPC](https://beej.us/guide/bgipc/html/multi/index.html).

`sockets` are commonly referred to by their _Address Family_, seen in constants such as `AF_UNIX`, or `AF_LOCAL`, representing local sockets specifically. You might also want to know about _Protocol Family_, seen in constants such as `PF_UNIX` and `PF_LOCAL`.

Valid `socket` types that should be known are:

|type|description|
|-|-|
|`SOCK_STREAM`|A stream oriented packet used for TCP|
|`SOCK_DGRAM`|datagram oriented packet, no reordering, used for UDP|
|`SOCK_RAW`|Provides access to internal network protocols and interfaces. Only available to super-user|
|`SOCK_SEQPACKET`|A sequence-packet socket that is connection oriented, delivering messages in the order sent|

You can learn more about various types of valid `sockets` on the man page for the socket SystemCall:

[https://man7.org/linux/man-pages/man2/socket.2.html](https://man7.org/linux/man-pages/man2/socket.2.html)

Now that we've discussed what `sockets` are, and some of the well known constants that sockets use, let's look at the example in the man page.

### Unix Socket Example

The given snippet in the man page is a bit terse, but practical:

```c
       #include <sys/socket.h>
       #include <sys/un.h>

       unix_socket = socket(AF_UNIX, type, 0);
       error = socketpair(AF_UNIX, type, 0, int *sv);
```

In the example above, we import the definitions for socket and unix domain sockets, then construct a unix_socket, and assign error the exit code of calling `socketpair`.

It is helpful to consult the manual, let's take a look at the two syscall signatures from their respective man pages:

```c
int socket(int domain, int type, int protocol);
int socketpair(int domain, int type, int protocol, int sv[2]);
```

- [socket](https://man7.org/linux/man-pages/man2/socket.2.html)
- [socketpair](https://man7.org/linux/man-pages/man2/socketpair.2.html)

Using what we've learned about valid types, we can construct a simple program that creates a socket, and prints its file descriptors or any relevant error:

```c
#include <stdio.h>
#include <sys/socket.h>
#include <sys/un.h>

int
main()
{
    int unix_socket, error;
    // socket vector, sv, is a vector pointer to two file descriptors
    // representing new sockets for server and client bindings
    int *sv[2];

    unix_socket = socket(AF_UNIX, SOCK_DGRAM, 0);
    // socketpair below is constructed for the OSX variant. The linux variant has a different signature, instead use:
    // error = socketpair(AF_UNIX, 0, *sv)
    error = socketpair(AF_UNIX, SOCK_DGRAM, 0, *sv);

    if (error != 0)
    {
      printf("Encountered error: %d\n", error);
      return error;
    }

    printf("Socket descriptor: %d\n", unix_socket);
}
```

Compiling and running our example can be done by running:

```sh
clang -o socket ./socket.c; ./socket

Socket descriptor: 3
```

Ok, so we created a socket, and it returned a descriptor, `3`. What does that mean?

You are likely familiar with file descriptors 0, 1, 2 if you've ever redirected output. They are `stdin`, `stdout`, and `stderr`.

## References

1. [Beej's Guide to Unix IPC](https://beej.us/guide/bgipc/html/multi/index.html)
1. [unix-7 man page](https://man7.org/linux/man-pages/man7/unix.7.html)
1. [socket-2 man page](https://man7.org/linux/man-pages/man2/socket.2.html)
1. [unix domain socket wikipedia](https://en.wikipedia.org/wiki/Unix_domain_socket)
1. [What's the difference between Unix sockets and TCP/IP sockets](https://serverfault.com/questions/124517/what-is-the-difference-between-unix-sockets-and-tcp-ip-sockets)
1. [File Descriptors](https://en.wikipedia.org/wiki/File_descriptor#:~:text=On%20Linux%2C%20the%20set%20of,%2Ffd%2F2%20is%20stderr%20.)
