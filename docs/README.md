# Setting up

## What to do

- Create a new Droplet
- Don't add SSH keys yet
- Go to 'Access' > Launch Console
- Login as root and change your password (check email for the password / reset it)

```bash
# After logging in, change root's password:
passwd

# install `openssh-server`
sudo apt-get install openssh-server

# edit /etc/ssh/sshd_config
vim /etc/ssh/sshd_config

# look for `PasswordAuthentication` and change it from `no` to `yes`
# <ESC> /PasswordAuthentication <Enter>
# $i
# `no` => `yes`
# <ESC> :wq <Enter>
sudo service ssh restart

exit

# Then, from your local machine:
ssh-copy-id -i ~/.ssh/YOUR_KEY_NAME_RSA user@host

# Enter your password / passphrase
# Try out sudo. If it works, go back to /etc/ssh/sshd_config
# change `PermitRootLogin` from `yes` to `no`

# when you're done:
sudo service sshd restart

# enable bash completion for yourself
vim ~/.bashrc
# add the following
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi

# then
exec bash
```

- `passwd`
- Create SSH keys on your local machine
- `ssh-copy-id -i ~/.ssh/YOUR_KEY_NAME_RSA user@host`
- `ssh root@host`
- `useradd -m -p PASSWORD USERNAME`
- `usermod -aG sudo USERNAME`
- `su -- USERNAME`
-
-

## Other useful shenanigans

- Deleting a user

```bash
userdel -rf USERNAME
```

- Installing essential build scripts:

```bash
sudo apt install build-essential
```

- [Installing Node](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04)
