---
layout: post
title: "Todo list after install ubuntu"
date: "2019-01-02 16:18:59 +0900"
---


## Bashrc
* Update PS1
```sh
force_color_prompt=yes
color_prompt=yes
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

if [ "$color_prompt" = yes ]; then
  PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\] $(parse_git_branch)\[\033[00m\]\$ '
else
  PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
```

## ~/.ssh/config
* create config file
```sh
Host *
   ServerAliveInterval 120

Host git.cdnetworks.com
   User git
   IdentityFile ~/.ssh/id_rsa_git

Host gitlap.com
   User liush79@gmail.com
   IdentityFile ~/.ssh/gitlab

Host stack-spectrum-api-tester
   Hostname 10.192.239.64
   User ubuntu
   IdentityFile ~/.ssh/stack-ci.pem
   Port 22

Host stack-spectrum-api-server
   Hostname 10.192.239.83
   User ubuntu
   IdentityFile ~/.ssh/stack-ci.pem
   Port 22
   ServerAliveInterval 120
```
