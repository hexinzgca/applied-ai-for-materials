# 作业：学习液态铪（Hf）的热力学

本作业基于 [Paulson 等人（2019）](https://linkinghub.elsevier.com/retrieve/pii/S0020722518314721) 的工作，该研究为铪（Hf）的不同相学习了热力学模型。  
本作业的目标是：  
1. 为液态 Hf 的性质建立模型；  
2. 探索示例笔记本中未涉及的参数估计方面：  
   - 在不同模型之间强制执行一致性  
   - 降低模型对异常值的敏感度  
   - 学习数据集权重  

### 安装问题

在 Windows 上，“采样器”只能单进程运行（与[子进程启动方式](https://www.pythonforthelab.com/blog/differences-between-multiprocessing-windows-and-linux/)有关）。  
创建 kombine 的 `Sampler` 类时，请添加选项 `pool=kombine.serialpool.SerialPool()`（例如：`kombine.Sampler(128, 5, ln_posterior_t, pool=kombine.serialpool.SerialPool())`），强制 kombine 单进程运行。

## 准备：加载数据

我们提供 Paulson2019 中的两个数据集供本作业使用。用 Pandas 读入内存：
