# *GIT操作（基于ubuntu，以下操作都是基于我自己的github来操作的）*
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
4. 配置公钥
```
buntu配置:
$ ssh-keygen -t rsa -C "youremail@domain.com"
$ cd ~/.ssh
$ ls
id_rsa  id_rsa.pub  known_hosts
(此时就可以看到后缀为.pub结尾的文件就是公钥)
$ gedit id_dsa.pub
(复制该文件里面的内容)

github配置
1. Settings
2. SSH and GPG keys
3. New SSH key
4. 标题任意取，把复制的内容加到key里面去
5. Add SSH key
```
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
#### 可能会出现的问题
|出现问题|修正方法
----- | -----
error: failed to push some refs to 'https://github.com/TJTao/git-test' | git pull --rebase origin master
fatal: 'https://github.com/TJTao/GIT/' 鉴权失败 | [CSDN](https://shliang.blog.csdn.net/article/details/119698015?spm=1001.2014.3001.5506)
## GIT分支管理
### 概念
1. git所有分支之间彼此互不干扰，各自完成各自的工作和内容。可以在分支使用完之后合并到总分支上，安全、便捷、不影响其他分支工作
### 分支管理常用命令
|命令|描述
----- | -----
git branch | 查看分支
git branch <name> | 创建分支
git checkout <name> | 切换分支
git checkout -b <name> | 创建+切换分支
git merge <name> | 合并某分支到当前分支
git branch -D <name> | 删除分支
git branch -d <name> | 删除分支
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
1. 使用指令git branch -d dev删除dev分支，得到结果如下：
```
已删除分支 dev（曾为 bf0c75e）。
```
### 分支管理应用
#### 创建新分支并且修改不同分支下的文件内容，提交，提交完查看不同分支下的文件内容内容不同
1. 使用如下指令创建并切换到新分支
```
git checkout -b dev
```
2. 使用如下指令查看当前分支
```
git branch

终端输出：
* dev
  master
```
3. 修改当前dev分支的文件内容并使用指令git add添加文件，再使用git commit提交，之后使用指令cat查看该文件内容，我创建的文件名readme.md
```
git add .
git commit -m "我是dev修改内容"
cat readme.md

终端输出：
#### 我是dev分支下修改的内容
```
4. 使用指令git checkout master切换到主分支，并使用cat来查看master主分支下readme.md的内容
```
git checkout master
cat readme.md

终端输出：
#### 我只是一个测试的
```
#### 合并分支（快速合并）
1. 切换分支到master,使用如下指令合并dev分支，之后使用cat查看当前分支下的文件内容
```
git checkout master
git merge dev
cat readme.md

终端输出：
#### 我是dev分支下修改的内容
#### 我是dev分支下修改的内容
```
#### 合并冲突
1. 参照以下步骤就会出现合并冲突:
```
git checkout dev
修改dev分支下的文件内容
git add .(添加文件)
git commit -m "我是第dev修改的内容"(提交)
git checkout master(切换到master分支)
修改master分支下的文件内容
git add .(添加文件)
git commit -m "我是master修改的内容"(提交)
git merge dev(合并dev)

终端输出结果:
自动合并 readme.md
冲突（内容）：合并冲突于 readme.md
自动合并失败，修正冲突然后提交修正的结果。
```
#### 合并冲突解决方法
1. 手动将文件内容中的>>>>>>> dev删除，之后进行以下指令就可以看到合并冲突已经解决
```
git diff
git status -s(终端输出结果 UU readme.md)
git add .
git status -s(终端输出结果 M  readme.md)
git commit(就可以看到冲突已经解决)
cat readme.md(查看文件里面的内容，可以看到分支dev和分支master的内容已经合并)
```

