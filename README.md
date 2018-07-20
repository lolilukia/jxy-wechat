## 小程序说明文档

### 小程序基本信息

名称： 嘉小羽

类型： 工具->预约/报名

 面向用户：同济大学嘉定校区羽毛球协会会员

### 应用场景

同济嘉定羽毛球协会是创办自2009年的优秀体育类社团，社团活动包括羽毛球教学等日常活动和趣味赛、会员挑战赛等特色活动。活动场地位于体育馆，共有5片场地，每学期加入羽毛球协会的同学在150位左右。

为使有意加入羽毛球协会的同学都能够有机会参与活动，协会制定了一个方案，将所有加入社团的同学拉到一个微信群中，然后在活动开始的前一天晚5点在微信群中发送姓名进行报名，社团干事将报名的同学姓名按报名顺序整理成电子表格。由于场地有限，前30名报名的同学可以参与活动，期间如果临时有事不能参加需要在群里@干事进行退报名。另外，干事需要在活动开始之前将电子表格打印下来，核对并让参与活动的同学签名。在活动结束时，干事需要将同学的活动情况整理到本学期的一张大表中，并通知余额不足的同学充值。

由此可见，干事除了筹备特色活动，在日常活动中也需要付出相当多的精力，于是我们联想到可以使用小程序来减轻报名活动干事的工作量。

### 解决的实际问题

- 实现了在加入社团人数远远大于场地数的情况下，每位同学公平地参加活动
- 不必在活动报名期间随时关注并记录群内消息，不必实时整理更新报名情况，小程序将显示最新的报名人数和已报名同学姓名
- 不必将报名情况打印并让同学签名，仅需监督是否有未报名而到场的同学
- 不必在活动结束后整理活动到场情况，直接将数据库数据导出即可
- 不必逐一提醒余额不足的同学充值，小程序会在报名时提醒余额不足的同学充值

### 小程序说明

#### 使用流程

![](https://cl.ly/0y3U2D2j151m/download/series0.jpg)

由于我们将学号作为唯一标识，因此使用之前需要先填写个人资料

![](https://cl.ly/2o2Q010c0O03/download/series1.jpg)

填写完个人资料后，可以看到剩余次数（新加入协会并缴纳会费的同学剩余次数是10次），并且可以看到参与活动的记录和充值记录

![](https://cl.ly/3L2R1p1x1N0y/download/series2.jpg)

如有兴趣可以填写调查问卷，每学期招新的时候将会根据调查问卷生成图表，指导本学期的教学日常活动。活动分为“日常”和“特色”活动，日常活动在每周二和每周四，每周二是教学场，周四是活动场。特色活动一学期有2-3个，特色活动可以带社团之外的同学参加

![](https://cl.ly/1O3U180w1040/download/series3.jpg)

点击日常活动的标题进入活动报名页面，如果尚未报名，可以点击进行报名，报名将会扣除相应次数（教学场是3次，自由活动场是1次），报名成功之后会显示报名的位次，点击报名详情将会看到按报名次序报名的同学姓名

![](https://cl.ly/2X0J2n0d3v3x/download/series4.jpg)

已报名的界面会显示退报名按钮，退报名会返还相应次数。特色活动的详情页包括活动介绍和报名按钮，因为可能会有非协会的同学报名，因此该报名表单与小程序的个人资料不进行绑定，单独提交到数据库的一张表中，此处按照真实情况特色活动都已结束表单未进行显示。最后是充值，点击付款码可以调用微信自带接口保存图片然后进行支付，支付后次数添加功能使用另外一个小程序（同济嘉定羽协充值工具，已发布）

#### 附加说明

- 由于未开放web-view功能，特色活动中详情链接无法跳转至配套公众号文章，暂时使用链接替代
- 由于未开放微信支付功能，而又有该功能需要，因此使用保存付款码的方式进行转账支付

### 技术开发方案

#### 前端

前端使用微信开发者工具开发，所使用的主要组件为tabBar、tabPage、view、icon、text、button、form、input、label、picker、textarea、image等等，使用了发起请求、下载图片、数据缓存、提示等API

#### 后端

后端使用了php的yii2框架，托管在阿里云虚拟主机上

#### 数据库表

#### 活动表activity

![](https://cl.ly/3b0c0l463Z17/download/Image%202018-06-05%20at%2000.53.49.png)

#### 招新资料表enroll

![](https://cl.ly/2e1Y2J223d1F/download/Image%202018-06-05%20at%2000.57.19.png)

#### 会员表member

![](https://cl.ly/2z3l160X0Z3c/download/Image%202018-06-05%20at%2000.58.45.png)

#### 充值表recharge

![](https://cl.ly/3a2j1p3o0N2i/download/Image%202018-06-05%20at%2001.00.54.png)

#### 特色活动报名表special

![](https://cl.ly/2J3G0p2C0o2L/download/Image%202018-06-05%20at%2001.02.30.png)

#### 特色活动信息表feature

![](https://cl.ly/3O1C1I1E2p3K/download/Image%202018-06-05%20at%2001.03.30.png)

#### 调查问卷表survey

![](https://cl.ly/1J3e2B2u0D0n/download/Image%202018-06-05%20at%2001.04.23.png)

### 团队组成与分工

#### 组成

- 队长 同济大学 机械与能源工程学院 范斌
- 队员 同济大学 软件学院 李婧
- 队员 同济大学 电子与信息工程学院 黄键坤

#### 分工

项目主要工作有： UI设计，开发，测试，文档，工作量均平均分配
