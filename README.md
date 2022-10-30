# Setting up an ftp server

These are the config file for my Very Secure File Transfer Protocol server. 

## What is ftp?
A File transfer protocole. It's all in the name. Computer use that protocole to send data over the internet

## What is vsftpd? 
ftp has a long history of vulnerability vsftpd is a linux tool built to be more solid and secure than the traditional ftp. it can be improved with chrooting(what i did) and/or ssl

Also a great video explaining <a href=https://youtu.be/r1nJT63BFQ0>what is ssl</a>

As usual I wrote the readme as I was completing the project so the ReadMe is more like a couple of reminder I scribbled down along the way not a proper ReadMe...



Dont forget to create a new user specially for ftp connections by.

My config files assume the new user's name is ftpuser(=> he is the only user in the userlist)

Add any other user to that list, the ftp connection won't work if their username isn't. Also in the conf file I enabled the chroot jail for security=> ftp connection won't have access to the actual root of the ftp server.

Finally don't forget to restrict ftpuser, and any other user from ssh connections. the sshd conf file is located @ /etc/ssh/sshd_conf

Add either of the following lines:
AllowUsers username1 2
AllowGroups Groups
DenyUsers 
DenyGroups

Don't forget to transfet ownership of each file to the ftpuser
crontab line
chown -R /home/ftpuser/*


adding ssl is actually a hasle better keep ftpuser out of ssh and drop ssl but just in case<a href=https://www.funoracleapps.com/2020/04/how-to-use-ftps-or-ssl-with-ftp-on-linux.html> here</a> is a useful article
Along the way I figured out that adding ssl to the ftp make use of ssh => the ftpuser has to be on the sshd.conf to be able to connect. I don't want that (personal choice). There may be a way around but since the ftp server is running on my home network and the ftpuser is in a chroot jail i don't have to worry.
  
  
  Next thing to do (maybe) add a bash script to automate the process.
 
  ## Peace.
