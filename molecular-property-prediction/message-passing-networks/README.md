# 消息传递网络

本模块将讲解如何从零开始使用 TensorFlow 构建消息传递神经网络（MPNN）。

这些库中的代码与早期版本的 [nfp](https://github.com/NREL/nfp) 非常接近。
如果你希望进行更前沿的分子深度学习，我建议学习 [nfp](https://github.com/NREL/nfp)、
[megnet](https://github.com/materialsvirtuallab/megnet)、
[schnetpack](https://schnetpack.readthedocs.io/en/stable/) 或 [deepchem](https://deepchem.io/) 等包。
我们在 MPNN 中使用的方法为教学目的而简化，旨在帮助你理解更复杂包中的内部机制。

## 先决条件

在开始“解释 MPNN”笔记本之前，请先阅读 Keras 关于[函数式 API](https://keras.io/getting_started/intro_to_keras_for_engineers/#building-models-with-the-keras-functional-api) 的文档。我们在该笔记本中大量使用 Keras。

## 关键概念

完成这些模块后，你将能够：

- [ ] 将材料训练数据转换为对模型有用的形式
- [ ] 理解数据加载器是什么，以及它们如何提高模型训练效率
- [ ] 构建或修改消息传递神经网络
