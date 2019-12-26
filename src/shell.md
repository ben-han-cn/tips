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
