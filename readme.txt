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
		
	4.**撤销修改
	
	
		1）git checkout -- file可以丢弃工作区的修改：
		
			命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
			
			一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
			
			一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
			
			总之，就是让这个文件回到最近一次git commit或git add时的状态。
		
			注：git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令，我们在后面的分支管理中会再次遇到git checkout命令。
		
		2）用命令git reset HEAD file可以把暂存区的修改撤销掉（unstage），重新放回工作区
	
		场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
		场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
		场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
		
	5.删除文件
	
		命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容。
	
三、远程仓库
	1.添加远程仓库
	 创建远程仓库
		第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。
			   如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
				$ ssh-keygen -t rsa -C "youremail@example.com"
				邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可

				如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

		第2步：登陆GitHub，打开"Account settings"，"SSH Keys"页面：

				然后，点"Add SSH Key"，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
	 添加远程库
		第1步：登陆GitHub,在右上角找到"Create a new repo"按钮，创建一个新的仓库
				在Repository name填入  testgit  ，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库
				目前，在GitHub上的这个learngit仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。
				现在，我们根据GitHub的提示，在本地的 testgit  仓库下运行命令：
				
				$ git remote add origin git@github.com:Poisonous0/testgit.git
				
				添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。、
				
		第2步：就可以把本地库的所有内容推送到远程库上：
			$ git push -u origin master
			
			把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
			由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
			推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样：
			从现在起，只要本地作了提交，就可以通过命令：

			$ git push origin master
			
			把本地master分支的最新修改推送至GitHub
			
		小结

			要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；

			关联后，使用命令git push -u origin master第一次推送master分支的所有内容；

			此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
							
	2.从远程仓库克隆
		 git clone git@github.com:michaelliao/gitskills.git
四、分支管理
	1.创建与合并分支
		查看分支：git branch

		创建分支：git branch <name>

		切换分支：git checkout <name>

		创建+切换分支：git checkout -b <name>

		合并某分支到当前分支：git merge <name>

		删除分支：git branch -d <name>