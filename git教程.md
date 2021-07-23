

https://github.com/boniu-w/gitskills

### 1. 在新電腦上生成ssh 私钥

列出 所有 .ssh文件

ls -al ~/.ssh  

运行命令

ssh-keygen -t rsa -C "boniu-w@live.cn"  # 按三次回车

cat ~/.ssh/id_rsa.pub生成新的SSH
登陆github,点击头像-settings-new SSH,复制新生成的SSH

echo "# gitProject" >> README.md
git init

 // 添加所有更改 或某个更改
git  add .    
git add README.md         

git commit -m "first commit"

git remote add origin https://github.com/boniu-w/gitProject.git       #给git仓库 提供远程地址 关联远程库

git push -u origin master

1. 安装完成后 进一步设置
     git config --global user.name "Your Name"
     git config --global user.email "email@example.com"
     之后,在一个空的文件夹下输入
     git init
     会生成一个.git 的文件 表示这个文件夹 是一个 git可以管理的本地库

2. 要关联一个远程库，使用命令

>   git remote add origin git@server-name:path/repo-name.git；


关联后，使用命令

> git push -u origin master

第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常
工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，
真是太方便了！

3. 要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
   Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

提交一个项目到GitHub
比如在gitskills文件夹下 这是我在GitHub上clone的repository,cd到这个文件夹下,右键打开bash,出现命令
窗口,执行git语句
		git add README.md
		git commit -m "first commit"
		git remote add origin https://github.com/boniu-w/gitProject.git
		git push -u origin master

就可以了
第三条 命令 再第一次执行过以后 就可以省略掉了 因为 在此文件夹下的.git文件中已保存了 地址
第四条命令中的 -u 也可以省略掉了

4. git log --pretty=online
   查看历史记录
5. 创建分支
     git checkout -b dev
     -b参数表示创建并切换，相当于以下两条命令：
     git branch dev
     git checkout dev
     查看当前分支,git branch命令会列出所有分支，当前分支前面会标一个*号
     git branch
     然后，我们就可以在dev分支上正常提交
     git add test1.txt 
     git commit -m "branch test"
6. 现在切换回master

  git checkout master

  切换回master分支后，再查看一个readme.txt文件，刚才添加的内容不见了！
  因为那个提交是在dev分支上，而master分支此刻的提交点并没有变
  现在，我们把dev分支的工作成果合并到master分支上

  git merge dev

  git merge命令用于合并指定分支到当前分支。合并后，再查看readme.txt的内容，
  就可以看到，和dev分支的最新提交是完全一样的。
  注意到上面的Fast-forward信息，Git告诉我们，这次合并是“快进模式”，也就是
  直接把master指向dev的当前提交，所以合并速度非常快
  当然，也不是每次合并都能Fast-forward，我们后面会讲其他方式的合并。
  合并完成后，就可以放心地删除dev分支了

  git branch -D dev

  删除后，查看branch，就只剩下master分支了：
  git branch
  因为创建、合并和删除分支非常快，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，
  这和直接在master分支上工作效果是一样的，但过程更安全

7. 小结
   Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>  // name: 其他分支名

删除分支：git branch -D <name>

8. 删除库中文件
       git rm 
9. 查看库中文件列表
       git ls-files

#### 代码冲突

#### 如何解决failed to push some refs to git

1. 可以通过如下命令进行代码合并【注：pull=fetch+merge]
   git pull --rebase origin master

   在使用git的过程中经常需要使用到git pull命令，在更新远端代码的同时如果与本地代码产生冲突了，

   那么冲突的文件中就出现了需要手动合并的部分，而git pull --rebase不同的地方则是当有这些冲突存在时，git帮我们自动创建了一个新的分支，并且git告诉你接下来你要在这个新的分支上处理这个冲突，

#### 分支 等

1. 查看本地分支

git branch

2. 查看本地与远程分支

git branch -a

3. 切换分支

git checkout branchName

4. 创建并切换分支

git checkout -b newBranchName

5. 切换分支

git checkout remoteBranchName

6. 删除本地分支

git branch -d branchName

7. 删除远程分支

git push origin -d branchName

#### 版本回退

git log

  // push 之前

  ----------没有add ----------

  git checkout .     更新到工作目录
  ---------- add 后----------

