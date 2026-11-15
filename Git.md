# Git



### 上传本地代码到远程仓库

```cmd
#初始化仓库
git init 

#添加远程仓库
git remote add origin 仓库地址

#添加所有文件夹和文件
git add .

#确认哪些文件将被上传
git status

#提交本地仓库
git commit -m "添加描述信息"

#重命名主分支节点，-M强制命名当前分支
git branch -M main

#上传至远程仓库， -u 设置上游跟踪（之后用git push），origin 远程仓库别名，main推送分支
git push -u origin main
```



### 分支

```cmd
#创建分支并切换
git switch -c 分支名

#切换分支
git branch 分支名

#删除远程分支
git push origin --delete 分支名
```





### 拉取远程仓库代码到本地

1. 核心拉取命令

```cmd
#拉取当前分支代码
git pull 

#拉取指定远程仓库，指定分支
git pull origin main

#拉取代码先不自动提交，之后手动提交
git pull --no-commit
```



2. 获取更新但不合并

```cmd
#获取最新提交，不会自动合并到当前分支，需要手动操作
git fetch

#获取远程仓库所有分支更新
git fetch origin

#获取所有配置的远程仓库拉取更新
git fetch --all
```



### 查看与配置

```cmd
#查看远程仓库origin的详细信息，包括跟踪分支
git remote show origin

#显示所有远程跟踪的分支
git branch -r

#查看本地分支与上游分支的对应关系和提交状态
git branch -vv
```



### 克隆远程仓库

```cmd
git clone 远程仓库地址
```



### 设置代理

```cmd
#查看代理配置
git config --global --get http.proxy
git config --global --get https.proxy

#端口为代理服务器的端口，v2rayn:10809
git config --global http.proxy http://127.0.0.1:10808
git config --global https.proxy http://127.0.0.1:10808

git config --global https.proxy http://127.0.0.1:7897
git config --global http.proxy http://127.0.0.1:7897
```



### 查看git所有配置

```cmd
git config --global --list
```



### 拉取新增内容

```cmd
git fetch origin main

# 3. 合并 main 分支到当前分支
git merge origin/main
```

