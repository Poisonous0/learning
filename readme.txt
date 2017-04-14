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
