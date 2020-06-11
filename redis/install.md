## 安装

1. wget http://download.redis.io/redis-stable.tar.gz
2. tar xzf redis-stable.tar.gz
3. cd redis-stable
4. make
5. make install
6. yum install tcl
7. make test

## 配置

1. 复制初始化脚本
   
   cp redis-stable/utils/redis_init_script /etc/redis_6380
2. 建立需要的文件夹

|    |  |
|----  | ----  |
| /etc/redis | 存放Redis的配置文件|
| /var/redis/端口号 | 存放Redis的持久化文件|


3. 修改配置文件 /etc/redis/端口号.conf

|     |   |   |
|  ----  | ----  | ---- |
| daemonize | yes | 使Redis以守护进程模式运行|
| pidfile   | /var/run/redis_端口号.pid | 设置Redis的PID 文件位置 |
| port | 端口号 | 设置Redis监听的端口号 |
| dir  | /var/redis/端口号 | 设置持久化文件存放位置

4. 启动
   
    /etc/init.d/redis_端口号 start

5. 随系统启动

   update-rc.d redis_端口号 defaults