放弃所有缓存

  git reset HEAD .

放弃某个 文件

  git reset HEAD filepathname 


  ----------commit 后----------

回退到上个版本

  git reset --hard HEAD^

回退到上上个版本

  git reset --hard HEAD^^

回退到上100个版本

  git reset --hard HEAD~100

回退到指定版本

  git reset --hard b863671 

  //  push 后

  git revert



#### 回退单个文件

```java
git log 完整文件名
git reset 版本号 完整文件名
   
```

#### 项目关联多个 库

​	git remote add wg 仓库地址    // wg 对应 原来的origin 
​	

	git remote -v  // 查看项目 关联的所有库
	
	提交时
	git push wg master 

#### git log 之后退出

​	英文状态下按Q

#### git 如果操作失误,错误的使用 git reset --hard 回滚

 使得工作目录改变了,可以使用git reflog,看到相应的快照,可以回滚回去.

```java
git reset --hard 分支名  // 让本地代码与分支代码保持一致
```

#### git 的一个bug

```java
error: RPC failed; curl 18 transfer closed with outstanding read data remaining
fatal: The remote end hung up unexpectedly
fatal: 过早的文件结束符（EOF）
fatal: index-pack 失败
```

解决:

究其原因是因为curl的postBuffer的默认值太小，我们需要调整它的大小，在终端重新配置大小,在这里，把postBuffer的值配置成500M是不够用的,我设成了2G 才好

```java
 git config --global http.postBuffer 524288000
```

这样已经配置好了，如果你不确定，可以根据以下命令查看postBuffer。

   git config --list

---



#### github 下载单个文件夹

```java
git remote add -f origin 仓库地址
git config core.sparseCheckout true
echo "单个文件夹" >> .git/info/sparse-checkout
git pull origin master    
```



#### 查看单个文件的提交历史

```java
  git log  文件名(具体到文件详细路径)
```



#### git中Already up to date 问题

- 这个问题的原因是当前分支的代码与master分支代码不同步

  - 解决方法:

    ```java
    git checkout .  // 放弃本地缓存
    ```

#### 保留本地修改的同时,拉取 合并远程代码

```java
	git stash save "comment 你的一些注释" 
    git pull origin dev_wz
    git stash pop
```

#### git 修改分支名

```java
git branch -m 原名 新名
```

#### git 各种命令解释

1. git stash save "comment 你的一些注释" // 

   - 当正在dev分支上开发某个项目，这时项目中出现一个bug，需要紧急修复，但是正在开发的内容只是完成一半，还不想提交，这时可以用git stash命令将修改的内容保存至堆栈区，然后顺利切换到hotfix分支进行bug修复，修复完成后，再次切回到dev分支，从堆栈中恢复刚刚保存的内容

   - 总的来说，git stash命令的作用就是将目前还不想提交的但是已经修改的内容进行保存至堆栈中，后续可以在某个分支上恢复出堆栈中的内容。这也就是说，stash中的内容不仅仅可以恢复到原先开发的分支，也可以恢复到其他任意指定的分支上。git stash作用的范围包括工作区和暂存区中的内容，也就是说没有提交的内容都会保存至堆栈中。

2. git stash list  // 查看stash了哪些存储

3. git stash pop  // 取出stash的存储到当前的工作目录,并删除其他的stash,默认取第一个stash,即stash@{0}

4. git add .  // 缓存本地代码

5. git commit -m "comment"  // 提交本地代码到本地仓库

6. git commit --amend  // 修改最后一次提交的注释

7. git push origin master  // 推送本地库的代码到远程库

8. git diff  // 此命令比较的是工作目录(Working tree)和暂存区域快照(index)之间的差异

   也就是修改之后还没有暂存起来的变化内容

9. git diff --cached  // 查看本地代码与缓存区代码的不同

10. git diff --staged  // 同上, 查看本地代码与缓存区代码的不同

11. git checkout .  // 放弃本地缓存,也就是add . 之后的东西

12. git fetch  // 将远程库的代码拉取到本地,但还没有融合到本地代码中,用户可以先检查一下拉取的代码是否有要修改的地方,再决定是否要融合;拉取之后 使用 git diff 可以看到不同,然后idea 也会显示冲突的地方,然后修改,之后 add. -> commit -> push

13. git pull // 相当于 git fetch + git merge



#### github 下载 速度 慢

**方法一：**

```js
ping github.com
ping github.global.ss.fastly.net
ping github-cloud.s3.amazonaws.com
```



  **从GitHub下载文件一直非常慢，查看下载链接发现最终被指向了Amazon的服务器，下载地址是http://github-cloud.s3.amazonaws.com/，从国内访问Amazon非常慢，所以总是下载失败，解决方法时更改host文件，使该域名指向香港的服务器：**

**更改hosts文件：**

- Windows

> 更改`C:\Windows\System32\drivers\etc\hosts`文件，在文件中追加`219.76.4.4 github-cloud.s3.amazonaws.com`, 将域名指向该IP即可

- Mac

> 执行 `sudo vi /etc/hosts` 追加 `219.76.4.4 github-cloud.s3.amazonaws.com`



**最后执行**`**ipconfig /flushdns**`**命令，刷新 DNS 缓存。**

**方法二：**

```xml
#github
52.216.128.147 github-cloud.s3.amazonaws.com
140.82.114.4 github.com
199.232.69.194 github.global.ssl.fastly.net
```



​    **https://www.ipaddress.com/ \**使用 IP Lookup 工具获得下面这两个github域名的ip地址，该网站可能需要梯子，输入上述域名后，分别获得github.com和github.global.ssl.fastly.net对应的ip，比如192.30.xx.xx和151.101.xx.xx。准备工作做完之后，打开的hosts文件中添加如下格式，IP修改为自己查询到的IP：\**

\**192.30.xx.xx github.com
151.101.xx.xx github.global.ssl.fastly.net\**

\**\*\*最后执行\*\*`\*\*ipconfig /flushdns\*\*`\*\*命令，刷新 DNS 缓存。\*\*修改后的下载速度能达到 200KB/S 以上。\*\*\*\*\****

 **方法四：**

​    **这个需要开启代理，有些人开启后发现下载速度还是上不去，因为GitHub没被qiang，只是限速了，所以没走代理。需要修改pac.txt文件。在pac里面添加一行规则。后面需要加\*。因为下载的网站不是github.com。而是涉及很多个github\**\**.com 后面忘记了，但是都是github打头的。使用下面的规则github才全部走代理。**

```cpp
  "||github*.com",
```



**方法五：**

   **如果运行了SS（纸飞机）等代理工具，方法四只能用于加速网页浏览下载github仓库项目，但是如果你装了git或者sourcetree等其他git管理工具，使用方法四是无法走代理加速的。你需要设置自己的git才能使用代理。在C:\Users\用户名\.ssh 目录下config文件里，只有使用git生成过ssh密钥的才有此目录，没有config文件则新建一个，注意文件没有后缀。添加如下内容**

```cpp
Host github.com



ProxyCommand connect -H 127.0.0.1:1080 %h %p   #-S为socks



HostName %h



Port 22



User git



IdentityFile  ~/.ssh/id_rsa 



IdentitiesOnly yes
```

**下载connect.exe。放到git安装目录的bin目录下。**

**下载地址：https://download.csdn.net/download/qing666888/11973853**

**再次启动sourcetree进行SSH模式下clone 拉取代码，速度直接就上10M/S了，当然取决于你SSR的速度。**









#### git命令

