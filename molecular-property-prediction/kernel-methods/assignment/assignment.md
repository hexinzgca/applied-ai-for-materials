# 作业：使用精简特征集进行拟合

[Browning 等人](http://pubs.acs.org/doi/10.1021/acs.jpclett.7b00038) 展示了如何通过智能地选择大数据集中的训练点来获得更好的核岭回归模型。  
在本作业中，我们将仅使用 100 个训练点，重建他们的工作，以改进对最高占据分子轨道（HOMO）能量的预测模型。

## 问题 1：拟合库仑矩阵

加载 QM9 数据集，并为每个条目计算 [库仑矩阵](https://singroup.github.io/dscribe/latest/tutorials/coulomb_matrix.html)。将最大原子数设为 40。（QM9 数据集包含最多九个“重”原子（C、O、N、F）的分子。因此原子数最多的分子是壬烷 C<sub>9</sub>H<sub>20</sub>。）

构造一个包含 1000 条目的测试集。

使用 [KernelRidge](https://scikit-learn.org/stable/modules/generated/sklearn.kernel_ridge.KernelRidge.html) 回归与 RBF 核，拟合一个含 100 个参数的模型来预测 HOMO 能量（`'homo'`）。务必使用 [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) 来调优 $\alpha$ 和 $\gamma$ 参数。

*提示*：参数范围取 $10^{-6}$ 到 $10^0$，按对数间隔取 16 步。

重复拟合过程 16 次，每次使用不同的 100 条样本。分别绘制优化后的 $\alpha$、$\gamma$ 参数以及测试集 MAE 的三个 [直方图](https://matplotlib.org/3.3.3/api/_as_gen/matplotlib.pyplot.hist.html)。

- 优化后的模型参数是否随子集变化？
- 超参数（$\alpha$、$\gamma$）的变化幅度有多大？
- 能否对所有 100 条样本的子集使用同一组参数？

## 问题 2：绘制学习曲线

使用随机选取的 10、100 和 1000 条训练集拟合库仑矩阵模型。  
每种训练集大小重复实验 4 次，每次随机选取不同的集合。

- 绘制测试集平均模型精度、训练时间和推理时间随训练集大小的变化曲线。

## 问题 3：优化训练集

我们将使用遗传算法确定一个含 100 条目的优化训练集。

首先从训练集中分离出 1000 条“验证集”，用于评估我们特别挑选的训练集性能。

接下来实现一个函数，该函数接收训练集中点的索引列表，并在验证集上返回该模型得分的 MAE。  
此函数将被遗传算法用于为每组点打分。其签名如下：
