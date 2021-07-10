# MySQL安装

目标操作系统：Ubuntu20.04 LTS



#### 1、安装MySQL服务以及命令行客户端

```bash
sudo apt update
sudo apt install mysql-server mysql-client
```



#### 2、执行安全配置（可选）

安装完 mysql-server 会提示可以运行 mysql_secure_installation。运行mysql_secure_installation 会执行以下几个设置：

1.  为root用户设置密码
2.  删除匿名账号
3.  取消root用户远程登录
4.  删除test库和对test库的访问权限
5.  刷新授权表使修改生效

每一步都有选项，根据选项来选择是否使用以上配置

通过这几项的设置能够提高 mysql 数据库库的安全。建议生产环境中 mysq l安装这完成后一定要运行一次mysql_secure_installation

```bash
sudo mysql_secure_installation
```



#### 3、远程连接配置

如果需要使用数据库管理软件（例如 Navicat）远程管理数据库，需要给 root 用户创建远程连接的权限：

1.  修改配置文件 `mysqld.cnf`

    ```bash
    # 编辑 mysqld.cnf 将 bind-address=127.0.0.1 行注释掉
    sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
    ```

2.  重启MySQL服务

    ```bash
    sudo service mysql restart
    # 或
    sudo systemctl restart mysql.service
    ```

3.  连接MySQL并创建具有远程权限的root用户

    ```bash
    sudo mysql -u root -p
    
    mysql> use mysql;
    # 为了安全，请设置复杂密码
    mysql> CREATE USER 'root'@'%' IDENTIFIED BY 'c3#RxcpVSWSu';
    # 授权新的root用户对数据库所有权限
    mysql> grant all privileges on *.* to 'root'@'%';
    # 刷新权限
    mysql> FLUSH PRIVILEGES;
    ```

4.  如果远程连接时报错 plugin caching_sha2_password could not be loaded，执行：

    ```bash
    mysql> alter user 'root'@'%' identified with mysql_native_password by '123456';
    ```

    

