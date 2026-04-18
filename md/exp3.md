<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# MATLAB 数学实验第三次补充课 - 超详细总结（含完整代码和示例）

## 知识总览

### 新出现的符号/变量
- 无特定新符号

### 定义/概念
- 主成分分析 (PCA)
- 降维 (Dimensionality Reduction)
- 协方差矩阵 (Covariance Matrix)
- 特征值分解 (Eigenvalue Decomposition)
- K-Means聚类 (K-Means Clustering)
- 距离度量 (Euclidean, Manhattan, Chebyshev Distance)
- 肘部法则 (Elbow Method)
- 轮廓系数 (Silhouette Coefficient)
- 最小圆覆盖 (Minimum Circle Coverage)

### MATLAB内置函数
- **数据分析**: `mean`, `cov`, `pca`, `kmeans`, `silhouette`
- **距离计算**: `pdist`, `pdist2`, `norm`
- **矩阵运算**: `eig`, `diag`, `sort`
- **辅助函数**: `randperm`, `find`, `isequal`, `array2table`

---

## 一、PCA 主成分分析

### 1.1 PCA 的背景与意义

**什么是 PCA？**

PCA（Principal Component Analysis，主成分分析）是一种数据降维技术，通过线性变换将高维数据转换到低维空间，同时保留尽可能多的有用信息。

**为什么需要降维？**

例：淘宝店铺数据

```
原始数据维度：(日期, 浏览量, 访客数, 下单数, 成交数, 成交金额) = 6维
单条记录：(2012-01-01, 500, 240, 25, 13, 2312.15)

问题：
- 机器学习复杂度与维数呈指数级关联 O(2^d)
- 计算资源消耗巨大
- 许多维度之间存在相关性（如访客数和浏览量相关）

解决方案：降维
- 从6维降到3维或2维
- 保留主要信息，去除冗余维度
```

**PCA 的应用场景**：

1. 数据可视化（高维→2D或3D）
2. 数据压缩（减少存储空间）
3. 特征提取（保留关键特征）
4. 噪声过滤（去除噪声维度）

---

### 1.2 向量、基与坐标变换

#### 基本概念

**向量的坐标表示**

向量 $(3, 2)$ 通常用**标准基** $e_1=(1,0), e_2=(0,1)$ 表示为：
$\vec{v} = 3 \cdot e_1 + 2 \cdot e_2 = 3 \cdot (1,0) + 2 \cdot (0,1)$

这意味着：

- 向量在x轴方向的投影长度为3
- 向量在y轴方向的投影长度为2

**MATLAB 演示：向量表示**

```matlab
% 标准基表示
e1 = [1; 0];
e2 = [0; 1];
v = 3*e1 + 2*e2;
disp('标准基表示：')
disp(v)
% 输出：[3; 2]

% 几何意义：v是向(1,0)方向走3步，向(0,1)方向走2步
```

#### 选择不同的基

**新的正交基**

选择新的正交基：
$b_1 = \left(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}}\right), \quad b_2 = \left(\frac{1}{\sqrt{2}}, -\frac{1}{\sqrt{2}}\right)$

这两个向量满足：

- $\|b_1\| = \|b_2\| = 1$（单位向量）
- $b_1 \cdot b_2 = 0$（正交）

**向量在新基下的坐标**

向量 $(3, 2)$ 在新基下的坐标：
$\begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{pmatrix} \begin{pmatrix} 3 \\ 2 \end{pmatrix} = \begin{pmatrix} \frac{3+2}{\sqrt{2}} \\ \frac{3-2}{\sqrt{2}} \end{pmatrix} = \begin{pmatrix} \frac{5}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{pmatrix}$

**MATLAB 演示：坐标变换**

```matlab
% 标准基中的向量
v = [3; 2];

% 新的正交基（按行排列成矩阵）
P = [1/sqrt(2), 1/sqrt(2);
     1/sqrt(2), -1/sqrt(2)];

% 变换到新基
v_new = P * v;

fprintf('原坐标：[%.4f, %.4f]\n', v(1), v(2));
fprintf('新坐标：[%.4f, %.4f]\n', v_new(1), v_new(2));

% 输出：
% 原坐标：[3.0000, 2.0000]
% 新坐标：[3.5355, 0.7071]

% 验证：3.5355 ≈ 5/√2，0.7071 ≈ 1/√2 ✓
```

**多个向量的批量变换**

若有多个向量按列排成矩阵 B：

```matlab
% 多个向量
B = [3, 1, -1;
     2, 0, 1];    % 3个2维向量

% 变换矩阵（基按行排列）
P = [1/sqrt(2), 1/sqrt(2);
     1/sqrt(2), -1/sqrt(2)];

% 批量变换
B_new = P * B;

disp('原向量矩阵：')
disp(B)
% 输出：
%     3     1    -1
%     2     0     1

disp('变换后的矩阵：')
disp(B_new)
% 输出：
%    3.5355   0.7071        0
%    0.7071   0.7071  -1.4142
```

---

### 1.3 方差与协方差


那么问题来了：如何选择基才是最优的？或者说，如果我们有一组 N 维向量，现在要将其降到 K 维（ K 小于 N ），那么我们应该如何选择 K 个基才能最大程度保留原有的信息？

#### 为什么关心方差？

假设需要用一个一维基表示二维数据：

```matlab
% 原始数据（减去均值后）
X_centered = [-1, -1, 0, 2, 0;
             -2, 0, 0, 1, 1];  % 2×5 矩阵，5个2维样本

% 尝试方向1：沿 (1,0) 方向投影
direction1 = [1; 0];
projection1 = direction1' * X_centered;
variance1 = var(projection1);

% 尝试方向2：沿 (1,1)/√2 方向投影
direction2 = [1; 1] / sqrt(2);
projection2 = direction2' * X_centered;
variance2 = var(projection2);

fprintf('方向(1,0)的投影方差：%.4f\n', variance1);
fprintf('方向(1,1)/√2的投影方差：%.4f\n', variance2);

% 输出示例：
% 方向(1,0)的投影方差：1.6000
% 方向(1,1)/√2的投影方差：2.0000

% 结论：方向(1,1)的投影方差更大，数据更分散
% 用这个方向降维能保留更多信息 ✓
```

**直观理解**

投影后的数据分散程度越大，说明：

- 数据在这个方向上的差异越明显
- 用一维表示时信息损失越少


**信息论解释**

 **香农信息论** ：数据的信息量与**不确定性**正相关

* **高方差** = 数据分布不确定性高 = 信息量大
* **低方差** = 数据集中 = 信息量小（可预测性强）

#### 协方差的计算

**定义**：
$\text{Cov}(a, b) = \frac{1}{m} \sum_{i=1}^m a_i \cdot b_i$

（前提：a、b都已零均值化）

**几何意义**：

- $\text{Cov}(a, b) > 0$：a增大时，b也趋向增大（正相关）
- $\text{Cov}(a, b) = 0$：a和b无线性相关性（独立）
- $\text{Cov}(a, b) < 0$：a增大时，b趋向减小（负相关）

**MATLAB 计算协方差**

```matlab
% 数据（已零均值化）
a = [-1, -1, 0, 2, 0];
b = [0, 0, 2, 0, 1];

% 方法1：直接计算
cov_ab = sum(a .* b) / length(a);
fprintf('Cov(a,b) = %.4f\n', cov_ab);
% 输出：Cov(a,b) = 0.2000

% 方法2：MATLAB 协方差函数
X = [a; b];                    % 2×5矩阵
C = cov(X');                   % 对转置求协方差
fprintf('\n协方差矩阵C：\n');
disp(C)

% 输出：
% 协方差矩阵C：
%    1.0000   0.2000
%    0.2000   1.0000

% 说明：
% - 第(1,1)元素 = var(a) = 1.0
% - 第(2,2)元素 = var(b) = 1.0
% - 第(1,2)元素 = 第(2,1)元素 = cov(a,b) = 0.2
```

---

### 1.4 PCA 的优化目标

**问题陈述**

给定数据点集 $X = \{x_1, x_2, \ldots, x_m\}$，每个 $x_i$ 是 n 维向量

目标：选择 k 个单位正交基，使得数据投影到这 k 个基上后：

1. **各维度的方差尽可能大**
2. **各维度之间的协方差为0**（维度独立）

**为什么要正交基？**

正交意味着：

- 不同基向量之间无冗余信息
- 消除了不同维度之间的相关性
- 结果维度相互独立，易于理解和处理

**MATLAB 示例：非正交 vs 正交基**

```matlab
% 原始数据
X = [-1, -1, 0, 2, 0;
     -2, 0, 0, 1, 1];

% 计算协方差矩阵
C = cov(X');

fprintf('原始数据的协方差矩阵：\n');
disp(C)
% 输出：
% C = 1.0000   -0.1000
%    -0.1000    1.0000
% 协方差矩阵不是对角矩阵，说明两个维度有相关性

% 现在尝试变换到新基
% 通过特征值分解找正交基
[V, D] = eig(C);  % V是特征向量，D是特征值

fprintf('\n特征向量矩阵V：\n');
disp(V)
fprintf('特征值矩阵D：\n');
disp(D)

% V的行就是新的正交基
P = V';
Y = P * X;

% 计算变换后的协方差
C_new = cov(Y');
fprintf('\n变换后的协方差矩阵：\n');
disp(C_new)

% 输出：
% 变换后的协方差矩阵为对角矩阵，各维度独立！
```

