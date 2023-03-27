.. _1-本地库和远程库的交互:

1 本地库和远程库的交互
======================

1. **团队内部协作**

   -  git push: 从本地库推送到远程库

   -  git pull: 从远程库拉取到本地库

   -  git clone: 团队内其他成员克隆到本地库

2. **团队外协作**

   -  git fork: 远程库到团队外远程库

   -  git clone: 远程库到本地库

   -  git pull request: 提交修改申请

   -  git merge: 合并代码

.. _2-git-命令行操作:

2 Git 命令行操作
================

.. _21-初始化本地库git-init:

2.1 初始化本地库：git init
--------------------------

-  .git 目录中存放的是本地库相关的子目录和文件

.. _22-设置签名git-config:

2.2 设置签名：git config
------------------------

-  设置用户名和 email 地址，以区分不同开发人员的身份

-  级别

   -  项目级别 / 仓库级别：仅在本地库有效，优先于系统用户级别，保存在
      .git/config

      git config user.name xxx

      git config user.email xxx@xxx.com

   -  系统用户级别：登陆当前操作系统的用户级别，保存在 ~/.gitconfig

      git config --global user.name xxx

      git config --global user.email xxx

.. _23-添加提交及查看状态操作:

2.3 添加提交及查看状态操作
--------------------------

-  git status: 查看工作区、暂存区状态

-  git add [filename]: 将工作区的“新建/修改"添加到暂存区

-  git commit -m "commit msg" [filename]: 提交暂存区的文件到本地库

   -  -m "My first commit": 添加修改说明

.. _24-版本的前进与后退:

2.4 版本的前进与后退
--------------------

-  git log: 空格向上翻页，b向下翻页，q退出

   -  git log --pretty oneline

   -  git log --oneline

-  git reflog

-  基于索引值前进与后退

   -  git reset --hard [局部索引值]

-  使用\ ``^``\ 符号：往回退

   -  git reset --hard HEAD^

-  使用\ ``~``\ 符号：往回退n步

   -  git reset --hard HEAD~3

-  git reset

   -  --soft: 仅在本地库移动HEAD指针

   -  --mixed: 在本地库移动HEAD指针，并重置暂存区

   -  --hard: 在本地库移动HEAD指针，重置暂存区与工作区

.. _25-永久删除文件后找回:

2.5 永久删除文件后找回
----------------------

-  从本地库找回：除非将本地库删除，否则文件不会被删除，可以从本地库找回。

-  从暂存区找回：还未提交到本地库时，用git reset --hard HEAD一样可以找回

.. _26-比较文件差异:

2.6 比较文件差异
----------------

-  git diff [filename]

   -  不加任何参数，仅能比较工作区和暂存区的差异

   -  git diff HEAD [filename]

   -  git diff HEAD^ [filename] 将工作区中的文件和本地库历史记录比较

   -  不带文件名比较多个文件

.. _27-分支:

2.7 分支
--------

-  定义：在版本控制过程中，使用多条线同时推进多个任务

-  优势：

   -  同时并行推进多个功能开发，提高开发效率；

   -  各个开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响

-  操作：

   -  git branch -v: 查看所有分支

   -  git branch [branch_name]: 创建分支

   -  git checkout [branch_name]: 切换分支

   -  合并分支：

      -  第一步，切换到接受修改的分支

      -  第二步，执行merge命令 git merge [branch_name]

-  解决冲突

   -  编辑文件，删除特殊符号

   -  把文件修改到满意的程度，保存退出

   -  git add [filename]

   -  git commit -m "日志信息"，不需要带文件名

.. _3-github:

3 GitHub
========

.. _31-创建远程库:

3.1 创建远程库
--------------

.. _32-在本地创建远程库别名:

3.2 在本地创建远程库别名
------------------------

-  git remote add [nickname] [URL]

-  git remote -v

.. _33-推送操作:

3.3 推送操作
------------

-  git push [nickname] [branch]

.. _34-克隆操作:

3.4 克隆操作
------------

-  git clone [URL]

   -  完整的把远程库下载到本地

   -  创建origin远程地址别名

   -  初始化本地库

.. _35-拉取操作等同于fetch--merge）:

3.5 拉取操作（等同于fetch + merge）
-----------------------------------

-  git fetch [远程库地址别名] [远程分支名]

-  git merge [远程库地址别名/远程分支名]

-  git pull [远程库地址别名] [远程分支名]

.. _36-解决冲突:

3.6 解决冲突
------------

-  如果不是基于GitHub远程库的最新版所做的修改，不能推送，必须\ **先拉取**\ 。

-  拉去下来后如果进入冲突状态，则按照“分之冲突解决”操作解决即可。

.. _37-跨团队协作:

3.7 跨团队协作
--------------

-  进行 Fork 操作

-  本地修改，然后推送到远程

-  Pull request

.. _38-git工作流:

3.8 Git工作流
-------------

GitFlow

master / hot_fix / release / develop / feature\_
