# 如何使用git下载&上传项目到GitHub

首先是GitHub这边，需要先创建一个库。

如果是第一次搞的话，要先去`C:\Users\你的用户名`找一下有没有`.ssh\`这个文件夹。

如果没有的话，则需要在此处先右键`git bash here`。然后输入命令
```
ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```
回车。

然后去找到`.ssh\`这个文件夹，随便用一个文本编辑器打开里面的`id_rsa.pub`文件，<kbd>CTRL</kbd>+<kbd>A</kbd> <kbd>CTRL</kbd>+<kbd>C</kbd>。

接下来需要打开GitHub，点你的头像，然后下面有一个`Settings`，来到`SSH...`页面，然后点击`New SSH key`。在`Title`处给你的key取个名字，然后在下面`Key`处<kbd>CTRL</kbd>+<kbd>V</kbd>，然后点`Add SSH key`。

然后你可以重新打开你的git bash窗口，输入
```
ssh -T git@github.com
```
验证一下，如果接下来出现了`Hi 你的GitHub用户名...`就证明SSH key添加成功了。

然后输入
```
git config --global user.name  "你的GitHub用户名" 
git config --global user.email "你的GitHub注册邮箱"
```
这个应该是一次性操作。

至此，git和GitHub的联系就建立好了。如果你想要把GitHub上的仓库克隆到本地，去你的GitHub页面，点击`Code`，然后在上面的`Clone`那选择`SSH`，然后点击右边的复制按钮。然后去你的本地工作区，`git bash here`,然后输入代码
```
git clone 你之前复制的那段
```
如果不出意外的话，现在你已经把你的GitHub仓库克隆到本地了，你会在你目前bash的文件夹发现一个和GitHub仓库同名的新文件夹。

然后在文件夹中修改/添加你想要更改的内容。

回到bash窗口，输入
```
cd GitHub 仓库名
```
进入到刚才多出来的那个新文件夹，这里要注意一下bash用户名的最右边那个蓝色括号内的内容，那个就是系统默认的新建分支的分支名。

如果现在你已经完成了你对仓库的所有修改，那么输入
```
git add .
//这个.的意思是全部
git commit -m "对此次更改的说明"
git push -u origin main
//这里的main是系统默认的新建分支名，其实就是你当前的分支名
```
即可上传。

现在来到浏览器，打开你的GitHub仓库，你就会发现刚才所做的更改已经生效了。