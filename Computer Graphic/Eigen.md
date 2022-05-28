# Eigen食用指南

## 1. 开始之前

### 1.1 什么是 Eigen

**Eigen** 是一个高层次的 **C++** 开源库，能有效支持线性代数，矩阵和矢量运算，数值分析及其相关的算法。

> [Eigen官方文档](https://eigen.tuxfamily.org/dox/)（可能需要梯子）

### 1.2 如何安装 Eigen

* 通常的方法是下载 **Eigen** 的源文件编译安装，如果使用 **Linux** 或 **WSL** 可以通过以下指令快捷安装

  ```
  sudo apt install libeigen3
  ```

## 2. Eigen 的模块和头文件

![](https://cdn.jsdelivr.net/gh/Ashechol/markdown.img/Eigen.png)

| 模块        | 头文件                         | 功能                                                         |
| ----------- | ------------------------------ | ------------------------------------------------------------ |
| Core        | `#include <Eigen/Core>`        | 矩阵和数组的类，线性代数运算（包含三角矩阵，自伴算子乘法运算），数组操作。 |
| Geometry    | ` #include <Eigen/Geometry>`   | 变换，平移，缩放，2D旋转和3D旋转（四元组或角轴）。           |
| LU          | ` #include <Eigen/LU>`         | 求逆，行列式，LU分解                                         |
| Cholesky    | `#include <Eigen/Cholesky>`    | LLT和LDLTCholesky分解                                        |
| Householder | `#include <Eigen/Householder>` | 豪斯霍尔德变换（该模块用于其他模块的线性代数计算）           |
| SVD         | `#include <Eigen/SVD>`         | SVD分解                                                      |
| QR          | `#include <Eigen/QR>`          | QR分解                                                       |
| Eigenvalue  | `#include <Eigen/Eigenvalues>` | 特征值，特征向量分解                                         |
| Sparse      | `#include <Eigen/Sparse>`      | 稀疏矩阵的存储和一些基本线性运算                             |
|             | `#include <Eigen/Dense>`       | 包含了Core、Geometry、LU、Cholesky、SVD、QR、Eigenvalues模块 |
|             | `#include <Eigen/Eigen>`       | 包含整个Eigen库                                              |





**参考资料**

[Eigen官方文档](https://eigen.tuxfamily.org/dox/)

[【Eigen】从入门到放弃（一）：Eigen是个什么鬼？](https://zhuanlan.zhihu.com/p/36706885)

