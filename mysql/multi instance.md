1. 编辑配置文件

    vim /etc/my.cnf

2. 添加如下配置

    [mysqld@replica01]
    datadir=/var/lib/mysql-replica01
    socket=/var/lib/mysql-replica01/mysql.sock
    port=3307
    log-error=/var/log/mysqld-replica01.log

    [mysqld@replica02]
    datadir=/var/lib/mysql-replica02
    socket=/var/lib/mysql-replica02/mysql.sock
    port=3308
    log-error=/var/log/mysqld-replica02.log

3. 启动服务

    systemctl start mysqld@replica01
    systemctl start mysqld@replica02

4. 登录

    mysql -S /var/lib/mysql-replica01/mysql.sock -p

5. 找到临时密码
   
   sudo grep 'temporary password' /var/log/mysqld-replica01.log

6. 修改密码

    ALTER USER 'root'@'localhost' IDENTIFIED BY '!QAZxsw2';