# 作业：消息传递神经网络

本作业将带你一步步构建用于预测两种不同分子性质——原子化能和带隙能——的消息传递神经网络（MPNN）模型。我们还将看到网络设计对机器学习模型精度的巨大影响。

*提示*：在 Jupyter 中按 `Shift`+`Tab` 可调出函数的文档。练习过程中你可能需要频繁查阅函数文档，也可访问 [TensorFlow](https://www.tensorflow.org/guide) 官方文档。

## 问题 1：制作数据加载器

第一步是利用本仓库提供的[数据集](../datasets)，为训练、验证和测试数据分别创建数据加载器。

使用 `mpnn` 库中的 `make_loader` 函数，为每个数据集创建 `batch_size=32` 的数据加载器。  
你可以为每个加载器指定不同的输出属性及其他关键设置：

- 创建训练数据加载器时，通常建议启用“shuffle”。为什么？应设置哪个参数？
- 从训练数据中抽取几个批次，输出变量的平均值是多少？

*提示*：用上述 Jupyter 快捷键查看 `mpnn.data.make_data_loader` 的文档，或直接阅读本地 `mpnn` 目录下的源码。

## 问题 2：真正训练一个网络

*步骤 1*：我们需要对[MPNN 示例笔记本](../2_explain-message-passing-networks.ipynb)中的 `make_model` 函数做些修改，以构建能获得显著训练精度的网络：

1. 添加一个参数，用于切换 `Readout` 层使用的读出函数。  
1. 在读出层与输出层之间加入一个包含 32 个单元、激活函数为 'relu' 的 [Dense](https://keras.io/api/layers/core_layers/dense/) 层。  
1. 在当前输出层后添加 `mpnn.layers` 中的“缩放层”（即 `from mpnn.layers import Scaling`），并将缩放层的输出作为模型最终输出。  
   给 Scaling 层命名为 “scaling”（即 `Scaling(name='scaling')`）。

*步骤 2*：构建一个具有 64 维特征、2 个消息传递层、“sum”读出函数的模型。

完成后，`model.summary()` 应输出：
