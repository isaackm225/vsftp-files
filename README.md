<h1 align="center">
  <br>
  <img src="simple-logo.png" alt="simple-logo" width="200">
  <br>
  Ftp config files
  <br>
</h1>

<h4 align="center"> A bunch of config files for vsftp </h4>

<p align="center">
  <a href="https://paypal.me/izy225?country">
    <img src="https://img.shields.io/badge/$-donate-ff69b4.svg?maxAge=2592000&amp;style=flat">
  </a>
</p>

## How to use it

```bash
# make sure your linux machine is updated
$ sudo apt update && sudo apt upgrade (Debian based system)
$ sudo pacman -Syu (Arch based system)

# Download vsftpd
$ sudo apt install vsftp
$ sudo pacman -S vsftp

# Explore the documentation and the config files
```

# Setting up an ftp server

These are the config file for my Very Secure File Transfer Protocol server. 

## What is ftp?
A File transfer protocole. It's all in the name. Computer use that protocole to send data over the internet

## What is vsftpd? 
ftp has a long history of vulnerability vsftpd is a linux tool built to be more solid and secure than the traditional ftp. it can be improved with chrooting(what i did) and/or ssl

Also a great video explaining <a href=https://youtu.be/r1nJT63BFQ0>what is ssl</a>

Dont forget to create a new user specially for ftp connections.

My config files assume the new user's name is ftpuser(=> he is the only user in the userlist)

Add any other user to that list, the ftp connection won't work if their username isn't. Also in the conf file I enabled the chroot jail for security=> ftp connection won't have access to the actual root of the ftp server.

Finally don't forget to restrict ftpuser, and any other user from ssh connections. the sshd conf file is located @ /etc/ssh/sshd_conf

Add either of the following lines:
AllowUsers <usernames>
AllowGroups <groups>
DenyUsers <usernames>
DenyGroups <groups>

Don't forget to transfet ownership of each file to the ftpuser
crontab line
chown -R /home/ftpuser/*


adding ssl is actually a hasle better keep ftpuser out of ssh and drop ssl but just in case<a href=https://www.funoracleapps.com/2020/04/how-to-use-ftps-or-ssl-with-ftp-on-linux.html> here</a> is a useful article
Along the way I figured out that adding ssl to the ftp make use of ssh => the ftpuser has to be on the sshd.conf to be able to connect. I don't want that (personal choice).
  
  
  TODO(maybe): add a bash script to automate the process.
  

## You may also like...

- [Leetcode-serving-alarm](https://github.com/Izy-stack/LT-serving-alarm) - The Dojo Alarm
- [80s-themed-surveillance-web-portal](https://github.com/Izy-stack/80s-themed-surveillance-portal) - A web portal to serve live footage from camera


---

> GitHub [@Izy-stack](https://github.com/Izy-stack) &nbsp;&middot;&nbsp;
> Twitter [@isaackm225](https://twitter.com/isaackm225)



 
