---
layout: post
title: 将stackGAN改写为SDN
date: 2019-03-11 21:05:24.000000000 +09:00
---


Data/birds/

|

|-test/images.pickle

|-train/images.pickle

> 简述 __init__、__new__、__call__ 方法 :  https://foofish.net/magic-method.html

f1(f2(f3))   执行顺序是f1->f2->f3

遇见@，会开始装饰，装饰成f=f1(f2(f3))   即把f的函数地址换成后续的内容开始执行。


nn.Conv2d()
这个是卷积层，里面常用的参数有四个，in_channels, out_channels, kernel_size, stride, padding

in_channels表示的是输入卷积层的图片厚度
out_channels表示的是要输出的厚度
kernel_size表示的是卷积核的大小，可以用一个数字表示长宽相等的卷积核，比如kernel_size=3，也可以用不同的数字表示长宽不同的卷积核，比如kernel_size=(3, 2) stride表示卷积核滑动的步长

padding表示的是在图片周围填充0的多少，padding=0表示不填充，padding=1四周都填充1维

PyTorch的包autograd提供了自动求导的功能。当使用autograd时，定义的前向网络会生成一个计算图：每个节点是一个Tensor，边表示由输入Tensor到输出Tensor的函数。沿着计算图的反向传播可以很容易地计算出梯度。

在实现的时候，用到了Variable对象。Variable对Tensor对象进行封装，只需要Variable::data即可取出Tensor，并且Variable还封装了该Tensor的梯度Variable::grad(是个Variable对象)。现在用Variable作为计算图的节点，则通过反向传播自动求得的导数就保存在Variable对象中了。

Variable提供了和Tensor一样的API，即能在Tensor上执行的操作也可以在Variable上执行。


output = nn.parallel.data_parallel(new_net, input, device_ids=[0, 1])

nn.Conv2d能够结构一个四维的TensornSamples x nChannels x Height x Width。

# 特别注明：任何可以改变tensor内容的操作都会在方法名后加一个下划线'_'

if optimizer = optim.Optimizer(net.parameters()), model.grad_zero() and optimizer.grad_zero() are the same, they are interchangable.
