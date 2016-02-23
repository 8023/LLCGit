# LLCGit

##### 查看本地SSH:  
* `cd ~/.ssh` 如果有ssh `ls` 查看 ***_id_rsa_*** 私钥 ***_id_rsa.pub_*** 公钥



##### 检测SSH  
* `ssh -T git@github.com`  失败：Permission denied (publickey).

* `ssh -T git@git.yuandalu.com` 成功：Welcome to GitLab, llc!

##### 打开公钥 : 
* `vi id_rsa.pub` 

	```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC7odIM9m+pTppzApEXekWbSkk3pFxQJqEnxNyNdV5I2m3zUOkkmsSlVwEdXGwEamLrgx4e8zJCbsQyfPfpWEBW1vxf4FPfKln2hfXuWOAxMqPnhamwmIX9I1Rp4nyhCSv1VZwTFqa8dMdbfibtW2mF3HZND9mE/FI+nfXTgrT/c/PUDLRmmq5yc4MUQItdXYALqW7Xgy9nimpJrPAZro7aB3n6u/pj5Jrkrw3K3Yqi1mbhnCr0Fcua5JR1LSyLkPuIfzFkQgCAwxgJ1Ix02MHhdsg0XJp5SgqW/uX4qrupXDpE0Sw2aQEzqIU+avEKLjvjcz2c50OffZ+qOtzGyNaf 8023llc@sina.cn

	```

#####  生成 ssh :
* `$ ssh-keygen -t rsa -C "your_email@youremail.com" `

##### 添加SSH keys:

* git@git.yuandalu.com [GitLab SSH Keys](http://git.yuandalu.com/profile/keys)
* git@github.com [Github SSH Keys](https://github.com/settings/ssh)

##### 仓库操作(Repositories):

* 获取仓库 git地址后克隆到指定文件夹 

	`cd Desktop`
	
	</br>
	`git clone git@github.com:8023/LLCFramework.git`
	
	</br>
	`cd LLCFramework`
	
	</br>
	`git status -s`
	
* 修改
	
	`git add *`
		
	</br>
	`git commit -m '提交log'` 或 `git commit -a` 进入log的编辑文件 vi编辑保存退出后就行。

##### 分支

* 查看本地分支:

	 `git branch` 不带参数：列出本地已经存在的分支，并且在当前分支的前面加“*”号标记
* 列出远程分支

	 `git branch -r` 
* 创建本地分支

	`git branch branchname`
* 删除branchname分支
	
	`git branch -d branchname` d 如果当前分支有没合并的会报错 D 强制删除
* 删除远程branchname分支

	`git branch -d -r branchname `
* 切换分支

	`git checkout branchname`
* 克隆远程单个分支

	`git clone -b branchname` 
* 合并分支
	
	1.切换到将要合并到的分支：`git checkout master`
	
	2.合并分支到当前分支：`git merge branchname`
	
	3.解决冲突： 查看：`git status -s` 缓存:`git add *` 提交到本地：`git commit -m` 
	
* 回滚

	 
	git代码库回滚: 指的是将代码库某分支退回到以前的某个commit id
	
	【本地代码库回滚】：
	
	git reset --hard commit-id :回滚到commit-id，讲commit-id之后提交的commit都去除
	
	git reset --hard HEAD~3：将最近3次的提交回滚
	
	 
	
	【远程代码库回滚】：
	
	这个是重点要说的内容，过程比本地回滚要复杂
	
	应用场景：自动部署系统发布后发现问题，需要回滚到某一个commit，再重新发布
	
	原理：先将本地分支退回到某个commit，删除远程分支，再重新push本地分支
	
	操作步骤：
	
	1、`git checkout the_branch`
	
	2、`git pull`
	
	3、`git branch the_branch_backup` //备份一下这个分支当前的情况
	
	4、`git reset --hard the_commit_id` //把the_branch本地回滚到the_commit_id
	
	5、`git push origin :the_branch` //删除远程 the_branch
	
	6、`git push origin the_branch` //用回滚后的本地分支重新建立远程分支
	
##### 远程

* 提交到远程服务器：`git push origin master`

* 从远程服务器拉取：`git pull`



