#DOL开发环境配置
姓名：张亚琛 	 学号：14353404

&emsp;本次实验进行的是在Linux环境下的DOL的配置，由于我使用的windows系统，所以，利用的是虚拟机VMware平台进行的实验，安装的是Ubuntu16.04，在这个平台上进行实验的操作。

为了完成这次的实验，我们需要分几步完成：

	1、安装必要的环境
	2、进行dol文件的解压和安装
	3、编译systemc
	4、编译dol

所以，我们按照步骤进行相关的实验：

###1、安装必要的环境

1）我们需要做的是进行一些适当库的更新。首先需要的是先进行update，看下那些源可以使用：

	sudo apt-get update

<img src="http://p1.bpimg.com/567571/39b668e00d76f3c6.png" width="500" height="300" />

在进行了源的更新之后，我们可以继续进行下面的配置。

2）我们看到这次的实验是利用java进行编译的，那么我们就需要配置一些必要的环境。Ant是我们需要配置的一个环境，它是一个编译java的平台。

	sudo apt-get install ant

<img src="http://p1.bpimg.com/567571/9008613a47ec09a8.png" width="500" height="100" />

看到上面的一些信息，则说明我们的ant是配置成功的。


3）在安装好平台之后，我们的编译语言java的最重要的部分jdk需要安装了，我们用的是jdk7，所以，我们就配置jdk7。由于我用的是Ubuntu16.04的版本，所以，我的jdk是不可以直接进行安装的，需要加入一些适当的库，才可以进行jdk的安装。

	sudo add-apt-repository ppa:openjdk-r/ppa
	sudo apt-get update
	sudo apt-get install openjdk-7-jdk  // OpenJdk 7安装：
这样的话，就可以进行jdk的安装了，但是有的时候，还是不可以进行运行，那么我们需要看的是自己的jdk到底是什么版本的，选择正确的版本即可。

	sudo update-alternatives --config java

<img src="http://i1.piimg.com/567571/66d4573b1679e8fd.png" width="500" height="150" />

这里看到的是，我们选择了jdk7就可以正确运行了，这里是配置好了对应的环境。

4）为了能够解压我们拷贝进来的压缩包，我们也要安装unzip工具：

	sudo apt-get install unzip
<img src="http://i1.piimg.com/567571/7e4a02eab6653d20.png" width="500" height="100" />

这里，我们就可以进行下面的操作了。

###2、进行dol文件的解压和安装
我们将文件中的dol的压缩包拷贝到Ubuntu中，进行解压。

	mkdir dol
	unzip dol_ethz.zip -d dol
敲入上面的命令之后，可以看到下面的图片：

<img src="http://i1.piimg.com/567571/345b61cdc10d5faf.png" width="500" height="350" />

等虚拟机跑完了之后，我们就会发现自己的dol文件解压好了。

###3、编译systemc
我们首先是进行systemc文件的解压，然后再进行编译:

	tar -zxvf systemc-2.3.1.tgz
	cd systemc-2.3.1
	mkdir objdir
	cd objdir
	../configure CXX=g++ --disable-async-updates
	sudo make install

按照上面的步骤，我们就可以对systemc进行编译。

首先是进行解压：

<img src="http://i1.piimg.com/567571/060e9b00da8575d7.png" width="500" height="380" />

然后，进入我们解压后的文件夹，新建一个文件夹，然后进入其中，进行下面的编译操作：

<img src="http://i1.piimg.com/567571/e18a77a5a784454f.png" width="500" height="280" />

等到运行完了之后，我们就可以对比下课件，看下自己跑出来的结果是不是正确的。

<img src="http://i1.piimg.com/567571/03ba998f42fbb198.png" width="500" height="200" />

我们看到最终的结果是正确的，所以，我们就可以看到这次的systemc编译是正确的。

在看到上面的结果之后，我们需要再次检查下看下是不是有什么其他的被遗漏的东西：

<img src="http://p1.bpimg.com/567571/06e4cac89afa95fa.png" width="500" height="70" />

可以看到一共21个文件，没有遗漏的，所以，我们可以说是编译成功了。
###4、编译dol
在前面，我们进行了dol的解压，但是并没有进行编译，所以，这里进行编译：

	cd ../dol
	ant -f build_zip.xml all
	cd build/bin/main
	ant -f runexample.xml -Dnumber=1
首先进入第一步中解压好的文件夹dol，然后，我们去修改对应的xml文件，修改一些路径，改为我们需要的xml文件：

<img src="http://p1.bqimg.com/567571/4c9269d7305c0397.png" width="500" height="70" />

在修改好了之后，我们就可以编译它了。

<img src="http://p1.bqimg.com/567571/b3be289582f1b69b.png" width="500" height="70" />

<img src="http://p1.bqimg.com/567571/8dc814d45c671b08.png" width="500" height="60" />

所以，我们看到，这个时候，buidl_zip.xml是编译成功了，然后，我们可以尝试下运行这次的实验，结果如下所示：

<img src="http://p1.bpimg.com/567571/b20beb7f45c3d1ad.png" width="500" height="380" />

看到上面的结果的话，说明我们这次的实验配置成功了。

:blush: