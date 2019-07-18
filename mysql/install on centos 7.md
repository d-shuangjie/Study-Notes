

1. 下载rpm包

    wget https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm

2. 安装软件包

    sudo rpm -Uvh mysql57-community-release-el7-9.noarch.rpm

3. 查看yum源

    yum repolist all | grep mysql

4. 修改yum源,enable要安装的版本

    vim /etc/yum.repos.d/mysql-community.repo

5. 查看是否修改成功

    yum repolist enabled | grep mysql

6. 安装mysql

    yum install mysql-server -y

7. 启动并查看运行状态
    systemctl start mysqld.service
    systemctl status mysqld.service

8. 查看临时密码
    sudo grep 'temporary password' /var/log/mysqld.log

9. 处理登录需要修改密码
    mysql -uroot -p
    ALTER USER 'root'@'localhost' IDENTIFIED BY '!QAZxsw2';

 mysqladmin -u root -p version
 SHOW VARIABLES LIKE 'datadir';
