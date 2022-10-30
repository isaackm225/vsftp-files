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


adding ssl is actually a hasle better keep ftpuser out of ssh and drop ssl but just in case<a href=https://www.funoracleapps.com/2020/04/how-to-use-ftps-or-ssl-with-ftp-on-linux.html> here is a useful article
