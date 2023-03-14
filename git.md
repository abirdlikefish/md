# GIT

## 初始化版本库
` git config --global user.name "Your Name" `[^1]  
`git config --global user.email "email@example.com"`  
` git init `    在当前目录创建版本库  

[^1]: 注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。  

## 查看
` git config --global user.name `  
`git config --global user.email `  

## 提交文件


` git add -A `  添加全部  
` git add -p `  选择添加  
` git add helloworld.cpp `  
` git commit -m " your illustration " `  

## 查看仓库状态

` git status `  
` git diff `  

## 修改

`git mv helloworld.cpp hello.cpp`   移动文件  
` git reset --hard HEAD^ `  退回上个版本  
` git reset --hard HEAD^^ ` 退回上上个版本  
` git reset --hard HEAD~2 ` 退回上上个版本  
` git reset --hard commitID ` 退回commitID为commitID的版本  
` git reset HEAD helloworld.cpp ` 撤销暂存区修改,放回工作区  
` git checkout -- helloworld.cpp ` 撤销工作区修改，回到暂存区或版本库  
` git rm helloworld.cpp ` 删除文件,需commit  


## 查看历史
` git reflog `  查看历史指令,可用于查找版本号  
` git log `     查看日志 可被reset修改  
` git log --graph --pretty=oneline --abbrev-commit `  

## 初始化远程库

` ssh-keygen -t rsa -C "youremail@example.com" ` 生成ssh密钥  
` git remote add origin git@github.com:abirdlikefish/repositoryName.git `   
关联GitHub上的库 origin为习惯名  
` git remote rm origin ` 解除了本地和远程的绑定关系  
` git clone git@github.com:abirdlikefish/snake.git `  克隆库到本地  

## 控制远程库
` git fetch origin ` 更新本地的远程库信息  
` git push -u origin master ` 将本地库master分支推送到origin  
` git push origin master ` 之后推送不用加-u  
` git remote ` 查看远程库信息  
` git remote -v ` 查看远程库详细信息  
` git clone git@github.com:abirdlikefish/snake.git `  克隆库到本地  
` git checkout -b dev origin/dev `  创建远程`origin`的`dev`分支到本地
` git pull ` 抓取远程库  
` git branch --set-upstream-to <branch-name> origin/<branch-name> ` 建立本地分支与远程库分支联系  



## 分支相关
` git checkout -b dev ` 创建并切换到 `dev` 分支  
` git switch -c dev ` 创建并切换到 `dev` 分支  
` git checkout dev `    切换分支为`dev`  
` git switch dev `    切换分支为`dev`  
` git branch dev `  创建分支  
` git branch `   查看分支  
` git branch -d dev `   删除`dev`分支  
` git branch -D dev `   强制删除`dev`分支,即使未合并  
` git merge dev `  合并指定分支(dev)到当前分支  
` git merge --no-ff -m "merge with no-ff" dev ` 合并指定分支(dev)到当前分支并禁用Fast forward (从分支历史上就可以看出分支信息)  
` git stash `   暂时储存工作区  
` git stash pop `   弹出储存的工作区  
` git stash list `  查看储存的工作区列表  
` git stash apply `  恢复储存的内容但不删除  
` git stash drop `  删除储存的工作区  
` git cherry-pick commitID `  将commitID做的修改复制到当前分支  
` git rebase `  整理分叉提交历史  


## 标签
` git tag ` 查看所有标签  
` git tag tagName `  给当前分支最近commit添加标签tagName  
` git tag tagName commitID`  给commitID添加标签tagName  
` git show tagName `    显示tagName详细信息  
` git tag -a tagName -m "illustration" `    创建带有说明的标签，用-a指定标签名，-m指定说明文字  
`git push origin tagName` 可以推送一个本地标签  
`git push origin --tags`    可以推送全部未推送过的本地标签  
`git tag -d tagName`  可以删除一个本地标签  
`git push origin :refs/tags/tagName`  可以删除一个远程标签  