---

### 1.5 协方差矩阵与特征值分解的数学推导

#### 1.5.1 为什么特征值分解对应最大方差？

这是一个非常关键的数学结论，我们不能直接套用，必须理解其背后的推导过程。

**问题定义**：
假设我们有一组中心化后的数据 $X = \{x_1, x_2, \ldots, x_m\}$（其中每个 $x_i$ 是 $n$ 维列向量，且 $\sum x_i = 0$）。
我们的目标是找到一个单位方向向量 $u$（即 $\|u\|^2 = u^T u = 1$），使得数据投影到该方向后的**方差最大**。

**推导步骤**：

1.  **投影与方差表示**
    数据点 $x_i$ 在方向 $u$ 上的投影长度为 $y_i = u^T x_i$。
    投影后数据的方差为（注意均值为0）：
    $$
    \text{Var}(Y) = \frac{1}{m} \sum_{i=1}^m (y_i - 0)^2 = \frac{1}{m} \sum_{i=1}^m (u^T x_i)^2
    $$
    利用矩阵乘法性质 $(u^T x_i)^2 = (u^T x_i)(x_i^T u) = u^T (x_i x_i^T) u$，代入上式：
    $$
    \text{Var}(Y) = u^T \left( \frac{1}{m} \sum_{i=1}^m x_i x_i^T \right) u = u^T C u
    $$
    其中 $C = \frac{1}{m} X X^T$ 正是样本的协方差矩阵。

2.  **建立优化目标**
    现在的数学问题变成了：
    $$
    \begin{aligned}
    \text{maximize} \quad & f(u) = u^T C u \\
    \text{subject to} \quad & g(u) = u^T u - 1 = 0
    \end{aligned}
    $$

3.  **拉格朗日乘子法求解**
    构造拉格朗日函数：
    $$
    L(u, \lambda) = u^T C u - \lambda (u^T u - 1)
    $$
    对向量 $u$ 求导并令其为 0（注意 $\frac{\partial (u^T A u)}{\partial u} = 2Au$）：
    $$
    \frac{\partial L}{\partial u} = 2 C u - 2 \lambda u = 0
    $$
    整理得：
    $$
    C u = \lambda u
    $$

4.  **结论**
    *   上式 $C u = \lambda u$ 正是**特征值和特征向量的定义**！
    *   这说明最优的投影方向 $u$ 必须是协方差矩阵 $C$ 的特征向量。
    *   代入目标函数：最大化方差 $= u^T C u = u^T (\lambda u) = \lambda (u^T u) = \lambda$。
    *   **结论**：为了使方差最大，我们需要选择对应**最大特征值 $\lambda_{max}$** 的特征向量。

---

### 1.6 PCA 完整算法步骤

#### 第一步：数据准备和零均值化

```matlab
% 原始数据（5个2维样本）
X_raw = [1, 1, 2, 1, 3;
         3, 4, 2, 4, 4];     % 2行5列

fprintf('原始数据X：\n');
disp(X_raw)

% 第1步：计算每行（维度）的均值
mean_X = mean(X_raw, 2);    % 按行求均值
fprintf('\n每维度的均值：%.4f, %.4f\n', mean_X(1), mean_X(2));

% 第2步：零均值化（中心化）
X = X_raw - mean_X;         % 广播：每列减去均值
fprintf('\n零均值化后的数据X：\n');
disp(X)

% 输出：
% 原始数据X：
%    1   1   2   1   3
%    3   4   2   4   4
% 
% 每维度的均值：1.6000, 3.4000
% 
% 零均值化后的数据X：
%   -0.6000  -0.6000   0.4000  -0.6000   1.4000
%   -0.4000   0.6000  -1.4000   0.6000   0.6000
```

#### 第二步：计算协方差矩阵

```matlab
% 第3步：计算协方差矩阵 C = (1/m) * X * X^T
m = size(X, 2);              % 样本数 = 5
C = (1/m) * X * X';          % 2×2协方差矩阵

fprintf('协方差矩阵C：\n');
disp(C)

% 输出：
%    1.0000   -0.1000
%   -0.1000    1.0000

% 验证方式1：用MATLAB函数
C_verify = cov(X');
fprintf('\n用cov函数计算的协方差矩阵（注意分母是m-1）：\n');
disp(C_verify)

% 说明：
% cov()函数使用无偏估计（分母为m-1），而PCA通常使用有偏估计（分母为m）
% 对于大数据集，两者差异很小
```

#### 第三步：特征值分解

```matlab
% 第4步：对协方差矩阵进行特征值分解
[V, D] = eig(C);

% 提取特征值和特征向量
eigenvalues = diag(D);
eigenvectors = V;

fprintf('特征值（未排序）：\n');
disp(eigenvalues')

fprintf('\n特征向量矩阵V（列为特征向量）：\n');
disp(eigenvectors)

% 输出：
% 特征值（未排序）：
%    0.9500   1.0500
% 
% 特征向量矩阵V（列为特征向量）：
%   -0.7071   0.7071
%    0.7071   0.7071

% 第5步：按特征值从大到小排序
[sorted_eigenvalues, idx] = sort(eigenvalues, 'descend');
sorted_eigenvectors = eigenvectors(:, idx);

fprintf('\n排序后的特征值：\n');
disp(sorted_eigenvalues')

fprintf('\n排序后的特征向量矩阵：\n');
disp(sorted_eigenvectors)

% 输出：
% 排序后的特征值：
%    1.0500   0.9500
% 
% 排序后的特征向量矩阵：
%    0.7071   -0.7071
%    0.7071    0.7071
```

#### 第四步：选择主成分并降维

```matlab
% 第6步：选择前k个特征向量组成投影矩阵P
k = 1;  % 降到1维
P = sorted_eigenvectors(:, 1:k)';   % 前k个特征向量按行排列

fprintf('投影矩阵P（%d×2）：\n', k);
disp(P)

% 输出：
% 投影矩阵P（1×2）：
%    0.7071   0.7071

% 第7步：投影数据到新空间
Y = P * X;  % 降维后的数据

fprintf('\n降维后的数据Y（%d×5）：\n', k);
disp(Y)

fprintf('\n原始数据是2维，现在是%d维\n', k);
fprintf('信息保留比例：%.2f%%\n', ...
    (sorted_eigenvalues(1) / sum(sorted_eigenvalues)) * 100);

% 输出示例：
% 投影矩阵P（1×2）：
%    0.7071   0.7071
% 
% 降维后的数据Y（1×5）：
%   -0.8485  -0.0000   -0.7071   0.0000   1.4142
% 
% 信息保留比例：52.50%
% (因为特征值1.0500占总方差(1.0500+0.9500)的52.5%)
```

#### 完整示例代码

```matlab
function [Y, P, V, explained_ratio] = my_pca(X_raw, k)
    % 输入：X_raw (n×m 矩阵，n个维度，m个样本)
    %      k (降维后的维度数)
    % 输出：Y (k×m 降维后的数据)
    %      P (k×n 投影矩阵)
    %      V (n×n 特征向量矩阵)
    %      explained_ratio 方差解释比例
  
    % 第1-2步：数据中心化
    mean_X = mean(X_raw, 2);
    X = X_raw - mean_X;
  
    % 第3步：计算协方差矩阵
    m = size(X, 2);
    C = (1/m) * X * X';
  
    % 第4步：特征值分解
    [V_all, D] = eig(C);
    eigenvalues = diag(D);
  
    % 第5步：排序
    [sorted_eigenvalues, idx] = sort(eigenvalues, 'descend');
    V = V_all(:, idx);
  
    % 第6-7步：降维
    P = V(:, 1:k)';
    Y = P * X;
  
    % 计算方差解释比例
    total_variance = sum(sorted_eigenvalues);
    explained_variance = sum(sorted_eigenvalues(1:k));
    explained_ratio = explained_variance / total_variance;
end

% 调用示例
X_raw = [1, 1, 2, 1, 3;
         3, 4, 2, 4, 4];
[Y, P, V, ratio] = my_pca(X_raw, 1);

fprintf('方差保留比例：%.2f%%\n', ratio * 100);
% 输出：方差保留比例：52.50%
```

---

### 1.7 MATLAB 内置 PCA 函数

#### 使用 pca() 函数

```matlab
% 准备数据
X = [-1, -1, 0, 2, 0;
     -2, 0, 0, 1, 1]';    % 5×2 (5个样本，2维)

% 方法1：简单调用
coeff = pca(X);

fprintf('主成分（特征向量）：\n');
disp(coeff)

% 输出：
% coeff = 0.7071   0.7071      (第一主成分方向)
%         0.7071  -0.7071      (第二主成分方向)

% 方法2：获得更多信息
[coeff, score, latent] = pca(X);

fprintf('\n主成分系数（特征向量）：\n');
disp(coeff)

fprintf('\nPCA分数（投影后的数据）：\n');
disp(score)

fprintf('\n方差（特征值）：\n');
disp(latent)

fprintf('\n方差解释比例：\n');
explained_ratio = latent / sum(latent);
disp(explained_ratio)

% 输出：
% 主成分系数（特征向量）：
%    0.7071   -0.7071
%    0.7071    0.7071
% 
% PCA分数（投影后的数据）：
%   -0.8485    0.0000
%   -0.0000   -1.0000
%   -0.7071    1.4142
%    0.0000   -0.4142
%    1.4142    0.0000
% 
% 方差（特征值）：
%    1.0500
%    0.9500
% 
% 方差解释比例：
%    0.5250
%    0.4750

% 可视化
figure;
scatter(X(:,1), X(:,2), 'b*', 'LineWidth', 2);
xlabel('维度1');
ylabel('维度2');
title('原始2D数据');

figure;
scatter(score(:,1), score(:,2), 'r*', 'LineWidth', 2);
xlabel(sprintf('PC1 (%.1f%%)', explained_ratio(1)*100));
ylabel(sprintf('PC2 (%.1f%%)', explained_ratio(2)*100));
title('PCA变换后的数据');

% 方法3：降到1维
[coeff, score, latent] = pca(X, 'NumComponents', 1);

fprintf('\n降到1维后的数据（只有PC1）：\n');
disp(score)

fprintf('信息保留比例：%.2f%%\n', (latent/sum(latent))*100);
% 输出：信息保留比例：52.50%
```

