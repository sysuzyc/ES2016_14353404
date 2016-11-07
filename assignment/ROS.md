##ROS在Ubuntu下安装
###14353404 张亚琛
在Ubuntu下安装ROS，模拟运行雷达功能。

###实验步骤
本次实验的步骤如下：

	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
	sudo apt-get update
	sudo apt-get install ros-kinetic-desktop-full
	apt-cache search ros-kinetic
	sudo rosdep init
	rosdep update
	echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
	source ~/.bashrc
	source /opt/ros/kinetic/setup.bash
	sudo apt-get install python-rosinstall

其中，每一步都需要安装正确之后，才可以很好的完成这次的实验。
详细的步骤如下所示：

首先是进行一些依赖项的申请和更新：

![](http://7xrn7f.com1.z0.glb.clouddn.com/16-11-7/25149358.jpg)

然后是进行rosedp配置：

![](http://7xrn7f.com1.z0.glb.clouddn.com/16-11-7/62190280.jpg)

![](http://7xrn7f.com1.z0.glb.clouddn.com/16-11-7/79841658.jpg)

然后是进入到bash的目录下，找到对应的文件，并运行之。

![](http://7xrn7f.com1.z0.glb.clouddn.com/16-11-7/68942145.jpg)

所以，在上面的内容跑完之后，我们的ROS就安装并配置完成了。

###实验感想

这次的实验其实不是很难，只是进行了对ros的配置，并没有很实际的用到这些东西。但是，在后面的实验中还是会用到的。在后面进行catagropher的配置中是会利用到ROS工具的。所以，这一次的实验其实只是为了给后面的实验打下基础而已。因此，我们这里必须要保证配置是没有问题的。不然的话，后面的实验室没有办法完成的。这次的配置基本上就是按照文档进行的，也没有碰到什么问题。这里也就不再多说。最后，希望ta可以给些比较有实用性的实验内容。这样的话，同学们也会更加的有耐心去做这些的实验。而不是做完了之后，不知道以后会不会用到，而以敷衍的态度来做这些作业。那样的话是没有任何的价值的。