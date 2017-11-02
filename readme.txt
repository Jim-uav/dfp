运行步骤：
前提：系统已经部署好Anaconda和tensorflow
     tmux是一个和terminal类似的命令输入窗口，但tmux可以分屏，且在连接远程服务器时，可以让程序独立运行在服务器，而不受本地客户端关机或者断开连接的影响。

1. 激活tensorflow
   $ source activate tensorflow
   
2. 安装requirements.txt中的包

   $ pip install requirements.txt
   
   可能会报错，尝试如下命令：
   
   $ pip3 install requirements.txt
   
   如果还是报错，出现如下错误信息：
   
    Could not find a version that satisfies the requirement requirements.txt (from versions: )
   
   那么就打开requirements.txt，逐个安装：
   
   $ pip install tensorflow
   $ pip install numpy
   .
   .
   .
   
3. 下载程序，通过terminal命令，导航到程序所在目录
 
4. 通过terminal或者tmux打开jupyter notebook
   点击打开Async-Q.ipynb，菜单栏Cell->Run All，开始运行程序。
   运行可能会报错，出现如下错误信息：
   
   ModuleNotFoundError: No module named 'tensorflow'
   
   可参考链接：https://github.com/conda-forge/tensorflow-feedstock
   退出tensorflow，并退出到根目录，重新安装tensorflow，命令如下：
   
   $ source deactivate tensorflow

   $ conda config --add channels conda-forge

   $ conda install tensorflow

   $ conda search tensorflow --channel conda-forge
   
   然后，重新激活tensorflow:
   
   $ source activate tensorflow
   
   重新进入到程序所在目录，打开jupyter notebook，再次运行程序，运行时间比较长，成功之后，最后一行会显示Saved Model。
   
5. 在通过upyter notebook运行程序时，可以同时打开TensorBoard，观察网络训练情况。
   
   首先，另外打开一个terminal窗口，或者新建一个tmux窗口
   
   然后，导航到程序所在目录：
   
   $ cd /home/yourdir/dfp
   
   最后，设置tensorboard的路径，输入如下命令：
   
   $ tensorboard --logdir=worker_0:'./train_0',...worker_n:'./train_n'
   
   其中的n可以通过查看程序运行情况设置，在运行的程序最末端，会显示worker的个数。
   命令中的worker_0，workder_1...是人为设置的空间名字。

   