# Git 使用笔记

### 1 Git 第一次使用
#### 1.1 仓库建立

首先要在GitHub或者Gitee上创建一个**新远程仓库**

```
# 1 在Linux上安装Git
sudo apt-get install git

# 2 在初始化本地仓库
git init

# 3 Git的全局或本仓库配置
git config --global user.name "Jian-Xiao"   //没有global就只针对本仓库
git config --global user.email "email@qq.com"

# 4 为本地仓库指定远程仓库
git remote add origin https://gitee.com/Jian-Xiao/Segment.git
```

#### 1.2 上传

至此，本地仓库已经与远程仓库建立连接，接下来就是**上传**文件

```
# 1 将工作区文件添加到暂存区
git add README.md   //将单个改动放入暂存区
git add .           //将所有改动放入暂存区

# 2 将暂存区提交到本地仓库
git commit -m "填写提交说明" 

# 3 将本地仓库推送到远程仓库的master分支
git push origin master

```

#### 1.3 同步
然后，也可以从远程仓库**同步**最新版本
```
# 1 将远程仓库克隆到本地
git clone https://gitee.com/Jian-Xiao/Segment

# 2 获取最新版本
git pull origin master

```