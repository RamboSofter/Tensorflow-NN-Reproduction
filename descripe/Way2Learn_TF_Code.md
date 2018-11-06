如何高效地学习Tensorflow源代码？
# 学习步骤：
# (1)了解自己要研究的基本领域，如图像分类、物体检测、语音识别等，了解对应这个领域所用的技术，如卷积神经网络（convolutional neural network,cnn）
和循环神经网络RNN，知道实现的基本原理。
# (2)尝试运行GitHub上对应的基本模型(https://github.com/tensorflow/models),其目录结构如下：
- AUTHORS #作者
- CONTRIBUTING.md #贡献指导
- LICENSE #版权许可
- README.md
- WORKSPACE
- autoencoder #自编码器
- compression #图像压缩
- differential_privacy
- im2txt  #图像描述
- inception  #对ImageNet数据集用Inception V3架构去训练和评估
- lm_lb  #语言模型
- namignizer #起名字
- neural_gpu
- neural_programmer
- next_frame_prediction
- resnet   #残差网络
- slim   #图像分类
- street  #路标识别或验证码识别
- swivel  #使用Swivel算法转换词向量
- syntaxnet  #分词和语法分析
- textsum   #文本摘要
- transformer
- tutorials #官方教程
- video_prediction

## slim目录
slim目录中的TF-Slim是图像分类的一个库，它包含用于定义、训练和评估复杂模型的轻量级高级API。可以用于训练和评估的几个广泛使用的CNN图像分类模型
，如lenet，alexnet，vgg,inception_v1,inception_v2,inception_v3,inception_v4,resnet_v1,resnet_v2等，这些模型都位于slim/nets中，具体如下：
- alexnet.py
- alexnet_test.py
- cifarnet.py
- inception.py
- inception_resnet_v2.py
- inception_resnet_v2_test.py
- inception_utils.py
- inception_v1.py
- inception_v1_test.py
- inception_v2.py
- inception_v2_test.py
- inception_v3.py
- inception_v3_test.py
- inception_v4.py
- inception_v4_test.py
- lenet.py
- nets_factory.py
- nets_factory_test.py
- overfeat.py
- overfeat_test.py
- resnet_utils.py
- resnet_v1.py
- resnet_v1_test.py
- resnet_v2.py
- resnet_v2_test.py
- vgg.py
- vgg_test.py

## TF-Slim 
TF-Slim 包含的脚本可以让人从头训练模型或从预先训练的网络开始训练模型并微调，这些脚本位于slim/scripts,具体如下：
- finetune_inception_v1_on_flowers.sh
- finetune_inception_v3_on_flowers.sh
- train_cifarnet_on_cifar10.sh
- train_lenet_on_mnist.sh
TF-Slim还包含用于下载标准图像数据集，将其转换为Tensorflow支持的TFRecords格式，这些脚本位于slim/datasets，具体如下：
- cifar10.py
- dataset_factory.py
- dataset_utils.py
- download_and_convert_cifar10.py
- download_and_convert_flowers.py
- download_and_convert_mnist.py
- flowers.py
- imagenet.py
- mnist.py

# (3)结合要做的项目，找到相关的论文，自己用Tensorflow实现这篇论文的内容，这会让你有一个质的飞跃。
