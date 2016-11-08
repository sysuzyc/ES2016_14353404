#在ROS下安装运行cartographer
###14353404 张亚琛
##1、实验过程
###Install wstool and rosdep
	sudo apt-get update
	sudo apt-get install -y python-wstool python-rosdep ninja-build
首先是对于在上一次的实验中安装的工具的初始化。

![](http://p1.bpimg.com/567571/812e34e8c0ca9705.png)

#### Create a new workspace in 'catkin_ws'
	mkdir catkin_ws
	cd catkin_ws
	wstool init src
	wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall
	wstool update -t src
	
![wstool](http://img.blog.csdn.net/20161108211656943)

###Install deb dependencies

	rosdep init
	rosdep update
	rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y

![](http://p1.bpimg.com/567571/36d96534dd73084a.png)

###Build and install

	catkin_make_isolated --install --use-ninja
	source install_isolated/setup.bash
本来按照google的官方网站的做法，是需要翻墙才可以的，不然的话，就会报错。但是如果不想翻墙的话，需要采用以下方法：
####Build and install Ceres.
	git clone https://ceres-solver.googlesource.com/ceres-solver
	cd ceres-solver
	mkdir build
	cd build
	cmake .. -G Ninja
	ninja
	ninja test
	sudo ninja install
这一步得到的是ceres的建立和初始化，通过从导入对应的文件，可以很好的避免翻墙这种方法。结果也是比较正常的。

![这里写图片描述](http://img.blog.csdn.net/20161108211610379)

然后进行下最后一步，可以看到：

![](http://p1.bqimg.com/567571/c760bf5c26f46b0b.png)

####Build and install Cartographer

	git clone https://github.com/hitcm/cartographer.git
	cd cartographer
	mkdir build
	cd build
	cmake .. -G Ninja
	ninja
	ninja test
	sudo ninja install
在自己下载的cartographer文件夹中，执行上述的命令，就可以很好的完成这次的实验了。

![cat](http://img.blog.csdn.net/20161108211844663)

同样的最后的一步执行如下：

![这里写图片描述](http://img.blog.csdn.net/20161108212858555)

上面的命令执行完了之后，我们需要做的就是安装cartographer_ros。

为了安装的方便，我们都并没有下载到catkin_ws文件夹下面，所以，自己下载到任意路径之后，执行以下的操作。
	cd catkin_ws/src
	git clone https://github.com/hitcm/artographer_ros.git
	cd catkin_ws
	catkin_make

![cm1](http://img.blog.csdn.net/20161108211959105)

等这些语句运行完之后，看下catkin_ws的src文件夹下都有哪些内容：

![](http://p1.bqimg.com/567571/4be3e72f858ff82d.png)

如果是上面这些内容的话，那么结果就是正确的了。

###Running the demos
	# Download the 2D backpack example bag.
	wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag
	
	# Launch the 2D backpack demo.
	roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag

如果前面的步骤都是正确的话，这一步是可以正确的完成的。

初次运行如下所示：

![](http://p1.bqimg.com/567571/33dfb3d10f32be03.png)
![cm3](http://img.blog.csdn.net/20161108212312180)

看到结果如下所示：

![这里写图片描述](http://img.blog.csdn.net/20161108211147596)

这个是最开始的界面图。

下面的是运行了半个小时之后的效果图：

![这里写图片描述](http://img.blog.csdn.net/20161108211123078)

所以，结果是正确的。

##2、实验感想
这次的实验其实是比较麻烦的，主要是需要翻墙才可以进行那一步操作，如果不翻墙的话，是不可以的，所以，我们需要找对方法来替代那一步对应的操作。所以，这里是比较麻烦的。然后，虽然过程比较坎坷，但是最终还是做出来了。看到这些图片的时候，还是比较开心的。毕竟自己调了一天了，还是没有调通，最后在师兄的指导下，改正了错误，才终于搞好了。也是不容易啊！最后，还是比较开心自己能够搞出来这个东西啦~
