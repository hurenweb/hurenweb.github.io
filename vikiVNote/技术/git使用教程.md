# git使用教程

> 20250220周四


# 安装客户端并配置SSH公钥

1. 下载git客户端，官网下载`git for windows`，或者国内淘宝镜像下载。
2. 一路默认安装，在桌面右键出现`git bash here`表示安装结束。
3. 在github官网注册账户，创建仓库。
4. 本地创建ssh key。进入目录`C:\Users\huren\.ssh`，生成github-ssh公钥，`ssh-keygen -t ed25519 -C 'hurenweb@qq.com'`，一路回车；也可以更改文件名：`ssh-keygen -t ed25519 -C 'hurenweb@qq.com' -f ~/.ssh/id_rsa_github`。
5. 复制`id_ed25519.pub`里面的key。在github上创建SSH公钥。
6. 测试连接：`ssh -T git@github.com`如果是第一次的会提示是否continue，输入yes回车，会看到`You've successfully authenticated`。

两个官方文档：
[github文档](https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[gitee文档](https://help.gitee.com/base/account/SSH%E5%85%AC%E9%92%A5%E8%AE%BE%E7%BD%AE)


# 设置或修改默认项

```cpp
// 设置或修改默认项
git config --global user.name "huren"
git config --global user.email "hurenweb@qq.com"
git config --global user.password "123456"

// 查看配置
git config --list 
```


# 分支操作

```cpp
// 查看所有分支
git branch

// 创建分支
git branch huren

// 创建+切换分支
git switch huren
git checkout huren

// 合并分支
git merge develop

// 删除分支
git branch -d huren
// 删除远程分支
git push origin --delete develop2022
```


# 添加和修改仓库地址

如果你在github创建了一个新的仓库，你想把你现有的本地代码push到你的git仓库。
这时常用的方式有2种，
一种是clone下来你带有.git属性的远程空文件夹，然后把本地代码放进去，最后push到远程。
还有一种就是本地用命令行添加仓库地址，方法如下：

```cpp
git init
git remote add origin https://git.XXXX.com/XXX/XXX.git
// 这样成功后就能正常add代码了。
```


# 拉取和推送代码

```cpp
// 查看状态，常用命令
git status

// 克隆项目
git clone url地址

// 把`工作区`的所有变化，添加到`版本库/暂存区`
git add .

// 进一步提交，并提交说明信息
git commit -m "修改登录页面"

// 拉取代码到本地
git pull
// 拉取代码到本地
git pull origin master
// 设置拉取默认分支
git pull --set-upstream origin master/huren

// 推送到远程服务器
git push
// 推送到远程服务器
git push origin master
// 设置推送默认分支
git push --set-upstream origin master/huren
```


# 工作区、暂存区和版本库的回退操作

```cpp
// 使用master/main分支的目录树，替换掉暂存区的目录树。工作区不受影响。
git reset HEAD

// 删除暂存区的目录树。工作区不受影响。
git rm --cached

// 使用暂存区全部或指定的文件替换掉工作区的文件。工作区未add的文件会被覆盖。也就是放弃修改。
git checkout .
git checkout --

// 使用HEAD指向的master/main分支的文件，替换掉暂存区和工作区的文件。回退最彻底的。
git checkout HEAD .
git checkout HEAD
```


# 暂存本地修改，再pull代码

命令行如下：
```cpp
// 暂存本地修改
git stash

// pull代码
git pull

// 恢复本地修改
git stash pop
```


# 其它命令行

```cpp
// 查看提交历史，与各次的提交说明。
git log

// 比较工作区与暂存区的差异，就是比较看看你到底都做了什么修改。
git diff

// 退出(quit)
:q

// 取消设置凭证帮助，解决报错`fatal: Authentication failed for`的情况。然后再clone就提示输入用户名和密码了。
git config --system --unset credential.helper

// 解决无法添加子文件夹的问题
git rm --cached myFiles
git add myFiles
```


# 其它信息

1. 操作时双击tab键的自动提示/补全功能。
2. 配置文件`.gitignore`，可以设置上传时忽略的文件。
3. `.` : 一个点代表当前目录，`..`：两个点 代表上级目录。
4. 删除git的配置，删除`.ssh`文件即可，位置为`C:\Users\huren\.ssh`。


# 不提交vue.config.js

```cpp
// 不提交vue.config.js，情况是在.gitignore文件里面没有禁止提交这个文件。
git update-index --assume-unchanged vue.config.js
git update-index --assume-unchanged package-lock.json
git update-index --assume-unchanged dist
```
