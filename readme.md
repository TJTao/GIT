# <h1><center>*GIT操作 0.1.0*</center></h1>

# 目录
## [1. GIT安装与配置](#1.GIT安装与配置)
### [1.1 安装与配置](#1.1安装与配置)

## [2. 拉取代码、上传代码](#2.拉取代码、上传代码)
### [2.1 拉取代码](#2.1拉取代码)
### [2.2 上传代码](#2.2上传代码)

## [3. 分支branch](#3.分支branch)
### [3.1 概念](#3.1概念)
### [3.2 常用命令](#3.2常用命令)
### [3.3 分支管理操作](#3.3分支管理操作)
#### [3.3.1 查看分支](#3.3.1查看分支)
#### [3.3.2 创建分支](#3.3.2创建分支)
#### [3.3.3 切换分支](#3.3.3切换分支)
#### [3.3.4 合并分支](#3.3.4合并分支)
#### [3.3.5 删除分支](#3.3.5删除分支)
### [3.4 分支管理应用](#3.4分支管理应用)
#### [3.4.1 创建新分支](#3.4.1创建新分支)
#### [3.4.2 合并分支（快速合并）](#3.4.2合并分支（快速合并）)
#### [3.4.3 合并冲突](#3.4.3合并冲突)
#### [3.4.4 合并冲突解决方法](#3.4.4合并冲突解决方法)

---------------------------------------------------------------
## <a id="1.GIT安装与配置">1. GIT安装与配置</a>
### <a id="1.1安装与配置">1.1 安装与配置</a>
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
## <a id="2.拉取代码、上传代码">2. 拉取代码、上传代码</a>
### <a id="2.1拉取代码">2.1 拉取代码</a>
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
### <a id="2.2上传代码">2.2 上传代码</a>
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
【可能会出现的问题】

|出现问题|修正方法
----- | -----
error: failed to push some refs to 'https://github.com/TJTao/git-test' | git pull --rebase origin master
fatal: 'https://github.com/TJTao/GIT/' 鉴权失败 | [CSDN](https://shliang.blog.csdn.net/article/details/119698015?spm=1001.2014.3001.5506)


## <a id="3.分支branch">3. 分支branch</a>
### <a id="3.1概念">3.1 概念</a>
1. git所有分支之间彼此互不干扰，各自完成各自的工作和内容。可以在分支使用完之后合并到总分支上，安全、便捷、不影响其他分支工作
### <a id="3.2常用命令">3.2 常用命令</a>
|命令|描述
----- | -----
git branch | 查看分支
git branch <name> | 创建分支
git checkout <name> | 切换分支
git checkout -b <name> | 创建+切换分支
git merge <name> | 合并某分支到当前分支
git branch -D <name> | 删除分支
git branch -d <name> | 删除分支

### <a id="3.3分支管理操作">3.3 分支管理操作</a>
#### <a id="3.3.1查看分支">3.3.1 查看分支</a>
1. 指令
```
git branch
```
2. 结果
```
* master
```

#### <a id="3.3.2创建分支">3.3.2 创建分支</a>
1. 指令
```
git branch dev
```
2. 此时就会出现两个分支,使用git branch指令查看,得到以下结果：
```
  dev
* master
```

#### <a id="3.3.3切换分支">3.3.3 切换分支</a>
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

#### <a id="3.3.4合并分支">3.3.4 合并分支</a>
1. 使用命令git checkout master 将分支切换到主分支得到结果如下:
```
切换到分支 'master'
您的分支与上游分支 'origin/master' 一致。
```
2. 使用指令git merge dev合并dev分支，我的ubuntu得到结果如下：
```
已经是最新的。
```
#### <a id="3.3.5删除分支">3.3.5 删除分支</a>
1. 使用指令git branch -d dev删除dev分支，得到结果如下：
```
已删除分支 dev（曾为 bf0c75e）。
```
### <a id="3.4分支管理应用">3.4 分支管理应用</a>
#### <a id="3.4.1创建新分支">3.4.1 创建新分支</a>
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

#### <a id="3.4.2合并分支（快速合并）">3.4.2 合并分支（快速合并）</a>
1. 切换分支到master,使用如下指令合并dev分支，之后使用cat查看当前分支下的文件内容
```
git checkout master
git merge dev
cat readme.md

终端输出：
#### 我是dev分支下修改的内容
#### 我是dev分支下修改的内容
```
#### <a id="3.4.3合并冲突">3.4.3 合并冲突</a>
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

#### <a id="3.4.4合并冲突解决方法">3.4.4 合并冲突解决方法</a>
1. 手动将文件内容中的>>>>>>> dev删除，之后进行以下指令就可以看到合并冲突已经解决
```
git diff
git status -s(终端输出结果 UU readme.md)
git add .
git status -s(终端输出结果 M  readme.md)
git commit(就可以看到冲突已经解决)
cat readme.md(查看文件里面的内容，可以看到分支dev和分支master的内容已经合并)
```

## 常用命令
【命令】
|命令|描述
--- | ---
git fetch | 用于从远程仓库获取代码库
git pull | 命令用于从远程获取代码并合并本地的版本

1. git fetch
【详细描述】
```
假设你已经配置好了一个远程仓库，并且你想要提取更新的数据，就可以使用这个命令:
$ git fetch [alias]
以上命令告诉Git去获取远程仓库有但是我没有的数据，然后可以执行:
$ git merge [alias]/[branch]
以上命令将远程仓库上的任何更新合并到你的当前分支
```
【具体用法】假设远程仓库已经有人更新了新的内容(基于我自己的仓库)
```
$ cd git-test
$ git fetch origin
终端输出:
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
展开对象中: 100% (3/3), 860 字节 | 860.00 KiB/s, 完成.
来自 https://github.com/TJTao/GIT
   91970a5..eaae3d2  master     -> origin/master
$ git merge origin/master
终端输出：
更新 91970a5..eaae3d2
Fast-forward
 readme.md | 74 +++++++++++++++++++++++++++++++++++---------------------------------------
 1 file changed, 35 insertions(+), 39 deletions(-)
$ gedit readme.md
查看更新过的内容
```

2. git pull
【详细描述】
```
git pull 其实就是 git fetch 和git merge FETCH_HEAD的简写
```
【命令格式】
```
git pull <远程主句名><远程分支名>:<本地分支名>
```

#### Personal access tokens
【消息更新】
```
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
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
```






















