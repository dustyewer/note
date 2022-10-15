ssh-keygen -t rsa -C "你自己注册GitHub的邮箱"
到GitHub上，打开“Account settings”--“SSH Keys”页面，然后点击“Add SSH Key”，填上Title（随意写），在Key文本框里粘贴 id_rsa.pub文件里的全部内容。
git config --global user.name "你的GitHub登陆名"
git config --global user.email "你的GitHub注册邮箱"

# 本地库和远程库关联
git remote add <name> <url>
name 为远程仓库的名字，自定义，一般为origin，
url 为远程仓库地址，就是你自己新建的那个仓库的地址
例如：git remote add origin git@github.com:dustyewer/note.git

#第一次push
git push -u origin master

#commit 合并 -i 的参数是不需要合并的commit的hash值
git rebase -i xxx
pick的 会保留
squash的会被合并掉

#新建并切换到本地dev分支
git checkout -b dev

#stash
git stash 暂存
暂存后可以切换到其他分支，切回来后
git stash pop 取最近一次
