## MySQL使用笔记

### 1 装mysql没有设置密码
```
# 1 查看默认用户和密码
sudo cat /etc/mysql/debian.cnf 
mysql -u debian-sys-maint
# 2 连接到mysql数据库
mysql> use mysql;
# 3 修改root用户密码               
mysql> update mysql.user set authentication_string=password('123456') where user='root' and Host ='localhost';
# 4 更新    
mysql> update user set plugin="mysql_native_password";     
mysql> flush privileges;
# 5 退出
mysql> quit; 
```

