---
title: juggling git logins
---

I have many git accounts over many services. I have 6 so far:

* work bitbucket.org
* work github.com
* personal-1 bitbucket.org
* personal-1 github.com
* personal-1 gitlab.com
* personal-2 github.com

Each of these accounts has an SSH key pair and I need to be able to clone from these easily.

[`ssh_config(5)`](http://man7.org/linux/man-pages/man5/ssh_config.5.html) to the rescue!

To add a new user-host pair with username `user` and host `example.com`:

1. Created a key-pair using `ssh-keygen` and saved it as `~/.ssh/user.example.com` and 
   `~/.ssh/user.example.com.pub`.

2. Upload `user.example.com.pub` to `example.com` via web interface.

3. Added the following entry in my `~/.ssh/config`:

        Match host example.com exec "test %r = user"    # 1
            User git                                    # 2
            IdentityFile ~/.ssh/user.example.com        # 3

    What this does is:

    1. If host is `example.com` and remote username (`%r`) is `user`
    2. Use remote username `git`
    3. Use private key specific to that user-host pair

4. Use the following command to clone repo named `example-repo`:

        git clone user@example.com:user/example-repo.git

    *Note: `user@` instead of the usual `git@`*

Job done.