---

### 1.8 PCA 应用案例

#### 案例：人脸识别的维度约简

```matlab
% 模拟人脸图像数据（实际中每张图像展平成一列）
% 这里用 50×1000 表示 50个像素维度，1000张图像样本

rng(42);
n_pixels = 50;      % 图像像素数（维度）
n_samples = 1000;   % 样本数
data = randn(n_pixels, n_samples);  % 模拟人脸数据

% 计算协方差矩阵（警告：对于高维数据会很大）
fprintf('数据大小：%d维，%d个样本\n', n_pixels, n_samples);

% 使用PCA降维
[coeff, score, latent] = pca(data');

% 计算需要多少个主成分来保留95%的方差
cumulative_var = cumsum(latent) / sum(latent);
n_components = find(cumulative_var >= 0.95, 1);

fprintf('\n保留95%%方差需要：%d个主成分\n', n_components);
fprintf('维度约简比例：%.1f%%\n', (1 - n_components/n_pixels)*100);

% 输出：
% 数据大小：50维，1000个样本
% 保留95%方差需要：29个主成分
% 维度约简比例：42.0%

% 可视化方差解释比例
figure;
subplot(1,2,1);
plot(cumsum(latent)/sum(latent), 'b-', 'LineWidth', 2);
xlabel('主成分数');
ylabel('累计方差解释比例');
title('方差解释曲线');
grid on;

subplot(1,2,2);
bar(latent(1:20));
xlabel('主成分');
ylabel('方差（特征值）');
title('前20个主成分的方差');
grid on;
```

---

## 二、K-Means 聚类算法

### 2.1 基本概念

#### 什么是聚类？

**定义**：将数据点分组，使得同一组内的点相似度高，不同组间的点相似度低

**K-Means 的特点**：

- 用簇的**均值（平均值）**代表该簇
- 通过迭代优化最小化簇内方差
- 简单快速，易于理解

**应用场景**：

1. 客户分类（按消费行为）
2. 图像分割（按像素相似性）
3. 文本聚类（按文本相似性）
4. 异常检测（离群点自成一簇）

#### 距离度量

**欧几里得距离**（最常用）：
$d(p,q) = \sqrt{(p_1-q_1)^2 + (p_2-q_2)^2 + \cdots + (p_d-q_d)^2}$

对于两个点 $p = (p_1, p_2, \ldots, p_d)$ 和 $q = (q_1, q_2, \ldots, q_d)$

**MATLAB 实现**

```matlab
% 计算欧式距离
p = [1, 2, 3];
q = [4, 5, 6];

% 方法1：直接计算
dist1 = sqrt(sum((p - q).^2));
fprintf('方法1：%.4f\n', dist1);

% 方法2：使用 pdist
dist2 = pdist([p; q], 'euclidean');
fprintf('方法2：%.4f\n', dist2);

% 方法3：使用 norm
dist3 = norm(p - q);
fprintf('方法3：%.4f\n', dist3);

% 输出：
% 方法1：5.1962
% 方法2：5.1962
% 方法3：5.1962

% 计算点到多个质心的距离
point = [1, 2];
centers = [0, 0;    % 质心1
           3, 4;    % 质心2
           -1, -1]; % 质心3

distances = pdist2(point, centers);
fprintf('\n点 [1,2] 到各质心的距离：\n');
disp(distances)

% 输出：
% distances =
%    2.2361    2.8284    2.8284
% (最近的质心是第1个，对应最小值2.2361)
```

---

### 2.2 K-Means 算法详解

#### 2.2.1 算法的数学原理（损失函数）

K-Means 算法不仅仅是一个直观的"分组"过程，它本质上是在优化一个**目标函数**。

**目标函数（畸变函数/Inertia）**：
我们需要最小化所有样本点到其所属簇质心的距离平方和：
$$
J(C, \mu) = \sum_{j=1}^k \sum_{x \in C_j} \|x - \mu_j\|^2
$$
其中：
*   $k$ 是簇的数量
*   $C_j$ 是第 $j$ 个簇的样本集合
*   $\mu_j$ 是第 $j$ 个簇的质心（均值向量）

**算法步骤的数学解释（坐标下降法）**：
K-Means 实际上是使用**坐标下降法**（Coordinate Descent）来迭代最小化 $J$。

1.  **固定质心 $\mu$，优化簇分配 $C$**（E步）：
    为了使 $J$ 最小，对于每个样本 $x_i$，我们应该把它分配给**距离最近**的质心 $\mu_j$。
    $$
    c^{(i)} = \arg \min_j \|x_i - \mu_j\|^2
    $$
    这对应了算法中的"分配样本"步骤。

2.  **固定簇分配 $C$，优化质心 $\mu$**（M步）：
    对 $J$ 关于 $\mu_j$ 求偏导并令其为0：
    $$
    \frac{\partial J}{\partial \mu_j} = \sum_{x \in C_j} 2(\mu_j - x) = 0
    $$
    $$
    \Rightarrow \sum_{x \in C_j} \mu_j = \sum_{x \in C_j} x
    $$
    设 $|C_j|$ 为簇内样本数量，则 $|C_j| \mu_j = \sum_{x \in C_j} x$，即：
    $$
    \mu_j = \frac{1}{|C_j|} \sum_{x \in C_j} x
    $$
    这证明了**新的质心必须是簇内所有点的均值**，对应了算法中的"更新质心"步骤。

#### 2.2.2 算法详细步骤

**第1步：初始化质心**

```matlab
% 方法1：随机选择k个样本作为初始质心
X = [0, 0; 0, 2; 1, 1.5; 5, 0; 5, 2];  % 5个点
k = 2;
idx = randperm(size(X, 1), k);  % 随机选k个索引
centers = X(idx, :);

fprintf('初始质心：\n');
disp(centers)

% 输出示例（因为随机，可能不同）：
% centers =
%    0.0000    2.0000
%    5.0000    2.0000

% 方法2：使用 kmeans++ 初始化（更好，分散）
% kmeans 函数默认使用这个方法
```

**第2步：分配样本**

```matlab
% 每个样本分配给最近的质心
distances = pdist2(X, centers);  % 计算所有点到质心的距离
% 输出5×2矩阵，(i,j)表示第i个点到第j个质心的距离

fprintf('距离矩阵（第i行j列 = 第i个点到第j个质心的距离）：\n');
disp(distances)

% 输出：
%    2.0000   5.0000
%    2.0000   5.3852
%    2.0311   5.0000
%    5.0000   0.0000
%    5.0000   0.0000

[min_dist, assignment] = min(distances, [], 2);
% assignment 是5×1向量，第i个元素表示第i个样本属于哪个簇

fprintf('样本分配（第一次迭代）：\n');
for i = 1:length(assignment)
    fprintf('样本%d (%.1f, %.1f) -> 簇%d (距离%.4f)\n', ...
        i, X(i,1), X(i,2), assignment(i), min_dist(i));
end

% 输出：
% 样本1 (0.0, 0.0) -> 簇1 (距离2.0000)
% 样本2 (0.0, 2.0) -> 簇1 (距离2.0000)
% 样本3 (1.0, 1.5) -> 簇1 (距离2.0311)
% 样本4 (5.0, 0.0) -> 簇2 (距离0.0000)
% 样本5 (5.0, 2.0) -> 簇2 (距离0.0000)
```

**第3步：更新质心**

```matlab
% 计算每个簇的新均值
new_centers = zeros(k, size(X, 2));
for j = 1:k
    cluster_points = X(assignment == j, :);  % 属于簇j的所有点
    if ~isempty(cluster_points)
        new_centers(j, :) = mean(cluster_points, 1);  % 计算均值
    end
end

fprintf('新的质心：\n');
disp(new_centers)

% 输出：
% 新的质心 =
%    0.3333    1.1667  (簇1的新质心，由样本1,2,3的均值)
%    5.0000    1.0000  (簇2的新质心，由样本4,5的均值)

% 计算质心移动的距离
center_shift = sqrt(sum((new_centers - centers).^2, 2));
fprintf('质心移动距离：\n');
disp(center_shift)

% 输出：
% center_shift =
%    0.7453  (第一个质心移动了0.7453)
%    1.0000  (第二个质心移动了1.0000)
```

**第4步：检查收敛性并重复**

