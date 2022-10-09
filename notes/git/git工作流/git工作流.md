# git工作流

## :rocket: 前言
工作区->本地库->远程库
善用分支

> 参考视频：[十分钟学会正确的github工作流，和开源作者们使用同一套流程](https://www.bilibili.com/video/BV19e4y1q7JJ?share_source=copy_web&vd_source=f5766ae3673b5d92307f29688f11ca21)

<iframe src="//player.bilibili.com/player.html?aid=561005338&bvid=BV19e4y1q7JJ&cid=846391446&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## :scroll: 工作流概述
---

本地正常开发

1.git clone xxx
2.git checkout -b feature 在新建feature分支上进行开发，不影响主分支正常运行
3.修改或者添加本地代码
4.git diff 查看自己对代码做出的改变
5.git add 上传更新后的代码至暂存区
6.git commit 可以将暂存区里更新后的代码更新到本地库
7.git push origin feature 将本地的feature分支上传至远程feature分支

---

在自己的开发期间，远程库主分支出现新的提交时

1.git checkout master 切换回main分支
2.git pull --rebase origin master 将远端修改过的代码再更新到本地，有冲突就解决
3.git checkout feature 回到feature分支
4.git rebase main 我在feature分支上，先把main移过来，然后根据我的commit来修改成新的内容，有冲突就解决冲突
5.git push -f origin feature 把rebase后并且更新过的代码再push到远端github上
6.远程仓库将feature分支的提交squash成一个提交后合并到master分支，然后删除远程feature分支

---

远端完成更新后
1.git branch -d feature 删除本地的feature分支
2.git pull --rebase origin master 再把远端的最新代码拉至本地