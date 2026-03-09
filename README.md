# 材料应用人工智能

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/WardLT/applied-ai-for-materials/HEAD)

本仓库汇集了芝加哥大学“材料科学与工程应用人工智能”课程所使用的 Jupyter 笔记本及其他教学资料。目前仍在持续更新中，未来数月内容与结构可能发生较大变动，敬请期待。

## 如何使用本仓库

每个主题领域均独立成目录，内含笔记本、讲义及 Python 环境配置。各目录通常再细分为若干子文件夹，聚焦特定子主题。

### 通过 Binder 在线运行

您可通过 [Binder](https://jupyter.org/binder) 在线运行所有笔记本。  
只需点击[此链接](https://mybinder.org/v2/gh/WardLT/applied-ai-for-materials/HEAD)即可在云端启动一份仓库副本。  
**注意：Binder 不会保存您的修改**，但您可用其浏览笔记本，或下载到本地完成实践作业。

### 本地安装

您可下载仓库 ZIP 包，也可通过 [git 克隆](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)。  

若使用 git 克隆，可在目录内执行 `git pull` 更新课程资料；  
否则需重新下载仓库以获取更新。

若您使用 Ubuntu Linux，环境安装最为便捷。  
首先安装编译某些包所需的 Fortran 与 C++ 构建工具，具体列表见 [apt.txt](./apt.txt)。  

接着使用 [mamba](https://mamba.readthedocs.io/en/latest/) 创建 Python 环境：