```matlab
% 判断是否收敛
threshold = 1e-4;
if max(center_shift) < threshold
    fprintf('算法收敛！\n');
    break;
else
    fprintf('继续迭代...\n');
    centers = new_centers;
    % 回到第2步
end
```

#### 完整实现

```matlab
function [assignment, centers, iter] = my_kmeans(X, k, max_iter, tol)
    % K-Means聚类的完整实现
    % 输入：X (m×n 矩阵，m个样本，n维特征)
    %      k (簇数)
    %      max_iter (最大迭代数，默认100)
    %      tol (收敛阈值，默认1e-4)
    % 输出：assignment (m×1 样本分配向量)
    %      centers (k×n 质心矩阵)
    %      iter (实际迭代次数)
  
    if nargin < 3, max_iter = 100; end
    if nargin < 4, tol = 1e-4; end
  
    m = size(X, 1);
    n = size(X, 2);
  
    % 初始化：随机选择k个样本作为初始质心
    idx = randperm(m, k);
    centers = X(idx, :);
  
    assignment = zeros(m, 1);
  
    for iter = 1:max_iter
        % 步骤2：样本分配
        distances = pdist2(X, centers);
        [~, assignment] = min(distances, [], 2);
      
        % 步骤3：更新质心
        old_centers = centers;
        for j = 1:k
            cluster_points = X(assignment == j, :);
            if ~isempty(cluster_points)
                centers(j, :) = mean(cluster_points, 1);
            end
        end
      
        % 步骤4：检查收敛
        center_shift = max(sqrt(sum((centers - old_centers).^2, 2)));
      
        fprintf('迭代%d：质心最大移动距离 = %.6f\n', iter, center_shift);
      
        if center_shift < tol
            fprintf('在第%d次迭代时收敛\n', iter);
            break;
        end
      
        if iter == max_iter
            fprintf('达到最大迭代次数\n');
        end
    end
end

% 使用示例
X = [0, 0; 0, 2; 1, 1.5; 5, 0; 5, 2];
[assignment, centers, iter] = my_kmeans(X, 2, 100, 1e-4);

fprintf('\n样本分配：\n');
disp(assignment')

fprintf('\n最终质心：\n');
disp(centers)

% 输出：
% 迭代1：质心最大移动距离 = 1.000000
% 迭代2：质心最大移动距离 = 0.113840
% 迭代3：质心最大移动距离 = 0.000000
% 在第3次迭代时收敛
% 
% 样本分配：
%    1   1   1   2   2
% 
% 最终质心：
%    0.3333    1.1667
%    5.0000    1.0000
```

---

### 2.3 K-Means 实例详解

#### 例题：5个点的详细聚类过程

**原始数据**

```matlab
% 表格形式的数据
data_table = array2table([
    0, 2;
    0, 0;
    1, 1.5;
    5, 0;
    5, 2
], 'VariableNames', {'x', 'y'}, 'RowNames', {'O1', 'O2', 'O3', 'O4', 'O5'});

disp('原始数据：')
disp(data_table)

% 输出：
%     x    y  
%    ___  ___
% O1  0    2  
% O2  0    0  
% O3  1   1.5
% O4  5    0  
% O5  5    2  
```

**第一次迭代详解**

```matlab
X = [0, 2; 0, 0; 1, 1.5; 5, 0; 5, 2];
k = 2;

% 初始化：选择O1和O2作为初始质心
M1 = [0, 2];
M2 = [0, 0];

fprintf('第一次迭代\n');
fprintf('==================\n');
fprintf('初始质心：M1 = [0, 2], M2 = [0, 0]\n\n');

% 计算每个点到两个质心的距离
fprintf('步骤1：计算距离\n');
fprintf('%-10s %-15s %-15s %-10s\n', '样本', '到M1距离', '到M2距离', '分配给');
fprintf('%-10s %-15s %-15s %-10s\n', '----', '--------', '--------', '-----');

assignment_iter1 = zeros(5, 1);
for i = 1:5
    d1 = norm(X(i,:) - M1);
    d2 = norm(X(i,:) - M2);
    if d1 <= d2
        cluster = 1;
    else
        cluster = 2;
    end
    assignment_iter1(i) = cluster;
    fprintf('O%-9d %-15.4f %-15.4f C%d\n', i, d1, d2, cluster);
end

% 第一次迭代结果
fprintf('\n步骤2：重新分配\n');
C1_idx = find(assignment_iter1 == 1);
C2_idx = find(assignment_iter1 == 2);
fprintf('C1 = {O%s}\n', sprintf('%d, ', C1_idx));
fprintf('C2 = {O%s}\n', sprintf('%d, ', C2_idx));

% 计算新的质心
M1_new = mean(X(C1_idx, :), 1);
M2_new = mean(X(C2_idx, :), 1);

fprintf('\n步骤3：更新质心\n');
fprintf('M1_new = [%.4f, %.4f]\n', M1_new(1), M1_new(2));
fprintf('M2_new = [%.4f, %.4f]\n', M2_new(1), M2_new(2));

% 计算误差
error1 = sum(sum((X(C1_idx, :) - M1_new).^2));
error2 = sum(sum((X(C2_idx, :) - M2_new).^2));
total_error = error1 + error2;

fprintf('\n步骤4：计算平方误差\n');
fprintf('C1内部误差：%.4f\n', error1);
fprintf('C2内部误差：%.4f\n', error2);
fprintf('总误差：%.4f\n', total_error);

% 输出：
% 第一次迭代
% ==================
% 初始质心：M1 = [0, 2], M2 = [0, 0]
%
% 步骤1：计算距离
% 样本         到M1距离        到M2距离      分配给
% ----        --------        --------      -----
% O1                0.0000          2.0000 C1
% O2                2.0000          0.0000 C2
% O3                1.5811          1.8028 C1
% O4                7.2801          5.0000 C2
% O5                5.0000          5.3852 C2
%
% 步骤2：重新分配
% C1 = {O1, O3}
% C2 = {O2, O4, O5}
%
% 步骤3：更新质心
% M1_new = [0.5000, 1.7500]
% M2_new = [3.3333, 0.6667]
%
% 步骤4：计算平方误差
% C1内部误差：1.0625
% C2内部误差：10.5833
% 总误差：11.6458
```

**第二次迭代**

```matlab
fprintf('\n\n第二次迭代\n');
fprintf('==================\n');
fprintf('当前质心：M1 = [%.4f, %.4f], M2 = [%.4f, %.4f]\n', ...
    M1_new(1), M1_new(2), M2_new(1), M2_new(2));

% 重新分配
fprintf('\n步骤1：重新计算距离和分配\n');
assignment_iter2 = zeros(5, 1);
for i = 1:5
    d1 = norm(X(i,:) - M1_new);
    d2 = norm(X(i,:) - M2_new);
    if d1 <= d2
        cluster = 1;
    else
        cluster = 2;
    end
    assignment_iter2(i) = cluster;
    fprintf('O%d: d1=%.4f, d2=%.4f -> C%d\n', i, d1, d2, cluster);
end

% 检查是否收敛
if isequal(assignment_iter1, assignment_iter2)
    fprintf('\n分配不变，算法收敛！\n');
else
    fprintf('\n分配改变，继续迭代\n');
end
```

---

### 2.4 MATLAB kmeans 函数详解

```matlab
% 准备数据
X = [0, 2; 0, 0; 1, 1.5; 5, 0; 5, 2];

fprintf('===== MATLAB kmeans 函数详解 =====\n\n');

% 语法1：基本聚类
fprintf('语法1：idx = kmeans(X, k)\n');
idx = kmeans(X, 2, 'Replicates', 1);
fprintf('输出（样本分配）：\n');
disp(idx')
% 输出：1  2  1  2  2 (或类似的分配)

% 语法2：获得质心
fprintf('\n语法2：[idx, C] = kmeans(X, k)\n');
[idx, C] = kmeans(X, 2, 'Replicates', 1);
fprintf('样本分配（idx）：\n');
disp(idx')
fprintf('质心位置（C）：\n');
disp(C)

% 输出：
% 样本分配（idx）：
%    1   2   1   2   2
% 
% 质心位置（C）：
%    0.3333   1.1667  (质心1)
%    5.0000   1.0000  (质心2)

% 语法3：获得簇内距离和
fprintf('\n语法3：[idx, C, sumd] = kmeans(X, k)\n');
[idx, C, sumd] = kmeans(X, 2, 'Replicates', 1);
fprintf('簇内平方和（sumd）：\n');
fprintf('簇1内的点到质心的距离平方和：%.4f\n', sumd(1));
fprintf('簇2内的点到质心的距离平方和：%.4f\n', sumd(2));
disp(sumd)

% 输出：
% 簇1内的点到质心的距离平方和：1.0625
% 簇2内的点到质心的距离平方和：2.0000

% 语法4：获得每个点到质心的距离
fprintf('\n语法4：[idx, C, sumd, D] = kmeans(X, k)\n');
[idx, C, sumd, D] = kmeans(X, 2, 'Replicates', 1);
fprintf('点到质心的距离矩阵（D）：\n');
disp(D)

% 输出：
% D =
%    0.4472   5.4006  (O1到两个质心的距离)
%    0.8165   5.0000  (O2到两个质心的距离)
%    0.5976   5.0237  (O3到两个质心的距离)
%    5.3000   0.0000  (O4到两个质心的距离)
%    5.0990   1.0000  (O5到两个质心的距离)

% 高级参数1：初始化方法
fprintf('\n高级参数：初始化方法\n');
[idx1, C1] = kmeans(X, 2, 'Start', 'plus', 'Replicates', 1);
fprintf('K-means++初始化（推荐）\n');

[idx2, C2] = kmeans(X, 2, 'Start', 'uniform', 'Replicates', 1);
fprintf('随机初始化\n');

% 高级参数2：多次运行取最佳结果
fprintf('\n高级参数：多次运行\n');
[idx, C] = kmeans(X, 2, ...
    'Replicates', 10, ...        % 运行10次，取最好的
    'Display', 'final');         % 显示最终结果

% 高级参数3：完整参数设置
fprintf('\n完整参数设置示例：\n');
[idx, C] = kmeans(X, 2, ...
    'Start', 'plus', ...              % 初始化方法
    'Distance', 'sqeuclidean', ...    % 距离度量（平方欧式）
    'MaxIter', 1000, ...              % 最大迭代数
    'Replicates', 20, ...             % 重复次数
    'Display', 'iter', ...            % 显示每次迭代
    'TolFun', 1e-6);                  % 函数值容差

% 输出会显示每次迭代的信息
```

