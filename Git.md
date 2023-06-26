# Git的使用的基本方法

**代码托管平台：gitee**

**终端:Git Bash**

**参考文档：**

[Git](https://git-scm.com/)

[GitHub Git 备忘单 - GitHub Cheatsheets](https://training.github.com/downloads/zh_CN/github-git-cheat-sheet/)

![](C:\Users\Leonx\AppData\Roaming\marktext\images\2023-06-26-13-46-05-image.png)

##### 本地操作

1. **设置用户签名**：
   
   ```powershell
   git config --global user.name [用户名]
   
   git config --global user.email [邮箱]
   
   git config --global -l #展示签名字段
   ```
   
   > ps:
   > 
   > 如果**去掉 --global 参数**只对当前仓库有效。
   > 
   > 签名的作用是**区分不同操作者身份**。
   > 
   > 用户的签名信息在**每一个版本**的提交信息中能够看到，以此确认本次提交是谁做的。
   > 
   > Git 首次安装必须设置一下用户签名，否则无法提交代码。
   > 
   > 这里设置的用户签名**与代码托管中心的账号无关**。

2. **本地仓库初始化**
   
   将当前目录切换到仓库，可以在目标目录下点击 Git Bash Here
   
   <img title="" src="file:///C:/Users/Leonx/AppData/Roaming/marktext/images/2023-06-26-12-49-07-image.png" alt="" width="213" data-align="center">或者采用命令行切换
   
   ![](C:\Users\Leonx\AppData\Roaming\marktext\images\2023-06-26-12-50-36-image.png)
   
   ```powershell
   git init    
   ```
   
   > 运行命令后，将在目标目录下新建.git文件夹，该目录被Git接管

3. **将文件添加暂存区**
   
   ```powershell
   git add [filename1] [filename2]
   # 添加一个或多个文件到暂存区：
   
   git add [dir] 
   # 添加指定目录到暂存区，包括子目录 
   
   git add .
   # 添加当前目录下的所有文件到暂存区
   ```

4. 将文件添加至本地仓库
   
   使用git add命令将文件添加暂存区后，根据需要将这部分文件添加至本地仓库。
   
   ```powershell
   git commit [file1] [file2] -m [message] 
   # 此操作将暂存区的文件添加至本地仓库,如不指定file,则全部提交
   # [message]为此次操作的日志信息
   ```

5. 查看仓库状态
   
   使用 git status 命令![](C:\Users\Leonx\AppData\Roaming\marktext\images\2023-06-26-13-35-59-image.png)
   
   ```powershell
   git status [-s] 
   # 显示变更的文件 展示需要add和commit的文件
   # [-s]只显示文件名
   ```

6. Git标签
   
   ```powershell
   git tag -a [tag_name]
   ```

7. 查看历史提交
   
   ![](C:\Users\Leonx\AppData\Roaming\marktext\images\2023-06-26-13-40-11-image.png)
   
   ![](C:\Users\Leonx\AppData\Roaming\marktext\images\2023-06-26-13-39-47-image.png)
   
   ```powershell
   git log 
   # 详细显示历史提交记录，用于查看版本号
   
   git log --oneline 
   # 简洁显示历史提交记录
   
   git log --graph
   # 以图的形式，展示分支和合并
   
   git blame <file>
   # 展示指定文件的修改记录
   ```

8. 版本回退
   
   用于指定回滚到某一次提交的版本
   
   ```powershell
   git reset [--hard|--mixed|--soft] [HEAD]
   
   [--mixed]
   # 参数撤销工作区中所有未提交的修改内容，
   # 将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交
   
   git reset HEAD^           
   # 回退所有内容到上一个版本  
   git reset HEAD^ hello.php 
   # 回退 hello.php 文件的版本到上一个版本  
   git  reset  052e           
   # 回退到指定版本
   
   [--soft] 
   # 参数用于回退到某个版本
   
   [--hard] 
   # 参数撤销工作区中所有未提交的修改内容
   # 将暂存区与工作区都回到上一次版本
   # 并删除之前的所有信息提交
   ```
   
   ```powershell
   HEAD 使用说明
   
   HEAD # 表示当前版本
   HEAD^ # 上一个版本
   HEAD^^ # 上上一个版本
   HEAD^^^ # 上上上一个版本
   
   HEAD~0 # 表示当前版本
   HEAD~1 # 上一个版本
   HEAD^2 # 上上一个版本
   HEAD^3 # 上上上一个版本
   ```

##### 分支管理

1. 展示分支
   
   `git branch`

2. 新建分支
   
   `git branch [branchName]`
   
   `git branch -b [branchName] `新建并指向

3. 切换分支
   
   `git checkout [branchName]`

4. 删除分支
   
   `git branch -d [branchName]`

5. 合并分支
   
   1. 本地merge
      
      本地master分支可能为旧版本，此后推送时可能报错
   
   2. 远程推送

##### 远程分支

 `git remote add origin https:XXX.XXX.XXX`

`git remote remove origin `删除远程分支

`git fetch `获得最新的远程分支最新的改动

`git pull origin [branchName]`

`git push origin [branchName] [--force]`

强制push，可能会覆盖其他人代码

##### 远程合并（Pull Request）
