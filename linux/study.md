1.新增用户 useradd john
2.修改密码 passwd 或者 passwd john(root用户才能指定用户)
3.修改home目录 usermod -d /home/john -m john
4.冻结账号 usermod -L john
5.解冻账号 usermod -U john
6.删除用户 userdel john
7.添加用户组 groupadd group1
8.删除用户组 groupdel group1
9.查看用户 cat /etc/passwd  cat /etc/shadow
10.查看用户组 cat /etc/group
11.查看当前系统有哪些用户 users groups
12.rwx r=4读权限 w=2写权限 x=1执行权限 
13.file /root 查看文件类型
14.sticky 