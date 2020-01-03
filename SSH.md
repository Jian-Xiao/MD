# SSH 使用笔记

### 1 服务器连接
#### 1.1 使用密码连接
```
# 输入密码
ssh root@39.105.40.238
```

#### 1.2 使用密钥连接
```
# pem为密钥文件
ssh root@39.105.40.238 -i p3.pem
```

### 2 文件传输
#### 2.1 安装lrzsz
安装后，使用**rz,sz**命令即可进行文件传输，需要**终端支持**才可以（如：XShell等软件），如果只是命令行终端则需要安装**zssh**
```
# 安装lrzsz
sudo apt-get install lrzsz
# rz recieve 接受文件
rz
# sz send 上传文件，不支持文件夹
sz filename
```

#### 2.2 安装zssh
```
# 安装zssh
sudo apt-get install zssh
```
使用rz和sz的时候可能会遇到**乱码**，如果时zssh连接时使用 **Ctrl + 2** 快捷键即可
#### 2.3 实例
**服务器A**与**电脑B**之间要传输文件，服务器A要在**fa文件夹**下接收B电脑**fb文件夹**的**file文件**
```
# 1 进入fb文件夹，并使用zssh连接服务器
B\fb> zssh root@39.105.40.238 -i p3.pem

# 2 进入fa文件夹，并使用rz
A\fa> rz

# 3 按Ctrl+2进入zssh，并查看当前目录
zssh> pwd   //可知当前目录为B\fb

# 4 发送file文件
zssh> sz file

# 5 退出
zssh> quit
```