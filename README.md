# Git操作场景

### 新建分支做开发：

#### 首先确保本地没有被修改的文件

```
git checkout master
git checkout -b fa_{branch_name}
edit
git add -A && git commit -m "comment ..."
git push -u presandbox fa{branch_name}
```

#### 别人已经新建分支（我本地没有该分支，需要做后续开发）

#### 首先确保本地没有被修改的文件

```
git checkout master && git pull presandbox
```

#### 查看所有的远端开发分支

```
git branch -r  
git checkout -b fa{branch_name} --trace presandbox/fa{branch_name}
```

#### 根据业务需求，修改相应的文件和代码 。。。

#### 对修改完毕的代码做本地测试，如果没有问题的话，使用下面的代码做本地提交

```
git add -A && git commit-m "commit code for ..."
```

#### 为了可以和其他人共享你的代码修改，请执行以下命令

```
git push presandbox fa{branch_name}
```

#### 注意服务器可能会reject你的代码，如果是被reject的话，参考Merge

#### 别人已经新建分支，我在本地有该分支，我需要做后续开发

```
git checkout fa{branch_name}
git pull presandbox fa{branch_name}
```

#### 根据业务需求组，修改相应的代码和文件 。。。

```
修改完毕的代码做本地测试，如果没有问题的话，使用下面的代码做本地提交
git add -A && git commit-m "commit code for ..."
```

#### 为了可以和其他人共享你的代码修改，请执行以下命令

```
git push presandbox fa{branch_name}
注意服务器可能会reject你的代码，如果是被reject的话，参考Merge
```

#### Merge代码

###### 如果在提交代码是被reject的话，执行下面命令做merge(合并)

```
git pull presandbox fa{branc_name}
请仔细阅读改命令的输出：
	输出会有类似conflict的字样，对每一个标注conflict的文件，仔细阅读其内容，然后把不需要的代码删除，保留最终的代码
```

#### 修改了文件，但是分支不对

###### 例如：在master上修改了文件，在某个分支上修改了文件

```
* 新建临时分支
* git checkout -b temp_new_branch
* 将文件改动保存到新的临时分支下
* git add -A && git commit -m "add all change to new branch"
* 没有新的正确的分支，新建正确的分支
* git checkout master && git checkout -b fa{branch_name}
* 否则 git checkout fa{right_branch}
* 从临时分支获取最新的改动
* git merge temp_new_branch  ## 如果有冲突参考上边的做法
* 保存最新的改动到正确的分支
* git add -A && git commit -m "append all changes back to right branch"
* 删除临时分支
* git branch -D temp_new_branch
```

#### 删除无用的文件夹

```git
git rm -r --cached xxx
```

#### 合并某分支上的某次提交

```git
git cherry-pick commitid
```

#### 获取远程最新更新

```git
git fetch
本地已有修改的话： TODO待验证
	1. git stash
	2. git fetch
	3. git stash pop
```

#### 版本回退

```git
git revert commitid
```

#### 修改commit信息

```git
git commit -amend
1. 已push的
2. 未push的都可以修改
3. 历史提交信息请Google
```

