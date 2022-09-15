```shell
# write all the dirty cache to disk
sync

# clean all the caches, page + dentry + inode
echo 3 > /proc/sys/vm/drop\_caches

# cut back one word
ctrl + w
# get cut text back
ctrl + y
# search the history
ctrl + r

# execute cmd on each file belongs to the find result
find . -name "*.rs" -exec grep -rwn fmt {} \;
find . -type f -exec sed -i 's/privelages/privileges/g' {} \;
# concat the find result to one line and execute the cmd once
find . -name "*.rs" -exec grep -rwn fmt {} + 

# set bash editor
set -o vi

# file attribute
lsattr, chattr
chattr +a /var/log/message
a    file can only be open in append mode for writing
i    it cann't be deleted or renamed, no link can be created
     to this file, and no data can be written to the file
s    when file is deleted, its block are zeroed and sync with disk
S    when file is modified, the changes are wirtten synchronously on disk


# SUID, use run the binary file gain the privileges of owner
chmod u+s binary-file
# SGID, on binary file will give use the privelages of the group
chmod g+s binary-file
# SBIT, files in directory can only be deleted by root or file owner
chmod o+t tmp

#list block deivce info
lsblk

# set kernel option
sysctl -w net.ipv4.ip_forward=1

service svc_name status/start/stop/restart
systemctl status/start/stop/restart svc_name

# xargs
# find all the png file and compress them
# -print0 make sure each file end with null char
# -0 use null char as sep(default is blank or newline)
find Pictures/tecmint -name "*.png" -type f -print0 | xargs -0 tar -cvfz images.tar.gz

# copy a.txt to two folders
# -n 1, only pass one argument to cmd
echo ./Templates ./Documents | xargs -n 1 cp -v ./Downloads/a.txt 

# move files end with bak to ~/old.files
# the argument will be postioned to the end by default
# -I set the place holder
find . -name "*.bak" -print0 | xargs -0 -I {} mv {} ~/old.files
```
go run -gcflags '-m -l'

# fzf
$ git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
$ ~/.fzf/install

# install fzf in vim
cd ~/.vim/bundle/
git clone https://github.com/junegunn/fzf.vim
git clone https://github.com/junegunn/fzf

# awk
awk '{action}' filename
awk 'pattern' filename                  // awk -F: '$1 ~ /e$/' yang.txt
awk 'pattern {action}' filename         // awk -F: '$1 ~ /e$/ {print $2}' yang.txt
awk script
```awk
#!/usr/bin/awk -f

BEING {
     # set the input separators
     FS=':'
     # define a word cound
     words=0
}
{
     # add a record, NF stands for field count and $NF stands for last field
     words=words+NF
     print NF
}
END {
     # print the result
     print words " words.\n"
}
```

# management file permission
chown -R ben /var/www/my-websit.com/
chgrp -R www-data /var/www/my-websit.com/
chmod -R 750 /var/www/my-websit.com/
//new file will inherit the group ownership of parent folder
chmod g+s /var/www/my-websit.com/

# generate ssh key
```shell
ssh-keygen -t rsa -b 4096
ssh-copy-id -i public-key-file user@host
```

# split file
```shell
split -b 180m golang-arm.tar.gz golang-arm.tar.gz.
cat golang-arm.tar.gz.* > golang-arm.tar.gz
```

# enable core dump
```shell
ulimit -S -c unlimited
sudo sysctl -w kernel.core_pattern=/tmp/core.%u.%p.%t
```

# User management
```shell
sudo passwd -l[-u] user-name  #(un)block user
sudo getent group  #display groups
sudo getent group  groupname #display one group
sudo gpasswd -a user groupname #add user to group
```

# Shell runtime parameter
## `set -x` 
Is used to output the line of command executed before the result, with + at the beginning of the line to indicate that it is a command instead of a command output, and the arguments of each command will be expanded

## `set -u`
when it encounters a non-existent variable it will report an error and stop execution

## `set -e`
making the script terminate whenever an error occurs.

## `trap`
catch the corresponding signal and restore it accordingly.
`trap "rm -f $lockfile; exit" INT TERM EXIT`
