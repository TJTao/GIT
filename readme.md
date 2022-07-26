# GIT操作（基于ubuntu）
## GIT安装与配置
### 安装与配置
1. 安装命令
```
sudo apt-get install git
```
2. 指定用户名和邮箱
```
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"
```
3. 查看用户名和邮箱
```
git config --list
```
4. 配置公钥（这里自己上网查资料配置）
### 拉取远程仓库代码和将文件上传到远程仓库
#### 拉取远程仓库代码
1. 
2. 
3. 
4. 
5. 



## GIT分支管理
### 概念
1. git所有分支之间彼此互不干扰，各自完成各自的工作和内容。可以在分支使用完之后合并到总分支上，安全、便捷、不影响其他分支工作
### 分支管理常用命令
#### 1.查看分支
```
git branch
```
#### 2.创建分支
```
git branch <name>(分支名)
```
#### 3.切换分支
```
git checkout
```
#### 4.创建+切换分支
```
git checkout -b <name>(分支名)
```
#### 5.合并某分支到当前分支
```
git merge <name>(分支名)
```
#### 6.删除分支
```
git branch -D <name>(要删除的分支名)
```
### 分支管理操作
#### 查看分支
1. 指令
```
git branch
```
2. 结果
```
* master
```
#### 创建分支
1. 指令
```
git branch dev
```
2. 此时就会出现两个分支,使用git branch指令查看,得到以下结果：
```
  dev
* master
```
#### 切换分支
1. 指令
```
git checkout dev
```
2. 结果
```
切换到分支 'dev'
```
3. 使用git branch查看已经切换到了要切换的分支,结果如下(很明显已经看到符号*已经切换到了dev):
```
* dev
  master
```
#### 合并分支
1. 使用命令git checkout master 将分支切换到主分支得到结果如下:
```
切换到分支 'master'
您的分支与上游分支 'origin/master' 一致。
```
2. 使用指令git merge dev合并dev分支，我的ubuntu得到结果如下：
```
已经是最新的。
```
#### 删除分支
1. 使用指令git branch -D dev删除dev分支，得到结果如下：
```
已删除分支 dev（曾为 bf0c75e）。
```
### 分支管理应用










