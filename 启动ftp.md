which vsftpd
service vsftpd status
service vsftpd start
service vsftpd restart

netstat -an | grep 21

vi /etc/vsftpd.ftpusers中注释掉root
vi /etc/vsftpd.user_list中也注释掉root

vsftpd 500 OOPS: cannot change directory
登陆报错:
C:\>ftp 192.168.0.101
Connected to 192.168.0.101.
220 (vsFTPd 2.0.5)
User (192.168.0.101:(none)): frank
331 Please specify the password.
Password:
500 OOPS: cannot change directory:/home/frank
Login failed.
ftp> ls
500 OOPS: child died
Connection closed by remote host.

setsebool ftpd_disable_trans 1
service vsftpd restart

这是SELinux的设置命令,在不熟悉SELnux前，把SELinux关掉也可以的。

永久开启，即os重启后自动开启ftp服务
方法一：
cd /etc/xinetd.d ，编辑ftp服务的配置文件gssftp的设置：
vi /etc/xinetd.d/gssftp ，将 修改两项内容：

(a) server_args = -l –a 去掉-a 改为server_args = -l
(b) disable=yes改为disable=no
(c) 保存退出。

方法二：
(a) system-config-services , 进入图形界面的System services查看是否有 vsftpd项,如果没有转到2.,保存后退出

　 (b) 用redhat第三张盘 安装此服务（开始--删除/增加程序），200K左右

　 (c) #setup
　　 此时能看到vsftpd项，此时选中此services项,保存后退出.