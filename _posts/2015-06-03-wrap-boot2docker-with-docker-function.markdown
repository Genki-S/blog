---
layout: post
title: "Wrap boot2docker with this docker function for stress-free docker life on OS X"
categories: docker
---

## Problem

[Docker](https://www.docker.com/) is awesome. But one of the not-so-awesome things is that we need [boot2docker](http://boot2docker.io/) to use it on OS X.

You might be familiar with this error message when you run docker without executing `$(boot2docker shellinit)`:

```
FATA[0000] Get http:///var/run/docker.sock/v1.17/images/json: dial unix /var/run/docker.sock: no such file or directory. Are you trying to connect to a TLS-enabled daemon without TLS?
```

Or this message when you run docker after `$(boot2docker shellinit)`, but boot2docker itself is not started:

```
FATA[0032] An error occurred trying to connect: Get https://192.168.59.103:2376/v1.17/images/json: dial tcp 192.168.59.103:2376: i/o timeout
```

I don't know about you, but I don't want to deal with boot2docker (which is just a VM to run docker on) when I want to play around with docker. So, hoping someday docker will run natively on OS X, I wrote a simple docker function which wraps boot2docker and does the right thing.

## Solution

Put this `docker` function definition to your `~/.zshrc` or `~/.bashrc` (though not tested with bash):

<code data-gist-id='37aff8bff273e8f0e80c'></code>

It does 2 things before running actual docker command:

1. start boot2docker VM when it's not started
2. export docker environment variables when it's not set

So basically, you just have to run `$ docker COMMAND` whenever you want and the function will take care of all the boot2docker stuffs.
Happy docker life :)
