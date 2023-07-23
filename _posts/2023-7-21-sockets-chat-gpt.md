---
layout: post
title: An Exploration of Python Sockets Behavior
icon: python_sockets2.png
date: 2023-07-21
ready: false
show_date: true
---

<figure>
    <img class="mx-auto d-block blog-img" src="/assets/images/blog/python_sockets2.png" alt="python sockets">
    <figcaption class="text-center">High-Quality Resolution Cartoon Drawing of a Python with Sockets - Prompt for Image Generated by DreamStudio</figcaption>
</figure>

Let's delve into the intriguing world of Python sockets. Throughout my (short) career as a developer, debugging socket issues has always presented a unique challenge. Sometimes, the problem is as straightforward as connecting to the wrong port. Other times, it feels like your socket just releases packets into the void, leaving you puzzled about the lack of data on the receiving end. Whenever these bugs surface, I find myself employing a variety of debugging techniques, from simple `printf()` debugging to the amusing yet effective rubber duck debugging. However, despite all efforts, I've yet to discover a foolproof way to debug socket issues (yes, I should probably be using WireShark).

Last Friday, I found myself spending nearly two hours debugging some sockets code. Those two hours proved to be the final straws that broke the camel's back. And now, I officially have a bone to pick with the Python sockets API.

#### **The Final Straws**

Imagine opening two terminals and running the Python interpreter on both. The first terminal serves as a simple server for sending packets, while the second terminal receives packets from the server. Let's walk through the commands sequentially, following the `# Step X:` comments.

<div class="row">
    <div class="col">
        <code>Terminal 1:</code>
        <hr>
        <pre>
import socket

HOST = '127.0.0.1'
PORT = 5678 

# Step 1: Creating server socket
server = socket.socket(socket.AF_INET, 
                       socket.SOCK_STREAM)
server.bind((HOST, PORT))
server.listen(1)
server, _ = server.accept()


# Step 4: Close server 
server.close()

        </pre>
    </div>
    <div class="col">
        <code>Terminal 2:</code>
        <hr>
        <pre>
import socket

HOST = '127.0.0.1'
PORT = 5678

# Step 2: Creating client socket
client = socket.socket(socket.AF_INET, 
                       socket.SOCK_STREAM)
client.connect((HOST, PORT))
client.setblocking(False)

# Step 3: Receive data
packet = client.recv(1024) <---
## a) Error or empty byte array? ##

# Step 5: Receive data again
packet = client.recv(1024) <---
## b) Error or empty byte array ##
        </pre>
    </div>
</div>

Here's what we are doing. First, we open a server socket in `Terminal 1`. Then, we open a client socket in `Terminal 2`. The **non-blocking** client socket attempts to receive data from the server. Since the server socket has not sent any data, the `recv` function will not return empty data. **What is the expected behavior of the `recv` function in this scenario?** Will it throw an error, or will it return an empty byte array (e.g. `b''`)?

After attempting to receive a packet, we close the server socket with the `close()` function. Lastly, we try to receive a packet from the server once again. **Will the second `client.recv(1024)` throw an error, or will it return an empty byte array (e.g. `b''`)?**

#### **The Beef**

<figure>
    <img class="mx-auto d-block blog-img" src="/assets/images/blog/python_sockets_behavior.png" alt="the beef">
    <figcaption class="text-center">Demonstration of the Behavior</figcaption>
</figure>

According to the `recv` function [documentation](https://docs.python.org/3/library/socket.html#socket.socket.recv), I would have assumed `recv` returns an empty byte array on the first call. After all, there was nothing to receive! In fact, I think it would be a pretty intuitive and reasonable behavior for the `recv` function to return an empty byte array. However, instead, the function throws a `BlockingIOError`, all because the server didn't send any data. This... makes no sense. Shouldn't errors be reserved for unacceptable behaviors? How is the client even supposed to know the server didn't send any packets? Why would a client socket not be allowed to `recv` data?? I don't get it.

On the other hand, the second `recv` function will return... an empty byte array. So, wait a second. A client can `recv` from a socket that's already been closed, but it can't receive data from a server that hasn't sent any packets? Why would the `recv` function work on a closed socket at all!! Throw an error, goddamnit!

**/endrant**

In all honesty, I kinda get it. I brought this upon myself because I defined a non-blocking client socket. But if it were up to me, I'd make it so the first `recv` call would return an empty byte array, and the second call would throw an error. Just sayin'...