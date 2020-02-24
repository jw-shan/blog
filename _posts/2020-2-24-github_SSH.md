---
layout: post
title:  "Connecting to GitHub with SSH"
date:   2020-02-24 00:20 
---
We want to use the jupyter notebook in the remote server.

## 1. Generate a SSH key
```bash
$ ssh-keygen -t rsa -b 4096 -C "jwshan423@gmail.com"
```

Your should type a passphrase at the prompt `> Enter passphrase (empty for no passphrase): `

## 2.Add the SSH key to the ssh-agent
```bash
$ eval "$(ssh-agent -s)"
> Agent pid 39
$ ssh-add ~/.ssh/id_rsa
```

Then refer to this [help page](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) and complete the following steps.

1. `cat ~/.ssh/id_ras.pub` and copy the content to your clipboard.

2. Enter the  homepage of your [github](https://github.com/), click the profile photo, then click **Setting**.

3. In the user settings sidebar, click **SSH and GPG keys**.
4. Click **New SSH key** or **Add SSH key**.
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".
6. Paste your key into the "Key" field.
7. Click **Add SSH key**.
8. If prompted, confirm your GitHub password.

## 3. Test the connection to github
```bash
$ ssh -T git@github.com
# Attempts to ssh to GitHub
```

If you receive an error message, see [this](https://help.github.com/en/github/authenticating-to-github/error-permission-denied-publickey).

## 4. Auto-lauching `ssh-agent`
Paste the following lines into `~/.bashrc`
```bash
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

and `source ~/.bashrc`.

## 5. How to use
Then you can clone with SSH, for example `git@github.com:jw-shan/blog.git`.