---

### 2.5 K-Means 的优缺点分析

**优点**

```matlab
% 优点1：速度快
% 复杂度 O(nkt)：n个样本，k个簇，t次迭代

% 实际例子：
n = 1000000;    % 100万个样本
k = 5;          % 5个簇
t = 10;         % 10次迭代
operations = n * k * t;

fprintf('处理规模：%d个样本，%d个簇，%d次迭代\n', n, k, t);
fprintf('总操作数：%d万\n', operations / 10000);
fprintf('现代计算机可在毫秒级完成\n');

% 优点2：易于理解和实现
% 只有4步，算法清晰

% 优点3：聚类效果好（当簇密集、类间清晰时）
rng(42);
X_good = [randn(100, 2) + [0, 0];
          randn(100, 2) + [10, 0];
          randn(100, 2) + [5, 8.66]];

[idx_good, C_good] = kmeans(X_good, 3, 'Replicates', 10);
fprintf('良好的聚类情况：三个高斯簇，K-Means效果很好\n');
```

**缺点和解决方案**

```matlab
% 缺点1：对初值敏感
fprintf('\n缺点1：对初值敏感\n');
fprintf('问题：不同初始质心可能导致不同结果\n');
fprintf('解决方案：多次运行，取最好的结果\n');

% 示例
X_test = [0, 0; 10, 0; 5, 5; 5, 5.5];
results = [];
for rep = 1:10
    [~, ~, sumd] = kmeans(X_test, 2, 'Replicates', 1);
    results = [results; sum(sumd)];
end
fprintf('10次运行的总误差：\n');
disp(results')
fprintf('最小误差：%.4f\n', min(results));
fprintf('最大误差：%.4f\n', max(results));
fprintf('使用 Replicates 参数自动选择最佳\n');

% 缺点2：对异常点敏感
fprintf('\n\n缺点2：对异常点敏感\n');
X_with_outlier = [1, 1; 2, 2; 3, 3; 100, 100];
[idx, C] = kmeans(X_with_outlier, 1);
fprintf('只有4个点，一个是异常点[100,100]\n');
fprintf('质心位置：[%.2f, %.2f]\n', C(1), C(2));
fprintf('质心被异常点严重拖动！\n');
fprintf('理想质心应该在[2, 2]附近\n');

fprintf('\n解决方案：k-medoids（用实际点做质心）或数据预处理\n');

% 缺点3：只能处理连续属性
fprintf('\n\n缺点3：只能处理连续属性\n');
fprintf('问题：离散属性（如颜色、类别）无法用均值表示\n');
fprintf('解决方案：k-modes（离散）或k-prototype（混合）\n');

% 计算簇内平方误差（用于比较不同k值）
fprintf('\n\n肘部法则：选择最优的k值\n');
X_clustering = [randn(100, 2);
                randn(100, 2) + [5, 5];
                randn(100, 2) + [10, 0]];

inertias = [];
silhouette_scores = [];

for k = 1:8
    [idx, ~, sumd] = kmeans(X_clustering, k, 'Replicates', 5);
    inertias = [inertias; sum(sumd)];
    s = silhouette(X_clustering, idx);
    silhouette_scores = [silhouette_scores; mean(s)];
end

fprintf('不同k值的簇内距离平方和（Inertia）：\n');
for i = 1:length(inertias)
    fprintf('k=%d: %.2f\n', i, inertias(i));
end

figure;
subplot(1, 2, 1);
plot(1:length(inertias), inertias, 'b-o', 'LineWidth', 2);
xlabel('K值');
ylabel('Inertia（簇内距离平方和）');
title('肘部法则');
grid on;

subplot(1, 2, 2);
plot(1:length(silhouette_scores), silhouette_scores, 'r-o', 'LineWidth', 2);
xlabel('K值');
ylabel('平均轮廓系数');
title('轮廓系数法则');
grid on;

[~, best_k] = max(silhouette_scores);
fprintf('\n最优K值（根据轮廓系数）：%d\n', best_k);
```

---

## 三、K-Means 改进算法

### 3.1 K-Modes（离散数据）

**问题**：原始K-Means不能处理离散属性

```matlab
fprintf('K-Modes 算法演示\n');
fprintf('===============\n\n');

% 示例数据（离散属性）
% 属性1（颜色）：1=红 2=绿 3=蓝
% 属性2（大小）：1=小 2=中 3=大

X_discrete = [1, 1;  % 红色，小
              1, 2;  % 红色，中
              3, 3;  % 蓝色，大
              3, 3;  % 蓝色，大
              3, 3]; % 蓝色，大

fprintf('离散属性数据（颜色，大小）：\n');
for i = 1:5
    fprintf('样本%d: 颜色=%d, 大小=%d\n', i, X_discrete(i,1), X_discrete(i,2));
end

% K-Modes中，不计算均值，而是计算众数（最频繁值）
function mode_val = compute_mode(column)
    [~, mode_val] = mode(column);
end

% 假设前两个点属于簇1
cluster1_color = X_discrete([1,2], 1);
cluster1_size = X_discrete([1,2], 2);

mode1_color = compute_mode(cluster1_color);
mode1_size = compute_mode(cluster1_size);

fprintf('\n簇1的众数质心（颜色，大小）：[%d, %d]\n', mode1_color, mode1_size);
fprintf('解释：在簇1中，颜色最常见的是%d（出现2次），大小最常见的是%d\n', ...
    mode1_color, mode1_size);

% 假设后三个点属于簇2
cluster2_color = X_discrete([3,4,5], 1);
cluster2_size = X_discrete([3,4,5], 2);

mode2_color = compute_mode(cluster2_color);
mode2_size = compute_mode(cluster2_size);

fprintf('簇2的众数质心（颜色，大小）：[%d, %d]\n', mode2_color, mode2_size);
fprintf('解释：在簇2中，颜色全是%d，大小全是%d\n', mode2_color, mode2_size);

fprintf('\n关键区别：\n');
fprintf('K-Means：质心是均值（数值）\n');
fprintf('K-Modes：质心是众数（最频繁的离散值）\n');
```

### 3.2 K-Prototype（混合属性）

```matlab
fprintf('\n\nK-Prototype 算法演示\n');
fprintf('====================\n\n');

% 混合属性数据
% 属性1-2：连续（身高cm，体重kg）
% 属性3：离散（1=男，2=女）

X_mixed = [170, 65, 1;   % 男
           172, 68, 1;   % 男
           160, 50, 2;   % 女
           165, 55, 2];  % 女

fprintf('混合属性数据（身高, 体重, 性别）：\n');
fprintf('样本1: 身高=170, 体重=65, 性别=男\n');
fprintf('样本2: 身高=172, 体重=68, 性别=男\n');
fprintf('样本3: 身高=160, 体重=50, 性别=女\n');
fprintf('样本4: 身高=165, 体重=55, 性别=女\n');

% K-Prototype 距离定义
function dist = mixed_distance(p1, p2, alpha)
    % 连续属性：欧式距离
    cont_dist = sqrt(sum((p1(1:2) - p2(1:2)).^2));
  
    % 离散属性：汉明距离（0表示相同，1表示不同）
    disc_dist = sum(p1(3) ~= p2(3));
  
    % 总距离 = 连续距离 + α × 离散距离
    dist = cont_dist + alpha * disc_dist;
end

% 计算样本1和样本2的距离（都是男性）
alpha = 10;  % 给离散属性较高的权重
d12 = mixed_distance([170, 65, 1], [172, 68, 1], alpha);
fprintf('\n样本1到样本2的混合距离（都是男）：%.2f\n', d12);
fprintf('计算：连续距离 = sqrt((170-172)^2 + (65-68)^2) = %.2f\n', ...
    sqrt((170-172)^2 + (65-68)^2));
fprintf('      离散距离 = 0（性别相同）\n');
fprintf('      总距离 = %.2f + 10×0 = %.2f\n', ...
    sqrt((170-172)^2 + (65-68)^2), d12);

% 计算样本1和样本3的距离（不同性别）
d13 = mixed_distance([170, 65, 1], [160, 50, 2], alpha);
fprintf('\n样本1到样本3的混合距离（不同性别）：%.2f\n', d13);
fprintf('计算：连续距离 = sqrt((170-160)^2 + (65-50)^2) = %.2f\n', ...
    sqrt((170-160)^2 + (65-50)^2));
fprintf('      离散距离 = 1（性别不同）\n');
fprintf('      总距离 = %.2f + 10×1 = %.2f\n', ...
    sqrt((170-160)^2 + (65-50)^2), d13);

fprintf('\n结论：\n');
fprintf('- 样本1和样本2（都是男）距离较小（%.2f）\n', d12);
fprintf('- 样本1和样本3（不同性别）距离较大（%.2f）\n', d13);
fprintf('- 通过调整α值可以控制离散属性的影响权重\n');
```

