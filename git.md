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
