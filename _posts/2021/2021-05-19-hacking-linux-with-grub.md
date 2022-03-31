---
layout: post
title:  "Hacking linux through GRUB issue"
date:   2021-05-19 12:00:00 +0200
---

## Hack password on linux machine with GRUB

It happens, you need to hack or recover password on linux machine, when you even don’t know real password. You know nothing about real user, you have no clue what the password could be and other facts, but it’s not a problem!

If your situation matches with next conditions, you’re able to hack any linux machine:

    1. You have physical access to linux machine
    2. GRUB bootloader on linux machine have no password

Does it matches? Great!

Let’s start. The essence of the way is in changing OS preload script for letting us enter in root-authorized shell. To change script, you need to enter GRUB menu (in my case you should press “shift” key) when OS is loading:

GRUB menu

To enter preload script edit menu, press “e” key.

![grub menu](images/2021/os-loading.png)

Go to the “linux” line. Delete everything, that goes after “rw”. Move “ro” to “rw” and write “init=/bin/bash” after. (or path to another shell, OS uses).

We have changed hard disk access mode from “read only” to “read-write”, otherwise, we won’t be able to rewrite password.

Preload script before:

![preload script before](images/2021/script-before.png)

Preload script after:

![preload script after](images/2021/script-after.png)

Fine. Press F10 key to enter OS with edited preload script. Wait for load.

Change root password with passwd command

![change root password with passwd command](images/2021/change-check.png)

We appear in root shell. Enter “passwd” command, to change current (root) account password.

Congratulations! We have changed the root password without even knowing it!

Thanks for reading!

I will be grateful if you support me on Patreon or Boosty

Follow me on telegram: https://t.me/secretsupper (most part of content could be found exactly in telegram).

Follow me on twitter: https://twitter.com/MaksymovArtem