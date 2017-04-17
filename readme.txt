git学习
 一.创建版本库
    1、创建一个空的目录
        mkdir learngit
        cd learngit
        pwd   显示当前目录
    2、git init 命令把目录变成git可以管理的仓库
		命令执行后，当前目录会多一个.git的目录，若没看到说明这个目录默认是隐藏的，使用ls -ah 
    3、文件添加到版本库
         在learngit或者其子目录下添加一个文件 readme.txt 
		 把一个文件放到Git仓库只需要两步。
		 第一步，用命令git add告诉Git，把文件添加到仓库：
		 $ git add readme.txt
		 
		 第二步，用命令git commit告诉Git，把文件提交到仓库：
         $ git commit -m "wrote a readme file"

		 -m后面输入的是本次提交的说明
二.时光穿梭机
    
     git status 命令查看仓库当前的状态
	 git diff readme.txt 查看修改了什么内容（查看difference）

	 git diff    #是工作区(work dict)和暂存区(stage)的比较
	 git diff --cached    #是暂存区(stage)和分支(master)的比较
	 
	 *git diff 命令详解
	 
	 1.版本回退
		git log  命令显示从最近到最远的提交日志（日志中包含提交的内容和提交的id等信息）
		git log --pretty=oneline 如果嫌输出信息太多，可以加上--pretty=oneline参数  
		
		git reset --hard^ 回到上一个版本（回到过去的版本）
		git reset --hard 版本id (回到过去版本的未来版本，前提是知道未来版本的id，前几位即可)
		git reflog 记录每一次命令
		
		小结
		HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id
		穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
		要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本
	
	 2.工作区和暂存区
		
		工作区：Working Directory
				就是在你电脑上能看到的目录
		
		版本库：Responsitory
				工作区有一个隐藏目录.git,这个不算工作区,而是git的版本库
				
			git的版本库中存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。
		
			把文件往git的版本库添加的时候，是分成两步执行的：
			第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
			第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
			
	3.管理修改
		*git diff 命令详解
		
	4.撤销修改
		 
							
