#git常用命令
#### 1.创建版本库
mkdir leargit  
cd learngit  
pwd  (显示当前目录)  
git init  

#### 2.把文件添加到版本库  
创建txt文件，用Notepad++,编码格式UTF-8 withoutBOM  
git add readme.txt  （可以一次提交多个 git add file1.txt file2.txt）
git commit -m "add readme.txt" (-m后面输入本次提交说明)  

####3.修改删除命令
  git status 显示仓库当前状态  
  git diff 查看修改的具体内容  
  git log 显示从最近到最远的提交日志  
  git log --pretty=oneline 精简提交日志  
  git reset --hard HEAD^ 回退到上一个版本 (HEAD表示当前版本，上上版本HEAD^^,往上一百个版本HEAD~100)  
  git reset --hard commit id  回到当前版本 （commit id 为当前版本提交的一串数字，可以只写几位）  
  git  reflog  查看命令历史  
  git checkout -- readme.txt 把readme.txt文件在工作区的修改全部撤销  
  rm text.txt 删除text文件  
  git rm text.txt 删除版本库里的文件  
  git checkout -- text.txt 恢复被误删的文件
####4.远程库
  git remote add origin git@server-name:path/repo-name.git  关联一个远程库  
  git push -u origin master 第一次推送master分支的所有内容  
  git push origin master 推送最新修改；  
***
**注意**：could not read from remote respository问题解决  
删除远端和当前key，重新生成key   
ssh-keygen -t rsa -C 邮箱 连敲两次回车键  
会在本地C:\Users\你的用户名.ssh生成文件夹，里面有id_rsa和id_rsa.pub两个文件   
然后复制id_rsa.pub文件里面的内容，到https://github.com/settings/keys新建一个  
然后设置远程地址：（上面新建的） 
git remote add origin_new 新的地址   
git remote –v查看   
git push origin_new master重新推送 
***   
####5.从远程库克隆  
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。  
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
####6.对分支的操作
git branch 查看分支  
git branch <name> 创建分支  
git checkout <name> 切换分支  
git checkout -b <name> 创建+切换分支  
git merge <name> 合并某分支到当前分支（fast-forward 快速合并）  
git branch -d <name> 删除分支
git log --graph 查看分支合并图（git log --graph --pretty=oneline --abbrev-commit）  
git merge --no-ff -m "<description>" <name> 禁用ff模式普通合并分支  
git stash 把现场工作保存一下  
git stash pop 回到现场工作
git stash list 查看工作现场
git stash apply stash@{x} 恢复到指定的stash  
git branch -D <name> 丢弃一个没有被合并过的分支  
####7.多人协作
git remote -v 查看远程库  
git push origin branch-name 从本地推送分支  
git pull 抓取远程提交  
git checkout -b branch-name origin/branch-name 在本地创建和远程分支对应的分支  
git branch --set-upstream branch-name origin/branch-name 建立本地分支和远程分支的关联 
####8.标签管理  
git tag<name> 新建标签，默认HEAD 也可指定commit id   
git tag -a <tagname> -m "blalala" 指定标签信息  
git tag -s <tagname> -m "blablabla..." 用PGP签名标签  
git tag 查看所有标签    
git push origin <tagname>可以推送一个本地标签；  
git push origin --tags可以推送全部未推送过的本地标签；  
git tag -d <tagname>可以删除一个本地标签；  
git push origin :refs/tags/<tagname>可以删除一个远程标签。 
