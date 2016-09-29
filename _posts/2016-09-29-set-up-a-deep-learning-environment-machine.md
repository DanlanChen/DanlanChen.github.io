---
layout: post
title: "Set up deep learning enviroment"
date: 2016-09-28
---
To do deep learning, you need at least one GPU(mostly people use NVIDIA), one library(theano, tensorflow, torch), cuda library, cudnn library.

Setting up the libraries takes times, here are my steps.

I am using linux centos machine

1.install python toolkit
I choose to use ananconda. For me, I followed: https://docs.continuum.io/anaconda/install#linux-install

for me I chose 64 bit linux 2.7 python version.

then add these following to your .bashrc, of course you should change accordingly.

export PATH="/home/danlan/anaconda2/bin:$PATH"

alias python2.7="/home/danlan/anaconda2/bin/python"

alias python2.6="/usr/bin/python"

2. install theano

the official webpage (http://deeplearning.net/software/theano/install_centos6.html#install-centos6) of course you do not need to do much as you already installed ananconda, maybe "sudo pip install theano" works( but when I do pip using keras,I faced problem, not recommed if you installed ananconda).

you can also follow http://www.linjialiang.net/article/view.asp?id=135 to install developer version, I used his or her way.

Do not forget to edit your theano.rc as the two links indicate.

3.install for cuda toolkit

you should follow this:http://docs.nvidia.com/cuda/cuda-installation-guide-linux/#axzz4LdVj7PpG instead of http://www.linjialiang.net/article/view.asp?id=135

you should check your gpu ram using "nvidia-smi"

Normally, you should follow form 1 to 2.6, after getting this https://developer.nvidia.com/cuda-downloads , chose as indicates, there is also install instruction. 

aftert insatllation, you should follow 6.1.1 to do enviroment setting.

4.install cudnn

https://developer.nvidia.com/cudnn

register-download-follow instruction or do the commands below(actually below is simpler than the instruction, as the official instruction asks you to do alias and linking which is complete)

$ tar -zxf cudnn-7.5-linux-x64-v5.0-ga.tgz

$ cd cuda

$ sudo cp lib64/* /usr/local/cuda/lib64/

$ sudo cp include/* /usr/local/cuda/include


5. install keras

It is not successful as I followed the official website installation instruction, because I installed ananconda on my machine, but the system keeps on installing it on my previous python 2.6 lib package, I struggled a lot, by looking at https://www.quora.com/How-do-I-install-Python-packages-in-Anaconda

I did the following things:

conda create -n bunnies python=2.7

source activate bunnies

pip install keras( conda does not work).

But it means you need to activate this environment to use keras in the later time as well. If there is other solutions, please tell me.

Done


But there is also issue I do not solve:

I do not find any right answer on how to set bash as my default shell on centos. 
So I manually change my shell to bash by using exec /bin/bash every time i logged in the machine