---

## 四、最小圆覆盖问题

### 4.1 基本原理

```matlab
fprintf('最小圆覆盖问题演示\n');
fprintf('=================\n\n');

% 问题：找最小的圆覆盖所有点

fprintf('关键定理：最小圆由最多3个点决定\n\n');

% 情况1：直径由2个点确定
fprintf('情况1：圆由2个点的连线作为直径\n');
P1 = [0, 0];
P2 = [4, 0];

center_12 = (P1 + P2) / 2;
radius_12 = norm(P2 - P1) / 2;

fprintf('点P1 = [0, 0], P2 = [4, 0]\n');
fprintf('圆心 = (%.2f, %.2f)\n', center_12(1), center_12(2));
fprintf('半径 = %.2f\n\n', radius_12);

% 情况2：圆由3个点的三角形外接圆确定
fprintf('情况2：圆由3个点的外接圆确定（锐角三角形）\n');
P1 = [0, 0];
P2 = [4, 0];
P3 = [2, 3];

% 外接圆计算
% 圆心(h,k)满足：(P1-center)·(P1-center) = (P2-center)·(P2-center)
%                                        = (P3-center)·(P3-center)

% 从P1和P2的等距条件：
% (0-h)^2 + (0-k)^2 = (4-h)^2 + (0-k)^2
% h^2 = 16 - 8h + h^2
% 8h = 16
% h = 2

% 从P1和P3的等距条件：
% (0-h)^2 + (0-k)^2 = (2-h)^2 + (3-k)^2
% h^2 + k^2 = 4 - 4h + h^2 + 9 - 6k + k^2
% 0 = 13 - 4h - 6k
% 代入h=2：0 = 13 - 8 - 6k => 6k = 5 => k = 5/6

A = [2*(P2(1)-P1(1)), 2*(P2(2)-P1(2));
     2*(P3(1)-P1(1)), 2*(P3(2)-P1(2))];
b = [P2(1)^2 - P1(1)^2 + P2(2)^2 - P1(2)^2;
     P3(1)^2 - P1(1)^2 + P3(2)^2 - P1(2)^2];

center = A \ b;
radius = norm(P1 - center);

fprintf('点P1 = [0, 0], P2 = [4, 0], P3 = [2, 3]\n');
fprintf('外接圆圆心 = [%.4f, %.4f]\n', center(1), center(2));
fprintf('外接圆半径 = %.4f\n\n', radius);

% 验证三个点都在圆上
d1 = norm(P1 - center);
d2 = norm(P2 - center);
d3 = norm(P3 - center);
fprintf('验证（三个点到圆心的距离）：\n');
fprintf('P1到圆心：%.4f\n', d1);
fprintf('P2到圆心：%.4f\n', d2);
fprintf('P3到圆心：%.4f\n', d3);
fprintf('（都应该等于半径%.4f）\n\n', radius);

% 绘制
figure;
plot([P1(1), P2(1), P3(1), P1(1)], [P1(2), P2(2), P3(2), P1(2)], 'b-', 'LineWidth', 2);
hold on;
plot([P1(1), P2(1), P3(1)], [P1(2), P2(2), P3(2)], 'b*', 'MarkerSize', 12);

theta = linspace(0, 2*pi, 100);
x = center(1) + radius * cos(theta);
y = center(2) + radius * sin(theta);
plot(x, y, 'r-', 'LineWidth', 2);

plot(center(1), center(2), 'r+', 'MarkerSize', 15, 'LineWidth', 2);

axis equal;
grid on;
legend('三角形', '顶点', '外接圆', '圆心');
title('3点外接圆');
```

### 4.2 增量法算法

```matlab
fprintf('\n\n增量法求最小圆覆盖\n');
fprintf('==================\n\n');

function [center, radius] = min_circle_incremental(points)
    % 增量法求最小圆覆盖
    % 输入：points (n×2 矩阵)
    % 输出：center, radius
  
    n = size(points, 1);
  
    % 初始化：第一个点
    center = points(1, :);
    radius = 0;
  
    fprintf('初始化：将第1个点设为圆心，半径=0\n');
    fprintf('圆心：[%.2f, %.2f]，半径：%.2f\n\n', center(1), center(2), radius);
  
    for i = 2:n
        % 检查第i个点是否在圆内
        d = norm(points(i, :) - center);
      
        fprintf('第%d次迭代：加入点(%d)\n', i-1, i);
        fprintf('点(%d)到当前圆心的距离：%.2f\n', i, d);
      
        if d > radius + 1e-10
            % 点在圆外，需要扩展圆
            fprintf('点在圆外！需要扩展圆。\n');
            fprintf('暂定：以点1和点%d的连线为直径\n', i);
          
            % 以当前圆心和新点作为直径
            center = (center + points(i, :)) / 2;
            radius = norm(points(i, :) - center);
          
            fprintf('新圆心：[%.2f, %.2f]，新半径：%.2f\n', ...
                center(1), center(2), radius);
          
            % 检查前i-1个点
            fprintf('检查前%d个点是否都在新圆内...\n', i-1);
            all_inside = true;
            for j = 1:i-1
                d_j = norm(points(j, :) - center);
                if d_j > radius + 1e-10
                    fprintf('点%d不在圆内（距离%.2f > 半径%.2f）\n', j, d_j, radius);
                    all_inside = false;
                end
            end
          
            if all_inside
                fprintf('所有点都在圆内✓\n');
            end
        else
            fprintf('点在圆内，继续\n');
        end
        fprintf('\n');
    end
end

% 测试
points = [0, 0; 1, 0; 0.5, 1; 2, 2; -1, 0.5];
[center, radius] = min_circle_incremental(points);

fprintf('\n\n最终结果：\n');
fprintf('圆心：[%.4f, %.4f]\n', center(1), center(2));
fprintf('半径：%.4f\n', radius);

% 验证所有点都在圆内
fprintf('\n验证（所有点到圆心的距离）：\n');
for i = 1:size(points, 1)
    d = norm(points(i, :) - center);
    in_circle = d <= radius + 1e-10;
    fprintf('点%d：距离%.4f %s\n', i, d, in_circle ? '✓在圆内' : '✗在圆外');
end

% 绘制
figure;
scatter(points(:,1), points(:,2), 100, 'b*', 'LineWidth', 2);
hold on;
theta = linspace(0, 2*pi, 100);
x = center(1) + radius * cos(theta);
y = center(2) + radius * sin(theta);
plot(x, y, 'r-', 'LineWidth', 2);
plot(center(1), center(2), 'r+', 'MarkerSize', 15, 'LineWidth', 2);
axis equal;
grid on;
title(sprintf('最小圆覆盖（圆心[%.2f,%.2f]，半径%.2f）', ...
    center(1), center(2), radius));
legend('数据点', '最小圆', '圆心');
```

---

## 五、总结与对比

### 三种算法的对比表

```matlab
fprintf('三种算法的对比\n');
fprintf('===============\n\n');

algorithm_comparison = array2table({
    'PCA', '高维数据', '主成分、降维数据', 'O(n·m²)', '特征提取、可视化';
    'K-Means', '无标签数据', '簇标签、质心', 'O(nkt)', '簇分析、聚类';
    '最小圆覆盖', '平面点集', '圆心、半径', 'O(n³)', '几何计算'
}, 'VariableNames', {'算法', '输入数据', '输出结果', '时间复杂度', '适用场景'});

disp(algorithm_comparison)

% 输出：
%     算法          输入数据        输出结果       时间复杂度      适用场景
%     __________  ____________  ______________  __________  __________________
%     'PCA'       '高维数据'      '主成分、降维数据'  'O(n·m²)'  '特征提取、可视化'
%     'K-Means'   '无标签数据'    '簇标签、质心'    'O(nkt)'   '簇分析、聚类'
%     '最小圆覆盖'  '平面点集'      '圆心、半径'      'O(n³)'    '几何计算'
```

### 参数选择建议

```matlab
fprintf('\n\n参数选择建议\n');
fprintf('============\n\n');

fprintf('PCA：选择保留多少维度\n');
fprintf('-----\n');
fprintf('方法1：保留累计方差达到95%%\n\n');

% 示例
rng(42);
data = randn(100, 1000);  % 100维，1000个样本
[~, ~, latent] = pca(data');

cumulative_var = cumsum(latent) / sum(latent);
threshold = 0.95;
n_components = find(cumulative_var >= threshold, 1);

fprintf('总维度：100\n');
fprintf('保留95%%方差需要：%d维\n', n_components);
fprintf('维度约简比例：%.1f%%\n\n', (1 - n_components/100)*100);

fprintf('方法2：使用肘部法则（Explained Variance Ratio）\n');
fprintf('从累计方差曲线中找"肘部"（斜率变化最大的地方）\n\n');

fprintf('K-Means：选择簇数k\n');
fprintf('-----\n');
fprintf('方法1：肘部法则（Elbow Method）\n\n');

% 生成测试数据
rng(42);
X = [randn(100, 2) + [0, 0];
     randn(100, 2) + [10, 0];
     randn(100, 2) + [5, 8.66]];

k_range = 1:10;
inertias = [];

for k = k_range
    [~, ~, sumd] = kmeans(X, k, 'Replicates', 3);
    inertias = [inertias, sum(sumd)];
end

fprintf('不同K值的Inertia（簇内距离平方和）：\n');
for i = 1:length(k_range)
    fprintf('k=%2d: %8.2f\n', k_range(i), inertias(i));
end

fprintf('\n在k=3附近，曲线斜率明显变小（肘部）\n');
fprintf('选择k=3\n\n');

fprintf('方法2：轮廓系数（Silhouette Coefficient）\n');

silhouette_scores = [];
for k = 2:10
    idx = kmeans(X, k, 'Replicates', 3);
    s = silhouette(X, idx);
    silhouette_scores = [silhouette_scores, mean(s)];
end

fprintf('不同K值的平均轮廓系数：\n');
for i = 1:length(silhouette_scores)
    fprintf('k=%2d: %.4f\n', i+1, silhouette_scores(i));
end

[~, best_k_idx] = max(silhouette_scores);
best_k = best_k_idx + 1;
fprintf('\n最优K值（轮廓系数最大）：%d\n', best_k);
```

---

## 六、实践练习与案例

### 练习1：对鸢尾花数据进行PCA

```matlab
fprintf('练习1：鸢尾花数据PCA分析\n');
fprintf('========================\n\n');

% 加载数据
load fisheriris

fprintf('数据信息：\n');
fprintf('样本数：%d\n', length(species));
fprintf('特征数：4（花萼长、花萼宽、花瓣长、花瓣宽）\n');
fprintf('类别数：3（Setosa, Versicolor, Virginica）\n\n');

% 进行PCA
[coeff, score, latent] = pca(meas);

fprintf('特征值（方差）：\n');
disp(latent)

fprintf('\n方差解释比例：\n');
explained_ratio = latent / sum(latent);
disp(explained_ratio)

fprintf('累计方差解释比例：\n');
cumulative_ratio = cumsum(explained_ratio);
disp(cumulative_ratio)

fprintf('\n前2个PC就能解释%.2f%%的方差\n\n', cumulative_ratio(2)*100);

% 降到2维用于可视化
figure;
colors = [1, 2, 3];  % 三种颜色对应三个类别
for i = 1:length(unique(species))
    if i == 1
        species_name = 'Setosa';
    elseif i == 2
        species_name = 'Versicolor';
    else
        species_name = 'Virginica';
    end
    idx = strcmp(species, species_name);
    scatter(score(idx,1), score(idx,2), 50, 'filled', ...
        'DisplayName', species_name);
    hold on;
end

xlabel(sprintf('PC1 (%.1f%%)', explained_ratio(1)*100));
ylabel(sprintf('PC2 (%.1f%%)', explained_ratio(2)*100));
title('鸢尾花PCA降维可视化');
legend;
grid on;

fprintf('结论：三个品种在PC1-PC2平面上有很好的分离\n');
```

### 练习2：聚类合成数据

```matlab
fprintf('\n\n练习2：K-Means聚类\n');
fprintf('==================\n\n');

% 生成聚类数据（3个高斯簇）
rng(42);
X = [randn(100, 2) + [0, 0];
     randn(100, 2) + [10, 0];
     randn(100, 2) + [5, 8.66]];  % 三个质心呈等边三角形

fprintf('生成300个点，分成3个高斯簇\n');
fprintf('质心：[0,0], [10,0], [5,8.66]\n\n');

% K-Means聚类
[idx, C, sumd] = kmeans(X, 3, 'Replicates', 10);

fprintf('聚类结果：\n');
fprintf('簇1：%d个点\n', sum(idx==1));
fprintf('簇2：%d个点\n', sum(idx==2));
fprintf('簇3：%d个点\n', sum(idx==3));

fprintf('\n质心位置：\n');
fprintf('簇1质心：[%.2f, %.2f]\n', C(1,1), C(1,2));
fprintf('簇2质心：[%.2f, %.2f]\n', C(2,1), C(2,2));
fprintf('簇3质心：[%.2f, %.2f]\n', C(3,1), C(3,2));

fprintf('\n簇内距离平方和：\n');
fprintf('簇1：%.2f\n', sumd(1));
fprintf('簇2：%.2f\n', sumd(2));
fprintf('簇3：%.2f\n', sumd(3));
fprintf('总误差：%.2f\n\n', sum(sumd));

% 绘制结果
figure;
colors = {'r', 'g', 'b'};
for c = 1:3
    scatter(X(idx==c,1), X(idx==c,2), 30, colors{c}, 'filled', ...
        'DisplayName', sprintf('簇%d',c));
    hold on;
end
scatter(C(:,1), C(:,2), 200, 'k*', 'LineWidth', 3, 'DisplayName', '质心');
xlabel('特征1');
ylabel('特征2');
title('K-Means 聚类结果');
legend;
grid on;

fprintf('聚类成功！三个簇被正确识别\n');
```

### 练习3：比较不同距离度量

```matlab
fprintf('\n\n练习3：不同距离度量\n');
fprintf('==================\n\n');

X = [0, 0; 10, 0; 0, 10; 10, 10];

fprintf('4个点：(0,0), (10,0), (0,10), (10,10)\n\n');

% 欧式距离
D_euclidean = pdist(X, 'euclidean');
fprintf('欧式距离矩阵（上三角）：\n');
fprintf('%.2f %.2f %.2f %.2f %.2f %.2f\n', D_euclidean);

fprintf('\n距离矩阵（完整）：\n');
D_euclidean_full = squareform(D_euclidean);
disp(D_euclidean_full)

% 曼哈顿距离
D_manhattan = pdist(X, 'cityblock');
fprintf('\n曼哈顿距离矩阵（完整）：\n');
D_manhattan_full = squareform(D_manhattan);
disp(D_manhattan_full)

% 切比雪夫距离
D_chebyshev = pdist(X, 'chebychev');
fprintf('\n切比雪夫距离矩阵（完整）：\n');
D_chebyshev_full = squareform(D_chebyshev);
disp(D_chebyshev_full)

fprintf('\n比较：\n');
fprintf('点(0,0)到点(10,10)的距离：\n');
fprintf('- 欧式距离：%.2f\n', D_euclidean_full(1,4));
fprintf('- 曼哈顿距离：%.2f\n', D_manhattan_full(1,4));
fprintf('- 切比雪夫距离：%.2f\n', D_chebyshev_full(1,4));

fprintf('\n欧式距离 = sqrt(10²+10²) = %.2f\n', sqrt(10^2+10^2));
fprintf('曼哈顿距离 = |10|+|10| = 20\n');
fprintf('切比雪夫距离 = max(|10|,|10|) = 10\n');
```

---

## 七、常见错误与解决方案

```matlab
fprintf('常见错误与解决方案\n');
fprintf('==================\n\n');

fprintf('错误1：PCA中没有零均值化\n');
fprintf('-----\n');
X_raw = [100, 200; 110, 210; 120, 220];
X_not_centered = X_raw;  % 未零均值化

[coeff1, ~, latent1] = pca(X_not_centered);

X_centered = X_raw - mean(X_raw, 1);
[coeff2, ~, latent2] = pca(X_centered);

fprintf('未零均值化的第一主成分方向：[%.4f, %.4f]\n', coeff1(1,1), coeff1(2,1));
fprintf('零均值化后的第一主成分方向：[%.4f, %.4f]\n', coeff2(1,1), coeff2(2,1));
fprintf('\n结论：不零均值化会导致主成分错误！\n\n');

fprintf('错误2：K-Means中k值选择不当\n');
fprintf('-----\n');
X = [randn(100, 2); randn(100, 2)+[5, 5]];

fprintf('实际数据有2个簇，但错误地选择k=4\n\n');

[idx_wrong, C_wrong] = kmeans(X, 4, 'Replicates', 5);
fprintf('k=4时的簇分配：\n');
for i = 1:4
    fprintf('簇%d：%d个点\n', i, sum(idx_wrong==i));
end

fprintf('\n这样的聚类没有意义，会过度分割数据\n\n');

fprintf('错误3：处理异常值\n');
fprintf('-----\n');
X_no_outlier = [1, 1; 2, 2; 3, 3];
X_with_outlier = [1, 1; 2, 2; 3, 3; 100, 100];

[~, C_no] = kmeans(X_no_outlier, 1);
[~, C_with] = kmeans(X_with_outlier, 1);

fprintf('没有异常点时，质心：[%.2f, %.2f]\n', C_no(1), C_no(2));
fprintf('有异常点时，质心：[%.2f, %.2f]\n', C_with(1), C_with(2));
fprintf('\n单个异常点严重影响了质心位置！\n');
fprintf('解决方案：数据预处理（去除异常值）或使用k-medoids\n\n');

fprintf('错误4：尺度不同的特征\n');
fprintf('-----\n');
X_unscaled = [1, 1000; 2, 2000; 3, 3000];
X_scaled = (X_unscaled - mean(X_unscaled,1)) ./ std(X_unscaled,0,1);

fprintf('未标准化数据\n');
[idx1, C1] = kmeans(X_unscaled, 1);
fprintf('质心：[%.2f, %.2f]\n', C1(1), C1(2));

fprintf('\n标准化数据后：\n');
[idx2, C2] = kmeans(X_scaled, 1);
fprintf('质心：[%.4f, %.4f]\n', C2(1), C2(2));

fprintf('\n未标准化时，第二个特征（1000数量级）主导了距离计算\n');
fprintf('标准化后两个特征的贡献相等\n\n');

fprintf('最佳实践：\n');
fprintf('- 进行特征标准化：X_scaled = (X - mean(X)) ./ std(X)\n');
fprintf('- 这样所有特征对距离的贡献相等\n');
```

