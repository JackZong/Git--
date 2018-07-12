# Git 常见问题与解决办法
（方便自己以后遇到同样问题的时候查阅)

### 1. packet_write_wait connection to xx.xx.xx.xx Broken pipe   
### s：
  找到git安装的目录/etc/ssh，打开ssh_config文件
  ```
  sudo vim /etc/ssh/ssh_config 
  ```
  在其中修改（或者添加）
  ```
  Host *
  ServerAliveInterval 120
  ```
### 2. 如何撤销已 commit 的代码？
### s：
```
  git log //查看节点
  git reset commit_id //回退到上一个提交的节点
```
### 3. git 误操作 git reset 强制回滚，恢复 commit 方法
### s:
```
  git reflog //git reflog 会记录所有HEAD的历史
  git reset --hard // 回滚reset
```
### 4. 如何撤销 push
### s:
1. 利用git reset 先在本地回退到自己想要的版本
2. 利用 git push origin <branch> --force 强制更新
```
  git log
  git reset <commit>
  git push origin <branch> --force
```
### 5. 添加远程仓库作为本仓库的上游
### s:  
  ```
  git remote add <alias> <upstream git url> 
  // when you set alias you can fetch the upstream code use alias,just like as flow
  git remote add jackzong <upstream git url>
  git pull jackzong <branch>
  ```
### 6. rebase参数的使用和作用
### s:
  ```
  git pull <alias> <branch> --rebase
  作用：
  使用merge合并
        D--------E  
     /          \
A---B---C---F----G   master, origin/master
  使用rebase
  A---B---C---F---D'---E'   master, origin/master
  ```