| <span style="white-space: nowrap; width:30%">命令&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;</span> | <span style="white-space: nowrap;"> 解释&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; </span> | <span style="white-space: nowrap;">例子&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;</span> |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| git reflog show --date=iso 分支名                            | 查看分支的各种信息,有创建时间,在此分支上有过的操作           | git reflog show  --date=iso dev                              |
| git reflog                                                   | 查看当前分支的操作 日志                                      |                                                              |
| git branch -m 原名 新名                                      | 修改分支名                                                   |                                                              |
| git remote add wg 仓库地址                                   | 关联多个库 wg 对应 原来的origin<br>提交时 git push wg 分支名 | git remote add wg https://github.com/boniu-w/test.git <br> git push wg wg-tianjin |
| git remote -v                                                | 查看项目 关联的所有库                                        |                                                              |
| git checkout .                                               | 1.没add 前 放弃本地 所有修改的代码<br />2. add后             |                                                              |
| git checkout 具体文件名                                      | 更新到工作目录, git reset 文件后, 文件并没有立即更新, 有unstaged change after reset 这个信息,  然后使用这个命令, 把文件更新过来 | git reset 版本号 文件名<br />git checkout 文件名             |
| git reset HEAD .                                             | add 后 , 放弃本地修改                                        |                                                              |
| git log 完整文件名<br>git reset 版本号 完整文件              | 回退单个文件, 根据实际经验, 第二种好用                       | git add .<br />git stash<br />git reset 版本号 文件<br />第二种<br />git checkout 版本号 文件名 |
| git reset --hard 版本号                                      | 回退到指定版本                                               | git reset --hard b863671                                     |
| git commit --amend                                           | 修改最后一次提交的注释,会进入vim编辑器                       |                                                              |
| git rebase -i head~2                                         | 修改之前的已经提交的某次注释, 数字2表示是倒数第几次<br>1. 你想修改哪条注释 就把哪条注释前面的pick换成edit. 方法就是上面说的编辑方式：i---编辑，把pick换成edit---Esc---:wq.<br>2. 然后 git commit --amend<br>3. 修改注释, 保存退出后, git rebase --continue<br>4. 其实这个原理我的理解就是先版本回退到你想修改的某次版本，然后修改当前的commit注释，然后再回到本地最新的版本 |                                                              |
| git log  文件名(具体到文件详细路径)                          | 单个文件的提交历史                                           |                                                              |
| git diff 版本号1 版本号2 文件名                              | 比较两个版本之间的差别                                       |                                                              |
| git revert -n 版本号                                         | 反做某个版本, 比如说想反做版本2, 又不影响版本10, 使用git revert -n  版本2, 然后修改 提交, 生成版本11, 但版本10 是不受影响的, 和 git reset --hard 版本号, 是有区别的 |                                                              |
| git show 分支名                                              | 查看分支的 最新一次提交的完整信息                            |                                                              |
| git push origin --delete 分支名                              | 删除远程分支                                                 |                                                              |
| git fetch                                                    | 将本地分支与远程同步                                         |                                                              |
| git branch -r                                                | 查看远程分支                                                 |                                                              |
| git log --pretty=oneline                                     | 提交历史                                                     |                                                              |
| git config user.name                                         | 查看配置的user.name                                          |                                                              |
| git config user.email                                        | 查看配置的user.email                                         |                                                              |
| git config --global user.name 用户名                         | 全局配置 用户名,  修改时 也用这个命令, 修改当前项目的话 不用加 --global |                                                              |
| git config --global user.email  邮箱名                       | 全局配置邮箱, 修改也用此命令                                 |                                                              |
| git checkout branchName                                      | 切換分支                                                     |                                                              |
| git config --system --list<br />git config --local --list<br />git config --global --list<br />git config --list | 查看配置                                                     |                                                              |
| git merge dev                                                | 融合分支, 先切换到master, 再融合                             |                                                              |
| git remote rm origin                                         | 删除origin                                                   |                                                              |
| git remote set-url origin newGitUrl                          | 直接修改库地址                                               |                                                              |
| git config --global credential.helper store                  | 将用户名和密码长期全局地长期地存储在客户端(实际是客户端所在电脑，并非git的任何目录下，也就是说，即使重装git，改密码也存在) |                                                              |
| git config --global credential.helper cache                  | 设置记住密码（默认15分钟）                                   |                                                              |
| git config credential.helper 'cache --timeout=3600'          | 设置记住密码一个小时之后失效                                 |                                                              |
|                                                              | 在用http形式关联库的时候, 把用户名和密码加上, 这样就不用每次输入密码了 | http://yourname:password@git.oschina.net/name/project.git    |
| git log origin/master -n 3                                   | 查看远程库log                                                |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |

# 各种问题

## 1. git操作出现Unlink of file '......' failed. Should I try again?问题

**解决办法：**

> 解决方案不是简单的选择y或者n,而是关闭IDE，让IDE把这些文件释放掉
>
> 原因是工作目录有某些文件正在被程序使用，这个程序多半是Idea,VS或者eclipse,当然也可能是其他程序



