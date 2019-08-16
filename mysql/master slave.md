## mysql5.7 主从复制简单配置

1. master配置
    ```
    [mysqld]
    port=3306
    datadir=/var/lib/mysql
    socket=/var/lib/mysql/mysql.sock
    log-error=/var/log/mysqld.log
    log_bin=mysql-bin
    server-id=1
    innodb_flush_log_at_trx_commit=1
    sync_binlog=1
    binlog-do-db=test
    binlog-ignore-db=mysql
    ```
2. slave配置
    ```
    [mysqld@replica01]
    port=3307
    datadir=/var/lib/mysql-replica01
    socket=/var/lib/mysql-replica01/mysql.sock
    log-error=/var/log/mysqld-replica01.log
    port=3307
    log-error=/var/log/mysqld-replica01.log
    server-id=2
    replicate-do-db=test
    replicate-ignore-db=mysql
    ```
3. master创建用户并授权
    ```
    mysql> CREATE USER 'repl01'@'%' IDENTIFIED BY '!QAZxsw2';
    mysql> GRANT REPLICATION SLAVE ON *.* TO 'repl01'@'%';
    ```
4. 查看master状态
    ```
    mysql> SHOW MASTER STATUS;

    +------------------+----------+--------------+------------------+
    | File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
    +------------------+----------+--------------+------------------+
    | mysql-bin.000003 | 73       | test         | mysql            |
    +------------------+----------+--------------+------------------+
    ```

5. 登录从库,并连接主库
   ```
   mysql -S /var/lib/mysql-replica01/mysql.sock -p
   mysql> change master to master_host='127.0.0.1',master_port=3306,master_user='repl01',master_password='!QAZxsw2',master_log_file='mysql-bin.000003',master_log_pos=73;
   ```

6. 查看连接状态,并启动slave
   ```
   mysql> show slave status\G;
   mysql> start slave
   ```
7. 测试,测试之前把主库的数据库结构在从库同步一下
