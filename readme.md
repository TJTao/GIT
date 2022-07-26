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
1. 使用如下指令进行远程仓库代码的拉取：
```
sudo git clone https://github.com/TJTao/git-test

成功终端输出如下：
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 10 (delta 0), reused 7 (delta 0), pack-reused 0
展开对象中: 100% (10/10), 1.18 KiB | 1.18 MiB/s, 完成.
```
### 将文件上传到远程仓库
1. 使用指令mkdir leaning创建一个目录,并进入该目录下,再使用如下指令初始化一个git仓库：
```
git init
```
2. 在当前目录下创建一个文件,并且放入内容，之后使用如下指令添加文件：
```
git add .
```
3. 使用如下指令提交文件
```
git commit -m "第一次提交"(双引号里面的内容写文档的注释)
```
4. 使用如下指令查看历史提交记录
```
git log
```
5. 使用如下指令进行远程仓库操作
```
git remote add origin https://github.com/TJTao/TJTao(git remote操作)
```
6. 使用如下指令上传远程代码并合并
```
git push origin master(git push操作)
密码部分输入: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(注意这是我自己，自己参照下面出现问题的问题3来获取这条信息）

成功终端输出结果如下：
Username for 'https://github.com': TJTao
Password for 'https://TJTao@github.com': 
枚举对象中: 4, 完成.
对象计数中: 100% (4/4), 完成.
使用 4 个线程进行压缩
压缩对象中: 100% (3/3), 完成.
写入对象中: 100% (3/3), 1.23 KiB | 1.23 MiB/s, 完成.
总共 3 （差异 0），复用 0 （差异 0）
To https://github.com/TJTao/TJTao
   bf0c75e..7905d38  master -> master
```
#### 第6步可能出现的问题
##### 1.error: failed to push some refs to 'https://github.com/TJTao/git-test'
##### 解决方法，将远程和本地仓库合并就可以了
```
git pull --rebase origin master
```
##### 2.fatal: remote origin already exists.
##### 解决方法
```
git remote rm origin
```
##### 3.在执行第6步之后会有输入远程仓库名和密码的操作，输入密码不会上传成功，解决方法参照以下网址：
```
https://shliang.blog.csdn.net/article/details/119698015?spm=1001.2014.3001.5506
```
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
#### 我是dev分支下修改的内容





















