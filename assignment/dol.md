#DOL实例分析
姓名：张亚琛     学号：14353404

##example1
   这次的实验是修改代码，使其输出为3次方数。我们可以从以下几个方面着手，完成这次的实验。

首先，我们需要做的是找到example1.xml文件，分析一下这个文件到底是干什么的：

![](http://p1.bqimg.com/567571/72585aa51c33f0c1.png)

我们看到，这里面一共有三个进程，，所以，我们分开来看下到底他们都干了什么：

![](http://p1.bqimg.com/567571/5d239c4d5bf9d952.png)

其中，我们先看下generator函数中的操作，我们看到，他的意思是进行了一次遍历，如果，当前位置小于生产长度，那么我们就输出下标到输出端口，否则，就销毁程序。类似于我们的for循环进行遍历。

![](http://p1.bqimg.com/567571/ea7ec66937bb66fa.png)

我们看到的是，这个部分，是对于数据的操作，一个square就是多了对传入的数据i进行了运算，这里是进行了三次方的运算，所以，一次square就是一个3次方的操作。

![](http://p1.bqimg.com/567571/0d4a494f636c1b8b.png)

这个部分，是我们进行了数据的输出。

所以，总体来说的话，其实generator是相当于传入数据，square是进行数据的运算，consumer是进行数据的输出。

在了解了上面的信息之后，我们就可以进行结果的分析了。

![](http://p1.bqimg.com/567571/f6f4e804f2107059.png)

我们看到输出的结果为上图所示，就是每个consumer是其数据的三次方，所以，我们可以猜测出，example1的dot结构为generator，square和consumer：

![](http://p1.bpimg.com/567571/006d5316eb3170d6.png)

所以，和我们上面的猜测是一致的。

我们还可以看下的是example1.xml中的其他信息：

![](http://p1.bpimg.com/567571/636fc8726eb7771a.png)

其中，这一部分是说明了上面的两条路线上c1和c2的一个基本情况，都是fifo，然后数据为10，所以，一共有20个数据。

而在connection中：

![](http://p1.bpimg.com/567571/8da3ece236ee582b.png)

这一部分是针对于generator和C1的连接的说明

![](http://p1.bpimg.com/567571/28bd80938f7cc89b.png)

这一部分是C2和consumer的连接说明

![](http://p1.bpimg.com/567571/7644f66fd57966fa.png)

这一部分是square和C2的连接说明


![](http://p1.bpimg.com/567571/d5d096e3e5732c92.png)

这一部分是square和C1的连接说明。

所以，我们可以看到，完全符合dot图中的描述。

##example2
    example2和example1其实比较接近，不过example2主要集中体现在xml文件的修改上，使其从3个square变成2个square。

前面的分析中，我们已经知道了generator，square以及consumer的函数的作用了，那么我们就主要从xml中来分析这次的实验:

![](http://p1.bqimg.com/567571/caa9e7c664892176.png)

首先，我们先是在这个地方进行了修改，因为我们需要的是两个square，所以，这里定义为2，就可以了。

![](http://p1.bqimg.com/567571/ffbd0ae58e8c17e5.png)

这个地方是定义了0为input，1为output，所以，在后面的分析中，我们就可以更好的分析了。

我们可以看下connection中的代码：

![](http://p1.bqimg.com/567571/1b2c93bfdd0e334b.png)

这里是说明了从square到square的连接，他们的下表是一样的，也就是说C2_1和square_1是连接在一起，一次类推，直到迭代完毕，其中，C2是output，而square是input。

![](http://p1.bqimg.com/567571/74f67d808b43f660.png)

所以，我们看到这里是对应的square和C2的连接，其中C2的下表会大1，也就是说square_1和C2_2是连接在一起的，迭代到square的结束，其中square是output，C2是input。

剩下的就是我们的generator和consumer的连接问题了：

![](http://p1.bqimg.com/567571/8d405cf4bf7e027a.png)![](http://p1.bqimg.com/567571/098d6574958cd1b2.png)

这样，可以看到的是generator和C2连接的，consumer是和C2_N连接的。

所以，按照我们的分析，结果应该为两个2次方迭代，也就是4次方的数据，所以，我们可以看到为：

![](http://p1.bqimg.com/567571/e1faaf5f7cb2c3d2.png)

所以，我们的结果是正确的，而我们现在看下dol图：

![](http://p1.bqimg.com/567571/2c1051254e5ff4ac.png)

所以，我们的结果是正确的。

##实验感想
   这次的实验，其实还是比较简单的，就只是需要更改一些数据而已，为什么会出现这种结果，dot图又是如何出现的，连接为什么是那个样子的，这些都是我们需要了解的，不然只是改几个数据就做完了实验的话，我们也就失去做实验的意义。所以，我们还是需要在完成实验的基础上理解清楚实验的代码，知道到底怎么做之后，我们才可以很好的完成这次的实验，达到做实验的目的。