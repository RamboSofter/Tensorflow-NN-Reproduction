# Tensorflow的目录结构
- ACKNOWLEDGMENTS  #Tensorflow版权声明 
- ADOPTERS.md    #使用Tensorflow的人员或组织列表
- AUTHORS #Tensorflow作者的官方列表
- BUILD
- CONTRIBUTING.md #Tensorflow贡献指导
- ISSUE_TEMPLATE.md #提ISSUE的模板
- LICENSE #版权许可
- README.md
- RELEASE.md #每次发版的change log
- WORKSPACE #配置移动端开发环境
- bower.BUILD
- configure
- models.BUILD
- tensorflow #主目录，后面分析的重点
- thrid_party #第三方库，包括eigen3（特征运算的库，包括SVD、LU分解等）、gpus（支持cuda）、hadoop、JPEG、llvm、py、sycl
- tools #构建cuda支持
- util

# tensorflow文件夹目录
- BUILD
- __init__.py
- c
- cc #采用C++进行训练的样例
- compiler
- contrib #将常用功能封装在一起的高级API
- core #C++实现的主要目录
- examples #各种示例，本书后续讲的例子主要就在这个目录中
- g3doc #针对C++，Python 版本的代码文档
- go
- java
- opensource_only #声明目录
- python #Python实现的主要目录
- stream_executor #流处理
- tensorboard #App、Web支持，以及脚本支持
- tensorflow.bzl
- tf_exported_symbols.lds
- tf_version_script.lds
- tools #一些工具杂项
- user_ops
- workspace.bzl

## contrib
contrib目录中保存的是将常用的功能封装成的高级API。
网址：https://github.com/tensorflow/models
- framework:很多函数都在这里定义(例如get_variables、get_global_step),还有一些废弃或者不推荐（deprecated）的函数
- layers:这个包主要有initializers.py、layers.py、optimizers.py、regularizers.py、summaries.py等文件。initializers.py中主要是做
变量初始化的函数。layers.py中有关于层操作和权重偏置变量的函数。optimizers.py中包含损失函数和global_step张量的优化器操作。regularizers.py
中包含带有权重的正则化函数。summaries.py中包含将摘要操作添加到tf.GraphKeys.SUMMARIES集合中的函数。
- learn:这个包是使用Tensorflow进行深度学习的高级API，包括完成训练模型和评估模型，读取批处理数据和队列功能的API封装。
- rnn:这个包提供了额外的RNN Cell，也就是对RNN隐藏层的各种改进，如LSTMBlockCell、GPUBlockCell、FusedRNNCell、GridLSTMCell、AttentionCellWrapper等。
- seq2seq:这个包提供了建立神经网络seq2seq层和损失函数的操作
- slim:Tensorflow-Slim(TF-Slim)是一个用于定义、训练和评估Tensorflow中的复杂模型的轻量级库。在使用中可以将TF-Slim与Tensorflow 的原生函数和tf.contrib
中的其他包进行自由组合。https://github.com/tensorflow/models/tree/master/slim

## core
- BUILD
- common_runtime #公共运行库
- debug
- distributed_runtime #分布式执行模块，含有grpc session、grpc worker 、grpc master等
- example
- framework #基础功能模块
- graph
- kernels #一些核心操作在CPU、CUDA内核上的实现
- lib #公共基础库
- ops
- platform #操作系统实现相关文件
- protobuf #.proto 文件，用于传输时的结构序列化
- public #API的头文件目录
- user_ops
- util
Protocol Buffers 是谷歌公司创建的一个数据序列化(serialization)工具，可以用于结构化数据序列化，很适合作为数据存储或者PRC数据交换的格式。
序列化是指将对象的状态信息转换为可以存储或传输的形式的过程。

## examples
examples目录中给出了深度学习的一些例子，包括MNIST、word2vec、Iris、HDF5的一些例子，对入门很有帮助。

## g3doc
tensorflow的文档是用Markdown在维护的，并存放在g3doc中。g3doc目录可以认为是Tensorflow的离线手册，非常好用。
g3doc/api_docs目录中的任何内容都是从代码中的注释生成的，不应该直接编辑。脚本tools/docs/gen_docs.sh是用来生成API文档的。如果无参数调用
，它只重新生成Python API文档（即操作的文档，包括用Python和C++定义的）。如果传递了-a，运行脚本还会重新生成C++API的文档。这个脚本必须从tools/docs目录
调用，如果使用参数-a，需要安装doxygen。网址：http://www.tensorflow.org/community/documentation

## python
第4章中介绍的很多函数的实现都是在python这个目录中。例如激活函数，卷积函数，池化函数，损失函数，优化方法等

## tensorboard
tensorboard目录中是实现Tensorflow 图表可视化工具的代码，代码是基于Tornado来实现网页端可视化。
