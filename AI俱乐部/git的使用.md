# git的使用

简易的命令行入门教程:
Git 全局设置:

git config --global user.name "ZHQ"
git config --global user.email "1043098457@qq.com"
创建 git 仓库:

mkdir test2
cd test2
git init 
touch README.md
git add README.md
git commit -m "first commit"
git remote add origin git@gitee.com:zhqhjifvz/test2.git
git push -u origin "master"
已有仓库?

cd existing_git_repo
git remote add origin git@gitee.com:zhqhjifvz/test2.git
git push -u origin "master"


## 仓库创建
初始化当前目录为 管理仓库
git init 
// 此时目录有一 .git 目录，用来追踪管理版本

## 文件操作
添加文件
git add 文件名
// 将文件添加到暂存区中 

提交文件到仓库
git commit    
// -m 是注释   ---   git commit -m"注释"       

查看文件状态  —— 提交、修改状态
git status

查看文件修改内容
git diff 文件名

## 切换版本
查看提交历史记录
git log

git log -pretty=oneline
//简洁版

回到上一版本  (版本回退)
git reset --hard HEAD^    
// 回到上上版本 只需 HEAD^^     —— 依此类推


回到指定版本
git reset --hard 版本号   

查看版本号
git reflog


## 工作区与版本库
工作区：普通目录
版本库：工作区下的隐藏目录 .git 

版本库包含的主要项：
- stage(暂存区)
- 分支master(由 git 自动创建) 
- HEAD —— 指向 master 的指针 

回顾知新：
git add             将文件放到 暂存区 (stage)
git commit       将暂存区的内容放到 当前分支


## 撤销修改与删除文件
撤销修改 
应用场景：修改了文件，在没有提交的情况下发现修改有误，想要恢复之前修改前的文件
方法：

| 方法 |          命令           |             原理              |
| ---- | ---------------------- | ----------------------------- |
| 1.   | 手动修改                | 不解释                        |
| 2.   | git reset --hard HEAD^ | 回到上一版本                  |
| 3.   | git checkout -- 文件名  | 丢弃工作区修改                 |
| 4.   | git restore 文件名      | 撤销缓存区文件，回到追踪前状态 |

git checkout 的 -- 很重要，没有 -- ，就变成创建分支


查看删除文件
git rm -r -n --cached 文件/文件夹名称 

加上 -n 这个参数，执行命令时，是不会删除任何文件，而是展示此命令要删除的文件列表预览。

删除文件
git rm -r --cached 文件/文件夹名称

提交本地并推送到远程库
git commit -m "提交说明"
git push origin master





## 关联远程库
关联远程库
git remote add origin git@github.com:(github名)/项目名.git

删除关联远程库
git remote rm origin 


## 远程仓库关联文件
.ssh 目录文件详情：(了解即可)
位置 —— 位于用户目录下
id_rsa 文件  私钥
id_rsa 文件  公钥


known_hosts 文件 存放连接验证公钥
详细：
A通过ssh首次连接到B，B会将公钥1（host key）传递给A，A将公钥1存入known_hosts文件中，以后A再连接B时，B依然会传递给A一个公钥2，OpenSSH会核对公钥，通过对比公钥1与公钥2 是否相同来进行简单的验证，如果公钥不同，OpenSSH会发出警告， 避免DNS Hijack之类的攻击



## 提交与拷贝 远程仓库
将文件提交到 远程仓库
git push origin master

克隆远程库到本地
git clone github地址

## 解决 correct access rights and the repository exists 问题
原因：公钥出问题，需要删除 .ssh 下的文件 -> 重设用户名和邮箱 -> 重新生成 ssh 公钥

.ssh 目录： 用户目录/.ssh

步骤：
1. 设置用户名

    - git config --global user.name ‘zhandehuang’

2. 设置用户名邮箱

    - git config --global user.email ‘it_zdh@163.com’

3. 查看设置

    - git config --list
    
4. 生成 ssh 公钥

    - ssh-keygen -t rsa -C "邮箱"
    
5. 进入git网站 -> 设置 -> ssh keys -> 将.ssh 目录下 .pub 文件内容 复制粘贴 

完成。




# 分支说明
分支的作用：
master 主分支 用来发布新版本，是非常稳定的
// 一般不允许在 主分支上干活

dev 分支 
//一般在 新建dev 分支上干活、做测试，待代码稳定后合并到主分支master上来


## 创建与合并分支
分支：指的是随着提交次数，发生版本变化，所对应的时间线
1. 不同分支的时间线是独立的


创建分支
git checkout -b name 
//创建分支并切换                 -b  表示切换到创建分支

查看当前分支
git branch
// 列出所有分支，当前分支前面有一个星号

切换分支
git branch name
git checkout name

合并分支
git merge name
//将 name 的分支 合并到 当前分支        --- 相当于合并 两条时间线
// 提示信息：Fast-forward   ——  "快进模式"合并，直接把 master 指向 dev 的当前提交

删除分支
git branch -d name
// 合并完成后，可以删除被合并分支


### 合并分支冲突情况 与 解决
合并冲突发生的情况：
进行合并的两个分支   最新提交的内容  不同

冲突提示：
<<<<, =====, >>>>

<<<<  表示主分支的 修改内容
\=====  划分界限
\>>>> 表示被合并分支的 修改内容


解决方案：
修改最新提交内容一致即可


查看分支合并情况 
git log

### 分支管理策略
应用场景：合并分支，删除分支后，想要保留分支信息

默认情况下，合并分支时，使用 fast forward 模式。
该模式下删除分支后，丢失分支信息。

解决方案:
使用 -no-ff 禁用 "Fast forward" 模式

具体操作：
使用 
git merge --no-ff -m"注释" name 
代替 
git merge name

查看分支信息
git log --graph --pretty=oneline --abbrev-commit


## bug 分支
应用场景：保存临时工作区，处理即时问题

解决方案：
隐藏当前工作现场，等处理完即时问题后，恢复现场

隐藏工作区
git stash
//隐藏当前工作现场

查看工作现场
git stash list

恢复工作现场方法
1. git stash apply 
// 恢复后不删除 stash 内容 
// 需要使用 git stash drop 来删除
2. git stash pop
恢复的同时 删除 stash 内容


# 多人协作
查看远程库信息
git remote
//远程库默认名称 origin

查看远程库详细信息
git remote -v
// fetch 抓取
// push 推送

推送分支
git push origin master
//将本地更新的代码 推送到远程库中
//推送时，以当前分支为推送分支

## 抓取分支
克隆远程库到本地
git clone 远程库链接

问题：推送失败
当不同的人 推送同样的文件，修改同个地方的时候报错

解决方案：
1. 根据错误提示 ，将最新提交从 origin/dev 抓下来
git pull
//先用git pull把最新的提交从origin/dev抓下来，然后在本地合并，解决冲突，再推送。
2. git pull 失败
原因：没有指定本地dev分支与远程origin/dev分支的链接，根据提示，设置dev和origin/dev的链接
git branch --set-upstream dev origin/dev
// 参考，具体根据提示 操作
3. git pull
//由于最新的提交内容不同，合并有冲突，需要手动解决
//解决方法：修改内容相同即可(改成自己要改成的内容)
4. 解决冲突后，再提交，push 到远程库里。







参考文章：[Git使用 知乎](https://zhuanlan.zhihu.com/p/30044692)







