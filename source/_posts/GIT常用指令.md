---
title: git常用指令
date: 2019-11-29 10:32:16
categories: GIT
tags: 工具
---
## git使用

***每次推送前切记先拉取 git push 前先执行git pull***


#### 第一步 绑定邮箱和姓名

```
git config --global user.name "xxx"
git config --global user.email "xxxxxxx@xxx.com"
```

#### 第二步 生成公钥

```
ssh-keygen -t rsa -C "your_email@youremail.com" 

cd ~/.ssh
```


#### 第三步

将.ssh目录下的id_rsa.pub放入github或者gitLab setting 下的ssh key中

---

## git指令

```
git clone "ssh地址" 下载项目主分支
```
```
git config --global alias.co "checkout" 设置别名
```
```
git clone "分支名字" -b "ssh地址" 下载项目指定分支
```
```
git checkout -b "分支名字" 新建本地分支
```
```
git checkout "分支名字" 切换到本地分支
```
```
git merge "分支名字" 合并分支
```
## 上传代码到远程仓库
```
git add .  添加所有更改及文件至工作区
```
```
git add "路径"  添加指定文件至工作区
```
```
git commit -m "更新内容"  添加本次提交更改
```
```
git pull  拉取分支最新内容
```
```
git push  推送本次更新到远程分支
```
```
git diff  查看本次更改
```
```
git status  查看工作区状态
```
```
.gitignore规则不生效的解决办法

把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效
，原因是.gitignore只能忽略那些原来没有被追踪的文件，
如果某些文件已经被纳入了版本管理中，
则修改.gitignore是无效的。
那么解决方法就是先把本地缓存删除（改变成未被追踪状态），然后再提交：

git rm -r --cached .
```