## 2. 误 使用git reset --hard 版本号 之后, 再 git log 发现之后的版本不见了

解决:

- 使用命令, 查看操作日志

> git reflog



```c++
123@DESKTOP-O521OIN MINGW64 /d/ideaprojects/changsha/tientsineye (wg-0811)
$ git reflog
3296c73 (HEAD -> wg-0811) HEAD@{0}: reset: moving to 3296c7373f9eed0952361ce77bfdec0beee20509
57ca8ec HEAD@{1}: reset: moving to HEAD^
920a68e HEAD@{2}: reset: moving to HEAD
920a68e HEAD@{3}: reset: moving to HEAD~3
3296c73 (HEAD -> wg-0811) HEAD@{4}: reset: moving to HEAD
3296c73 (HEAD -> wg-0811) HEAD@{5}: commit: modify: 修改token过期时间为24天, 修改端口号为 13545
090c0eb HEAD@{6}: commit: modify: 版本在单点登录前 ac51aeea8b83a921f3935ee69dab6faf1406fbfc
ac51aee HEAD@{7}: reset: moving to ac51aeea8b83a921f3935ee69dab6faf1406fbfc
335111e HEAD@{8}: reset: moving to 335111e34edaafd283c87b8327ad476a32526033
b53158f (origin/wg-0811) HEAD@{9}: commit: modify: 为了本地化, 修改dev 配置文件, 现在能够正常启动了
67f1260 HEAD@{10}: checkout: moving from master to wg-0811
30fc463 (master) HEAD@{11}: pull origin wg-0811 --allow-unrelated-histories: Merge made by the 'recursive' strategy.
13f4a7e (origin/master, origin/HEAD) HEAD@{12}: clone: from ssh-git.yxkj-tj.com:tcc/tientsineye.git

```



- 使用 git show \<command id> 查看 commit 信息

```c++
123@DESKTOP-O521OIN MINGW64 /d/ideaprojects/changsha/tientsineye (wg-0811)
$ git show 67f1260
commit 67f12604f48252f9e54bed82bc2db8a9f627cdb9
Author: boniu <boniu-w@live.cn>
Date:   Fri Sep 25 17:05:17 2020 +0800

    总体没啥问题了

diff --git a/src/main/java/com/fybdp/tientsineye/controller/LoginController.java b/src/main/java/com/fybdp/tientsineye/controller/LoginController.java
index 682c07a..4136b81 100644
--- a/src/main/java/com/fybdp/tientsineye/controller/LoginController.java
+++ b/src/main/java/com/fybdp/tientsineye/controller/LoginController.java
@@ -97,7 +97,7 @@ public class LoginController {
         }
         if(teuser!=null){
             String realname = teuser.getRealName();
-            String pcname = teuser.getPcNumber();
+            String pcNumber = teuser.getPcNumber();
             String idcard_no = teuser.getIdcard_no();
             String username = teuser.getUserName();
             String depname = teuser.getDeptName();
@@ -110,7 +110,7 @@ public class LoginController {
             authTokenDetails.setPoliceName(idcard_no);
             authTokenDetails.setDeptId(depcode);
             authTokenDetails.setDeptName(depname);
-            authTokenDetails.setOperatorId(userId);
+            authTokenDetails.setOperatorId(pcNumber);

             List<String> aut = new ArrayList<String>();
             aut.add("ADMIN");

123@DESKTOP-O521OIN MINGW64 /d/ideaprojects/changsha/tientsineye (wg-0811)

```



- 再使用git reset --hard <版本号> 到想要的版本位置



## 3. gitee 403

原因: **git 客户端缓存了错误的密码**

先执行:  确认并添加主机SSH到可信列表

```
ssh -T git@gitee.com  
```

再: 

要么 添加ssh公钥后, 使用ssh地址

要么 修改缓存的密码



# gitignore



```swift
/mtk/ 过滤整个文件夹
*.zip 过滤所有.zip文件
/mtk/do.c 过滤某个具体文件
```

```swift
!src/   不过滤该文件夹
!*.zip   不过滤所有.zip文件
!/mtk/do.c 不过滤该文件
```







