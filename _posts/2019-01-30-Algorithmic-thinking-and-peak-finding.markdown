---
layout: post
title: Algorithmic thinking and peak finding
date: 2019-01-30 19:32:24.000000000 +09:00
---

无聊的我决定在寒假写博客来督促自己学习啦！本来想着读完《凸优化》，结果发现下学期有这门课，没办法，那就找点算法设计方面的书学习一下吧。

##开始我的第一篇博文了。

今天找到了MIT的公开课地址，
>https://ocw.mit.edu/courses/

里面有许多不错的课程。我刚刚好在听其中算法设计的课程。一方面巩固一下自己算法设计的能力，另一方面也可以提高一下英语水平，哈哈。

今天讲了peak finding的两种形式——1-D及2-D。1-D提到了两种算法，一种是straight-forward的，即从左到右逐个扫描，复杂度是![](http://chart.googleapis.com/chart?cht=tx&chl= $\theta(n)$)；另一种即广为人知的二分法，复杂度是![](http://chart.googleapis.com/chart?cht=tx&chl= $\theta(log(n))$)
2-D则是
```
#n by m matrix
取第m/2列，找到其中最大的元素(i,j) 
将(i,j)与(i+1,j+1) (i-1,j)比较，如果(i,j)最大，停止。
否则取较大元素所在的那一半的矩阵继续，m=m/2
```
时间复杂度是![](http://chart.googleapis.com/chart?cht=tx&chl= $\theta(nlog(m))$)

----------------------------------------------------------------------------------------
markdown写公式好麻烦啊。评论功能也没有打开，好像是墙的缘故。之后有空会改善这个。
