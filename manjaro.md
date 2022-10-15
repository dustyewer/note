
sudo pacman-mirrors -i -c China -m rank         //选择合适的源，安装的时候不报错即可（有些源安装的时候会出错）
sudo pacman -Syy                                //刷新系统
sudo pacman -S yay                              //安装yay

yay -S core/binutils                            //安装其他包安装时需要的工具  无法找到目标文件分割所需的 strip 二进制文件。
yay -S fakeroot                                 //安装其他包安装时需要的工具


sudo不要密码
1. 修改/etc/sudoers文件，清徐%sudo ALL=(ALL) ALL前的注释#
2. [重要] 不要在sudoers文件中直接添加用户设置，应该在/etc/sudoers.d/10-installer的%wheel ALL=(ALL) ALL行后添加如下配置

xxx ALL=(ALL) NOPASSWD: ALL
%xxx ALL=(ALL) NOPASSWD: ALL

安装输入法
yay -S fcitx-im    #默认全部安装
yay -S fcitx-configtool
yay -S fcitx-sogoupinyin

vi ~/.xprofile

export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"

source ~/.xprofile

百度云盘
yay -S baidunetdisk-bin

虚拟机
yay -S virtualbox

vscode
yay -S visual-studio-code-bin

微信-deepin版
yay -S deepin-wine-wechat

QQ
yay -S deepin.com.qq.im

yay -S deepin.com.qq.office

yay -S netease-cloud-music

yay -S vlc

yay -S filezilla

yay -S foxitreader

yay -S teamviewer

yay -S wps-office wps-office-mui-zh-cn

yay -S ttf-wps-fonts

yay -S git

yay -S nutstore

yay -S wiznote




配置使wps可以输入中文

    sudo vim /usr/bin/wps

export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"

yay -S youdao-dict

yay -S typora

yay -S deepin-screenshot

yay  -S deepin-terminal

安装MariaDb代替mysql(MyriaDb与Mysql相互兼容)
yay -S mariadb mariadb-clients

    安装成功后，根据提示，输入下列指令初始化MariaDb数据库

    sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

    一番信息自动输出完成后，执行以下代码

    sudo systemctl start mysqld # 启动MariaDb
    修改配置文件中的配置，可以直接登录，[mysqld]段 新加一行skip-grant-tables
    sudo nano /etc/my.cnf.d/server.cnf

    mysql -uroot 登录后执行下面两个sql语句
    flush privileges;
    alter user 'root'@'localhost' IDENTIFIED BY '12345678';

    成功后把配置文件改回来，重启mysql

    sudo systemctl enable mysqld # 设置mariaDb开机自启
    mysql -uroot -p # 输入设置的的密码，登录数据库


数据库 mongodb
yay -S aur/mongodb

数据库 redis
yay -S redis

yay -S docker


# 打印机
sudo pacman -S manjaro-printer
sudo systemctl enable --now cups.service
sudo systemctl enable --now cups.socket
sudo systemctl enable --now cups.path



pacman -S mysql
# 初始化MySQL，记住输出的root密码
mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql

# 设置开机启动MySQL服务
systemctl enable mysqld.service
systemctl daemon-reload
systemctl start mysqld.service
# 使用MySQL前必须修改root密码，MySQL 8.0.15不能使用set password修改密码
mysql -u root -p
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';


# 由于下载的压缩包格式为.tar.xz，因此必须先解压。解压的结果是.tar文件。
xz -d mysql-8.0.15-linux-glibc2.12-x86_64.tar.xz
tar -xv -f mysql-8.0.15-linux-glibc2.12-x86_64.tar


将解压内容放入合适的任意位置。

我将MySQL放入/usr/local/share。
# 不需要创建HOME目录
useradd -r mysql -M
# 将MySQL安装目录的拥有者以及用户组修改为mysql
chown -R mysql:mysql /usr/local/share/mysql

# samba
yay -S samba
yay -S manjaro-settings-samba 
systemctl start smb