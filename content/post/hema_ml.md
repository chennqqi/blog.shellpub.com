+++
draft = false
author = "admin@shellpub.com"
date = "2017-10-11T21:15:21+08:00"
description = "河马-机器学习算法检测WEBSHELL"
keywords = ["机器学习","WEBSHELL"]
title = "河马-利用机器学习检测WEBSHELL"
topics = ["机器学习"]
tags = ["机器学习","WEBSHELL","machine learning"]
type = "post"
url = "/2017/10/11/河马WEBSHELL机器学习.html"
+++

# [河马-利用机器学习检测WEBSHELL](http://ml.shellpub.com)

## 1. START
近些年机器学习火的一塌糊涂，机器学习、人工智能、深度学习、数据挖掘这些词汇耳熟能详。这些术语的背后是数学、统计学、计算机科学等多门学科的融合。利用这些技术使计算机具有归纳总结等学习能力来服务人类。

## 2. DO
借着这个国庆+中秋双节8天假日，做了一个简单的demo，算是河马安全在机器学习上第一次尝试。

**查杀传送门 [http://ml.shellpub.com](http://ml.shellpub.com)**

界面效果
![](https://s1.ax1x.com/2017/10/11/8MKgI.png)

区分一个文件是否是WEBSHELL是一个典型的[分类](http://blog.csdn.net/chl033/article/details/5204220)过程，属于[监督学习](https://baike.baidu.com/item/%E7%9B%91%E7%9D%A3%E5%AD%A6%E4%B9%A0/9820109?fr=aladdin)

有多种分类算法可选，尝试了K邻近、贝叶斯、决策树、逻辑回归几种方法。在我的实验条件下，使用决策树算法效果比较好。试验中使用4000个黑样本，2000个白样本（来自开源CMS）最终结果如下：

![](https://s1.ax1x.com/2017/10/11/8MAHO.png)
	
	准确率:0.97
	召回率:0.9687

**监督学习训练结果受训练样本集、分类特征值、数学模型等多种因素影响。**

机器学习查杀引擎目前处于试验阶段，结果仅供参考，建议移步[正式版](http://n.shellpub.com)或者下载[客户端](http://www.shellpub.com)

## 3. NEXT TODO

目前白样本的误报还有点高，收集更多的白样本加入到训练集中

改进feature,使之有更好的效果

##

各位请轻拍砖

如有任何建议意见请留言或者直接联系我们，请继续关注

QQ:[1494922137](tencent://message/?uin=1494922137&Site=&Menu=yes)

<mailto:service@shellpub.com>
