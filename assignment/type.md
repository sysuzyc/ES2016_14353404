#Github简单操作

[TOC]

Github是一个比较实用的网站，但是由于其操作起来不像Windows下的图形界面操作那么简单，所以，我们今天就来看下，如何在Github上新建文件夹，并上传资料。

##1、在github上建立一个新的文件


点击Create new file

![](http://p1.bqimg.com/567571/a0f5bcf3276d70df.png)

然后，在图中空白的部分，填写新建的文件夹的名称

![](http://p1.bqimg.com/567571/5dd3df1eb5cb0565.png)

在写完名称之后，可以利用一个“/”来进行区分。

![](http://p1.bqimg.com/567571/122543c1e42a803b.png)

然后，填写一个需要提交的文件

![](http://p1.bqimg.com/567571/f646e4111ace7060.png)
点击Commit new file就可以了

![](http://p1.bqimg.com/567571/53b20d9191da283b.png)

然后，我们就看到多了一个文件夹了：

![](http://p1.bqimg.com/567571/b2e01434e91cea68.png)

##2、从本地传入文件到新建的文件夹中

	git init
	git add ./assignment/readme.md
	git commit -m '你想输入的内容'
	git remote add origin https://github.com/sysuzyc/ES2016_14353404.git
	git push -f origin master

我们可以看到，按照上面的步骤的话，我们是可以完成这次的实验的。
其中，最后一句话，一般都是用-u就可以了，但是Ubuntu16.0.4有时会报错，所以，用-f还是最可靠的了。
出行这个界面就是上传成功：

![](http://i1.piimg.com/567571/da4a5b941cd73567.png)

然后，我们看下自己的Github中的情况为：

![](http://i1.piimg.com/567571/71fc7cf3fbb2d304.png)
所以，我们最终配置成功了。