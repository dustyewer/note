# 以管理员身份打开 PowerShell 并运行：
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
下载 Linux 内核更新包
运行上一步中下载的更新包。
wsl --set-default-version 2





# 首先更新软件源，保证其为最新。
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install mysql-server


sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
bind-address = 127.0.0.1 并注释掉

service mysql restart

    GRANT ALL PRIVILEGES ON *.* TO '用户名'@'%'IDENTIFIED BY '密码' WITH GRANT OPTION;
例如：GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'IDENTIFIED BY '12345678' WITH GRANT OPTION;
flush privileges;