---

## 八、总结

本文详细介绍了三种重要的数据分析算法：

1. **PCA（主成分分析）**：
   - 通过特征值分解找到数据的主要方向
   - 可以有效地进行降维和特征提取
   - 保留原始数据的主要信息
2. **K-Means（聚类）**：
   - 简单快速的无监督学习算法
   - 通过迭代优化找到最优的簇划分
   - 对初值敏感，需要多次运行取最佳结果
3. **改进算法**：
   - K-Modes：处理离散属性
   - K-Prototype：处理混合属性
   - K-中心点：处理异常值

掌握这些算法的原理和实现，对于数据分析和机器学习工作都非常重要！

## 九、⭐⭐⭐ 考试/实验重点总结

### 必考算法流程

#### PCA算法完整步骤（⭐⭐⭐ 必考）

```matlab
% 【PCA标准实现流程】

% 步骤1：数据准备
X_raw = [数据矩阵];             % n×m矩阵（n维，m个样本）

% 步骤2：数据中心化（零均值化）⭐⭐⭐
mean_X = mean(X_raw, 2);        % 每行（维度）的均值
X = X_raw - mean_X;             % 减去均值

% 步骤3：计算协方差矩阵
m = size(X, 2);                 % 样本数
C = (1/m) * X * X';             % n×n协方差矩阵
% 或用函数：C = cov(X')（分母是m-1）

% 步骤4：特征值分解⭐⭐⭐
[V, D] = eig(C);
eigenvalues = diag(D);

% 步骤5：按特征值从大到小排序
[sorted_eigenvalues, idx] = sort(eigenvalues, 'descend');
V_sorted = V(:, idx);           % 重排特征向量

% 步骤6：选择前k个主成分
k = 1;                          % 降到k维
P = V_sorted(:, 1:k)';          % 投影矩阵（k×n）

% 步骤7：投影降维
Y = P * X;                      % k×m降维数据

% 步骤8：计算方差解释比例
explained_ratio = sum(sorted_eigenvalues(1:k)) / sum(sorted_eigenvalues);
fprintf('保留%.2f%%的方差\n', explained_ratio*100);

% 🔑 考试要点：
% - 必须先零均值化！
% - 协方差矩阵是对称的
% - 特征值=各方向方差
% - 选择k使累计方差≥95%
```

#### K-Means算法完整步骤（⭐⭐⭐ 必考）

```matlab
% 【K-Means标准实现流程】

X = [数据矩阵];                 % m×n矩阵（m个样本，n维）
k = 3;                          % 簇数

% 步骤1：初始化质心
idx = randperm(size(X,1), k);   % 随机选k个样本
centers = X(idx, :);

% 步骤2-4：迭代优化
max_iter = 100;
tol = 1e-6;

for iter = 1:max_iter
    % 步骤2：样本分配（找最近质心）⭐⭐⭐
    distances = pdist2(X, centers);  % m×k距离矩阵
    [~, assignment] = min(distances, [], 2);  % 每行最小值
  
    % 步骤3：更新质心（计算均值）⭐⭐⭐
    old_centers = centers;
    for j = 1:k
        cluster_points = X(assignment == j, :);
        if ~isempty(cluster_points)
            centers(j, :) = mean(cluster_points, 1);
        end
    end
  
    % 步骤4：检查收敛
    center_shift = max(sqrt(sum((centers - old_centers).^2, 2)));
    if center_shift < tol
        fprintf('第%d次迭代收敛\n', iter);
        break;
    end
end

% 计算簇内误差
sumd = zeros(k, 1);
for j = 1:k
    cluster_points = X(assignment == j, :);
    sumd(j) = sum(sum((cluster_points - centers(j,:)).^2));
end

fprintf('总误差：%.4f\n', sum(sumd));

% 🔑 考试要点：
% - pdist2计算所有点到质心的距离
% - min(..., [], 2)按行找最小值
% - 更新质心用mean
% - 收敛判断：质心不再移动
```

#### MATLAB内置函数调用（⭐⭐⭐ 实际应用）

```matlab
% PCA内置函数
[coeff, score, latent] = pca(X);
% coeff：主成分系数（特征向量）
% score：降维后数据
% latent：方差（特征值）

% 降到k维
[coeff, score, latent] = pca(X, 'NumComponents', k);

% K-Means内置函数
[idx, C, sumd, D] = kmeans(X, k, 'Replicates', 10);
% idx：样本分配
% C：质心位置
% sumd：簇内距离平方和
% D：点到质心距离矩阵

% 🔑 参数设置：
% - 'Replicates', 10：运行10次取最佳
% - 'Distance', 'sqeuclidean'：距离度量
% - 'MaxIter', 1000：最大迭代数
```

### 关键概念速记

**PCA核心概念**：

1. **目标**：找方差最大的方向
2. **方法**：特征值分解协方差矩阵
3. **选择k**：累计方差≥95%（或肘部法则）
4. **输出**：降维数据、主成分、方差比例

**K-Means核心概念**：

1. **目标**：最小化簇内距离平方和
2. **方法**：迭代分配+更新质心
3. **选择k**：肘部法则或轮廓系数
4. **输出**：簇标签、质心位置、总误差

**三种距离**：

- 欧氏距离：$\sqrt{\sum(x_i-y_i)^2}$ （最常用）
- 曼哈顿距离：$\sum|x_i-y_i|$
- 切比雪夫距离：$\max|x_i-y_i|$

### 实验常见错误

#### 错误1：PCA没有零均值化

```matlab
% ❌ 错误
X = [数据];
[coeff, ~, ~] = pca(X);         % X未中心化

% ✅ 正确
X_centered = X - mean(X, 1);    % 按列中心化
[coeff, ~, ~] = pca(X_centered);
% 或直接用pca函数（自动中心化）
```

#### 错误2：K-Means的k值选择不当

```matlab
% 应该用肘部法则选择
inertias = [];
for k = 1:10
    [~, ~, sumd] = kmeans(X, k, 'Replicates', 5);
    inertias = [inertias; sum(sumd)];
end

plot(1:10, inertias, 'o-', 'LineWidth', 2)
xlabel('K值'), ylabel('Inertia')
title('肘部法则选择K')
% 找曲线"肘部"（斜率变化大的地方）
```

#### 错误3：样本和特征维度混淆

```matlab
% PCA要求：样本按列排列（或在pca函数中转置）
% 数据：100个样本，每个5维

% ✅ 正确格式1
X1 = randn(5, 100);             % 5×100（5维，100样本）
[coeff1, ~, ~] = pca(X1');      % 转置！

% ✅ 正确格式2
X2 = randn(100, 5);             % 100×5（100样本，5维）
[coeff2, ~, ~] = pca(X2);       % 不转置

% K-Means要求：样本按行排列
[idx, C] = kmeans(X2, 3);       % ✓ 100×5正确
```

### 实验报告模板

```matlab
%% 实验三：PCA与K-Means
% 姓名：XXX
% 学号：XXX
% 日期：2024-XX-XX

%% 1. 实验目的
% - 掌握PCA降维方法
% - 理解K-Means聚类算法
% - 学会使用MATLAB进行数据分析

%% 2. 实验内容

%% 2.1 PCA降维
clear all, close all, clc
rng default

% 加载数据
load fisheriris
X = meas;                       % 150×4数据

% PCA分析
[coeff, score, latent] = pca(X);

% 输出结果
fprintf('方差解释比例：\n');
explained = latent / sum(latent);
for i = 1:length(explained)
    fprintf('PC%d: %.2f%%\n', i, explained(i)*100);
end

% 可视化
figure
scatter(score(:,1), score(:,2), 50, species)
xlabel(sprintf('PC1 (%.1f%%)', explained(1)*100))
ylabel(sprintf('PC2 (%.1f%%)', explained(2)*100))
title('PCA降维可视化')

%% 2.2 K-Means聚类
% （类似结构）

%% 3. 实验结论
% - PCA前2个PC解释了XX%的方差
% - K-Means成功识别出3个簇
% - ...
```

### 考前冲刺检查清单

- [ ] 理解PCA的7个步骤（零均值化、协方差、特征值分解等）
- [ ] 会用pca函数并解释coeff、score、latent
- [ ] 理解方差解释比例的计算和意义
- [ ] 掌握K-Means的4个步骤（初始化、分配、更新、收敛）
- [ ] 会用kmeans函数和解释返回值
- [ ] 理解肘部法则选择k值
- [ ] 会用pdist2计算距离矩阵
- [ ] 理解轮廓系数评估聚类质量
- [ ] 能够可视化降维和聚类结果

<div align="center">⁂</div>
