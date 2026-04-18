## Document

乐绎华，Yue Yihua

September 17， 2025

## Contents

## 第一周电子版作业

□ Q1．安装MATLAB软件，并在命令行键入命令ver，检查自己的版本以及工具箱安装情况。（请在作业中提供该命令的 MATLAB运行结果，字体可以小一些。如果个人无法安装 MATLAB请指明自己安装的方式和计算机位置）
□ Q2．定义矩阵 $\boldsymbol{A}=\left[\begin{array}{ccc}\mathbf{1} & \mathbf{0} & -\mathbf{1} \\ \mathbf{- 1} & \mathbf{2} & \mathbf{1}\end{array}\right], \boldsymbol{B}=\left[\begin{array}{ccc}\mathbf{1} & \mathbf{0} & \mathbf{3} \\ \mathbf{0} & \mathbf{3} & \mathbf{1}\end{array}\right]$ ，以下代码运行结果是什么？并说明得出相应结果的理由
$A * B$
$A * B$
\％提示：B＇为B的共轭转置
$\square \mathrm{Q3}$ ．当 $\boldsymbol{a}$ 为何值时，矩阵 $\boldsymbol{A}=\left(\begin{array}{lll}\mathbf{1} & \mathbf{1} & \mathbf{2} \\ \mathbf{0} & \mathbf{3} & \mathbf{4} \\ \mathbf{0} & \mathbf{0} & \boldsymbol{a}\end{array}\right)$ 不能对角化？
（1）利用已学的高等代数的知识手算这道题。（可以键入在文档，可以拍照插入到文档）
（2）利用MATLAB帮助系统，了解MATLAB函数jordan的用法，并利用该函数验证 $\boldsymbol{a}=\mathbf{0}, \boldsymbol{a}=\mathbf{1}, \boldsymbol{a}=\mathbf{3}$ 时 $\boldsymbol{A}$ 分别能否对角化。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-002.jpg?height=725&width=1204&top_left_y=429&top_left_x=459)

```
>> A.*B
ans =

\begin{tabular}{rrr}
1 & 0 & -3 \\
0 & 6 & 1
\end{tabular}
```

$\mathrm{A} * \mathrm{~B}$ 没有输出因为 $2 \times 3$ 矩阵和 $2 \times 3$ 矩阵不可以直接进行矩阵乘法。
$\mathrm{A} * \mathrm{~B}^{\prime}$ 是在 $B$ 转置变成 $3 \times 2$ 矩阵之后可以左乘 $A$ 。
A．$* \mathrm{~B}$ 是矩阵的 Hadamard 乘积，若 $A=\left(a_{i j}\right), B=\left(b_{i j}\right)$ 则 $A \circ B=\left(a_{i j} b_{i j}\right)$ ，所以 $2 \times 3$ 矩阵和 $2 \times 3$ 矩阵可以直接进行 Hadamard 乘积。

Q3．$A$ 不能对角化 $\Rightarrow A$ 有重根 $\Rightarrow a=1$ 或了。
在 $a=1$ 。则。 $A=\left[\begin{array}{lll}1 & 1 & 2 \\ 0 & 3 & 4 \\ 0 & 0 & 1\end{array}\right], A-I=\left[\begin{array}{lll}0 & 1 & 1 \\ 0 & 2 & 4 \\ 0 & 0 & 0\end{array}\right]$ dinker $(A-I)=3-r(A-I)=2 \lambda=1$ 代数重数为 2 ，几何重数为 $2 \Rightarrow A$ 可对角化。

若 $a=3$ 。 则 $A=\left[\begin{array}{ccc}-2 & 1 & 2 \\ 0 & 0 & -2\end{array}\right] \quad A$ 古 $\left[\begin{array}{ll}1 & 2 \\ 0 & 3 \\ 0 & 0 \\ 0 & 3\end{array}\right]$ ，$A S I=\left[\begin{array}{ccc}-2 & 1 & 2 \\ 0 & 0 & 4 \\ 0 & 0 & 0\end{array}\right]$ ， $\operatorname{diake}(A-3 i) \lambda=3$ 代数重数为 2 ，几何重数为 $1 \Rightarrow A$ 不们对角化。

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-003.jpg?height=721&width=1202&top_left_y=1048&top_left_x=459)

$$
\begin{aligned}
& \gg A=\left[\begin{array}{llllll}
1 & 1 & 2 ; 0 & 3 & 4 ; 0 & 0
\end{array}\right] \\
& A= \\
& \begin{array}{rrrr}
1 & 1 & 2 & \\
0 & 3 & 4 & \\
0 & 0 & 1 &
\end{array}
\end{aligned}
$$

>> jordan (A)

$$
\begin{array}{r}
\text { ans }= \\
\begin{array}{rrr}
3 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{array}
\end{array}
$$

>> A=[ll 1 2;0 3 4;0 0 3]
$\mathrm{A}=$

| 1 | 1 | 2 |
| :--- | :--- | :--- |
| 0 | 3 | 4 |
| 0 | 0 | 3 |

>> jordan (A)
ans =

| 1 | 0 | 0 |
| :--- | :--- | :--- |
| 0 | 3 | 1 |
| 0 | 0 | 3 |

fx >>

# Document 

乐绎华，Yue Yihua

September 23， 2025

## Contents

## 第一次实验课后作业

【1】计算 $y=\frac{2 \cos (0.3 \pi)}{1+\sqrt{5}} \quad$ 的值。
【2】将分母中的 5 替换成 $\mathrm{e}^{2}+1, \mathrm{x}=-3: 3$ ，结果如何。
【3】一个序列1：16，变成 4 阶矩阵，求逆和行列式？结果如何加上一个希尔伯特阵，分别求逆和行列式。
分析一下原因？
【4】生成一个4阶随机阵，求特征值和特征向量。

```
命令行容口
不动采 MATLAB? 请美间有关央遈入门的资浱。
要开狤,请媬入doco
有关产品信息,请访问 www.mathworks.ccmo
>> y-2cos(0.3 pi)/(1+sqrt(5))
y=2cos(0.3 p1)/(1+sqrt(5))
无效表达式。请检查咉失的乘法运算符、㰦失或不对称的分隔符或者其借语法错误。要构造拒阵,请使用方括号而不员圆括号。
>> y-2 cos(0.3 pi)/(1+sgrt(5))
y=2 cos(0.3 p1)/(1+sqre(5))
无效表这
>> y-2*COS(0.3 pi)/(1+sgrt(5))
y=2*cos(0.3 p1)/(1+sqre(5))
无效表达式。请检查咉失的乘法运其符、垬失或不对利的分隔符或者其借语法错误。要构造就阵,清使用方括号而不员圆括号。
>> y-2*\operatorname{cos[0.3*pi)/(1+sgrt(5))}
y =
    0.3633
>> y=2* cos(0.3*p1)/(en.2+1)
函嗐或宽里 'e' 无法识别。
>> y-2*cos(0.3*pi)/(exp(2}+1)
v =
    0.1401
>> x-[-3;3]
x =
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-006.jpg?height=21&width=257&top_left_y=1039&top_left_x=515)

```
>> y=2* cos(0.3*pi)/(x)
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-006.jpg?height=31&width=96&top_left_y=1087&top_left_x=489)

```
>> y-2* cos(0.3*pi)./(x)
y =
    -0.3919 -0.5878 -1.1756 Inf 1.1756 0.5878 0.3919
>> z=[1:16]
z=
    \begin{array} { l l l l l l l l l l l l l l l l } { 1 } & { 2 } & { 3 } & { 4 } & { 5 } & { 6 } & { 7 } & { 8 } & { 9 } & { 1 0 } & { 1 1 } & { 1 2 } & { 1 3 } & { 1 4 } & { 1 5 } & { 1 6 } \end{array}
>> z=reshape (z,4,4)
z-
        \begin{array} { r r r } { 5 } & { 9 } & { 1 3 } \\ { 6 } & { 1 0 } & { 1 4 } \end{array}
    \begin{array} { l l l l } { 3 } & { 7 } & { 1 1 } & { 1 5 } \\ { 4 } & { 8 } & { 1 2 } & { 1 6 } \end{array}
>>
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-007.jpg?height=1030&width=1202&top_left_y=429&top_left_x=459)

第一个逆求不出来，因为是奇异矩阵，行列式为 0 ．第二个可逆．

```
>> rand(4)
ans =
    0.8147 0.6324 0.9575 0.9572
    0.9058 0.0975 0.9649 0.4854
    0.1270 0.2785 0.1576 0.8003
    0.9134 0.5469 0.9706 0.1419
>> a=ans
a =
    0.8147 0.6324 0.9575 0.9572
    0.9058 0.0975 0.9649 0.4854
    0.1270 0.2785 0.1576 0.8003
    0.9134 0.5469 0.9706 0.1419
>> eig(a)
ans =
    2.4021
    -0.0346
    -0.7158
    -0.4400
>> [u,v]=eig(a)
u =

\begin{tabular}{rrrr}
-0.6621 & -0.7149 & 0.1745 & 0.1821 \\
-0.4819 & -0.0292 & -0.6291 & -0.9288 \\
-0.2766 & 0.6972 & 0.5995 & 0.3178 \\
-0.5029 & -0.0438 & -0.4630 & 0.0570
\end{tabular}
v =
fx >>
```


## Document

乐绎华，Yue Yihua

September 24， 2025

## Contents

## 第二周电子版作业

## □Q1．改编的习题2第8题

（1）通过MATLAB函数diffil算求 $\boldsymbol{y}(\boldsymbol{t})=|\sin \boldsymbol{t}|$ 的导数 $\boldsymbol{y}^{\prime}(\boldsymbol{t})$ ，结果表达式在哪些点存在异常？为什么？
（2）计算 $\boldsymbol{y}^{\prime}\left(\frac{\boldsymbol{\pi}}{\mathbf{2}}\right)$ 与 $\boldsymbol{y}(\boldsymbol{t})$ 在 $\boldsymbol{t}=\mathbf{0}$ 的左导数 $\boldsymbol{y}_{-}^{\prime}(\mathbf{0})$ ，注意：左导数不是导数的左权限！
□ Q2．（1）用数学分析的方法证明等式 $\lim _{n \rightarrow \infty} \frac{n}{\sqrt[n]{n!}}=\mathbf{e}$ ．
（2）采用符号计算与函数isAlways验证 $\lim _{n \rightarrow \infty} \frac{n}{\sqrt[n]{n!}}=\mathbf{e}$ ．（提示函数：factorial）

Q3．计算二重积分（高数难度）

$$
\iint_{D}^{\square} \frac{1}{\sqrt{\left(1+x^{2}+y^{2}\right)^{3}}} \mathrm{~d} x \mathrm{~d} y, \quad\{D: 0 \leq x \leq 1,0 \leq y \leq 1\}
$$

（1）用已学习的数学分析知识计算这个积分。
（2）采用MATLAB符号计算验证你上一问的结果。（提示：由于 MATLAB的计算能力有限，被积函数的分母定义可能需要调整）

```
要开始,请键入doc。
有关产品信息,请访问 www.mathworks.com。
>> syms f(x)
>> f(x) = abs(sin(x))
f(x) =
abs(sin(x))
>> dfdx(x) = diff(f(x),x)
dfdx (x) =
(\operatorname{cos(\operatorname{conj(x))* sin(x) + sin(\operatorname{conj(x))* cos(x))/(2*(sin(\operatorname{conj(x))* sin(x))^(1/2))}}m}m}m
>> syms t
y = abs(sin(t));
dy = diff(y, t)
dy =
(\operatorname{cos(\operatorname{conj(t))*sin(t) + sin(\operatorname{conj(t))*\operatorname{cos(t))/(2*(sin(\operatorname{conj(t))*sin(t))^(1/2))}}m}m}m}m
>> simplify(dy)
ans =
sin(2*real (t))/(2*(sin(conj(t))* sin(t))^(1/2))
>> v = subs(dy, t, pi/2);
>> v = subs(dy, t, pi/2);
>> v = subs(dy, t, pi/2)
v =
0
>> left_deriv_at_0 = limit((abs(sin(t)) - 0)./t, t, 0, 'left')
left_deriv_at_0 =
-1
fr >> \textit{
```

表达式会在 $\frac{\pi}{2}+k \pi, k \in \mathbb{Z}$ 处异常。
Exercise 0．1．用数学分析的方法证明 $\lim _{n \rightarrow \infty} \frac{n}{\sqrt[n]{n!}}=e$ ．
Proof．记 $a_{n}=\frac{n}{\sqrt[n]{n!}}$ ，则 $\ln a_{n}=\ln n-\frac{1}{n} \sum_{k=1}^{n} \ln k=-\frac{1}{n} \sum_{k=1}^{n} \ln \frac{k}{n}$ 。由积分定义可知

$$
\lim _{n \rightarrow \infty} \ln a_{n}=-\int_{0}^{1} \ln x \mathrm{~d} x=1
$$

从而

$$
\lim _{n \rightarrow \infty} a_{n}=e
$$

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-011.jpg?height=966&width=1204&top_left_y=429&top_left_x=459)
Note 0．2．坑在于算出来的 Ls 是一个符号 $\exp (\operatorname{sym}(1))$ 而不是 $\exp (1)$ 。所以 isALlways 要与 $\exp (\operatorname{sym}(1))$ 比较而不是 $\exp (1)$ ．

问题 3：

由对称性，

$$
\begin{aligned}
I & =\iint_{D} \frac{1}{\sqrt{\left(1+x^{2}+y^{2}\right)^{3}}} d x d y \\
& =2 \int_{0}^{\pi / 4} \int_{0}^{1 / \cos \theta} r\left(1+r^{2}\right)^{-3 / 2} d r d \theta \\
& =\int_{0}^{\pi / 4} \int_{0}^{1 / \cos ^{2} \theta}(1+x)^{-3 / 2} \mathrm{~d} x \mathrm{~d} \theta \\
& =\int_{0}^{\pi / 4}(-2)\left[\left(1+\frac{1}{\cos ^{2} \theta}\right)^{-1 / 2}-1\right] \mathrm{d} \theta \\
& =2 \int_{0}^{\pi / 4} 1-\frac{\cos \theta}{\sqrt{1+\cos ^{2} \theta}} \mathrm{~d} \theta \\
& =\frac{\pi}{2}-2 \int_{0}^{1 / \sqrt{2}} \frac{1}{\sqrt{2-x^{2}}} \mathrm{~d} x \\
& =\frac{\pi}{2}-\left.2 \arcsin \left(\frac{x}{\sqrt{2}}\right)\right|_{0} ^{1 / \sqrt{2}} \\
& =\frac{\pi}{6}
\end{aligned}
$$

```
>> clear all
> f = (1+x^2_y^2)^(-3/2)'
    f = (1+x^2 - %
```

错误：文本字符无效。请检查不受支持的符号、不可见的字符或非 ASCII 字符的粘贴。

$$
\gg f=\left(1+x^{\wedge} 2+y^{\wedge} 2\right)^{\wedge}(-3 / 2) ;
$$

函数或变里＇ x ＇无法识别。

```
>> syms x y real
> f = (1+x^2+y^2)^(-3/2);
>> I=int(int(f,x,0,1),y,0,1);
>> I_simp = simplify(I)
```

I＿simp＝
pi／6
＞＞isAlways（I＿simp＝＝sym（pi／6））
ans＝
logical
1
$\underline{f_{\boldsymbol{x}}} \gg \mid$

Document

乐绎华，Yue Yihua

October 21， 2025

## Contents

口思考问题 1：计算 $\sqrt{2}$ 时，屏幕输出的是几位有效数字 （尝试使用命令format改变输出的格式），内存存储的又是几位有效数字？尝试使用sqrt（sym（2））作为真实值，观察误差。然后考虑 $\sqrt{979797}$ 观察误差。

```
>> sqrt(2)
ans =
    1.4142
>> format long
>> sqrt(2)
ans =
    1.414213562373095
>> format short
>> sqrt(2)
ans =
    1.4142
>> sqrt(sym(2))
ans =
2^(1/2)
>> error = abs(sqrt(sym(2))-sqrt(2))
error =
0
>> format long
>> error = abs(sqrt(sym(2))-sqrt(2))
x
```

```
    >> % 1. 计算双精度值 (计算值)
matlab_val = sqrt(2);
% 2. 计算符号精确值(真实值)
syms x
exact_val_sym = sqrt(sym(2));
% 将符号值转换为高精度小数(例如 30位)
vpa_precision = 30; % 设置 VPA 精度为 30 位
exact_val_vpa = vpa(exact_val_sym, vpa_precision);
% 3. 观察双精度值和精确值
fprintf('--- 计算根号2 ---\n');
fprintf('MATLAB双精度值(约16位): \t %.17f\n', matlab_val); % 显示17位小数
disp(['符号精确值 (VPA 30位): ' char(exact_val_vpa)]);
% 4. 计算绝对误差
% 绝对误差 = |计算值 - 真实值 |
% 为了计算误差,我们将符号精确值也截断为双精度进行比较 (或使用 VPA 误差)
error_val = abs(matlab_val - double(exact_val_vpa));
fprintf ('双精度计算的绝对误差 (与vPA比较):%.17e\n', error_val);
--- 计算根号2 ---
MATLAB双精度值 (约16位):1.41421356237309515
符号精确值 (VPA 30位):1.41421356237309504880168872421
双精度计算的绝对误差 (与VPA比较): 0.00000000000000000e+00
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-015.jpg?height=36&width=78&top_left_y=1258&top_left_x=464)

MATLAB 使用双精度浮点数（IEEE 754 标准），存储精度约为 52 位二进制尾数，对应十进制的精度约为：

$$
52 \times \log _{10}(2) \approx 52 \times 0.301 \approx 15.65
$$

故内存存储的精度约为 $15-16$ 位有效数字。

```
>> % 1. 计算双精度值 (计算值)
matlab_val_big = sqrt(979797);
% 2. 计算符号精确值 (真实值)
exact_val_sym_big = sqrt(sym(979797));
exact_val_vpa_big = vpa(exact_val_sym_big, vpa_precision);
% 3. 观察双精度值和精确值
fprintf('\n--- 计算根号979797 ---\n');
fprintf ('MATLAB双精度值 (约16位): \t %.17f\n', matlab_val_big);
disp(['符号精确值 (VPA 30位): ' char(exact_val_vpa_big)]);
% 4. 计算绝对误差
error_val_big = abs(matlab_val_big - double(exact_val_vpa_big));
fprintf ('双精度计算的绝对误差 (与VPA比较):%.17e\n', error_val_big);
--- 计算根号979797 ---
MATLAB双精度值 (约16位):989.84695786773022519
符号精确值 (VPA 30位):989.846957867730176922210985823
双精度计算的绝对误差 (与VPA比较): 0.00000000000000000e+00
```

口思考问题2：使用sym函数定义符号常量的时候，不用字符串无法录入长实数，用字符串做复杂运算会产生误差。那么如何不用字符串准确录入 0.123456789012345678901 ？

```
>> % 分子和分母作为符号整数定义
Numerator = sym(123456789012345678901);
Denominator = sym(1000000000000000000000); % 即 10^21
% 使用符号分数精确录入
% 关键: 分子和分母作为两个独立的、精确的符号整数被定义,然后执行符号除法
S_exact = Numerator / Denominator;
% 或者更简洁地直接构造:
% S_exact_alt = sym(123456789012345678901) / sym(10^21);
disp('精确录入的符号常量 s_exact 为分数形式:');
disp(S_exact);
% 验证精度(以30位精度显示):
disp('以30位精度验证:');
vpa(S_exact, 30)
精确录入的符号常量 s_exact 为分数形式:
3767602203745901/30517578125000000
以 30位精度验证:
ans =
0.123456789012345683968
fx >> |
```

□练习问题 1 ：在MATLAB中，输入 $1 / 0,-1 / 0,0 / 0$ 的结果分别是什么？

口练习问题2：求 $\arctan x$ 在 $\boldsymbol{x}=\mathbf{0}$ 处的十次泰勒展开？
□练习问题3：利用MATLAB符号运算计算幂级数的和

$$
\sum_{n=1}^{\infty} \frac{n+1}{n!} x^{n}
$$

□练习问题4：利用MATLAB符号运算计算积分

$$
\int_{-\infty}^{+\infty} e^{-x^{2}} d x
$$

```
>> 1/0
ans =
    Inf
>> -1/0
ans =
    -Inf
>> 0/0
ans =
    NaN
```

>> clear
>> syms
>> syms x
>> taylor(atan(x),x,0,'Order',10)
ans =
$x^{\wedge} 9 / 9-x^{\wedge} 7 / 7+x^{\wedge} 5 / 5-x^{\wedge} 3 / 3+x$

```
    >> syms n x;
    % 定义通项
    f_n = ((n + 1) / factorial(n)) * x^n;
    % 计算从 n=1 到无穷大的和
    S = symsum(f_n, n, 1, inf);
    >> S
    S =
    exp(x) + x*exp(x) - 1
fx >>
```

```
>> syms x;
% 定义被积函数
f = exp(-x^2);
% 计算从负无穷到正无穷的定积分
I = int(f, x, -inf, inf)
I =
pi^(1/2)
```

口大实验：设 $a_{n}=\left(1+\frac{1}{n}\right)^{n}, b_{\mathrm{n}}=\frac{n}{\sqrt[n]{n!}}, c_{n}=\sum_{k=0}^{n} \frac{1}{k!}, n \in \mathbb{N}_{+}$．
可以证明，三个数列都是收玫到常数 $\boldsymbol{e}$ 的数列．利用这两次课所学知识，尝试对三个序列的前 300 项的取值进行绘图（plot），并通过绘图结果分析到底哪一个数列更加快速的收敛到常数 $\mathbf{e}$ 。

口使用双精度数据进行运算可能会出现异常结果。

口尝试避免使用for循环，养成MATLAB的数组化编程习惯。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-020.jpg?height=546&width=1204&top_left_y=1130&top_left_x=459)

Note 0．1．这个图中出现跳跃的原因是 $170!\approx 7.257 \times 10^{306}$ ，这是双精度能够精确计算的最大阶乘。当 $n \geq 171$ 时，factorial（n）的结果会发生正溢出 （Overflow），MATLAB 会将其表示为 Inf．
$\%$ 大实验：比较三个收玫于常数 $e$ 的数列的收玫速度
$\%$（注意：此版本使用 MATLAB 默认的双精度浮点数，精度约为 $15-16$ 位）
clear；
clc；
$\%-0$ 。设置参数和常量 ——
$\mathrm{N}=300$ ；
$\mathrm{n} \_$values $=1: \mathrm{N}$ ；\％$n$ 的取值向量（double class）

```
% 机器常数 e 的双精度值(作为极限)
e_exact = exp(1);
disp ([, 常数 }\mp@subsup{\textrm{e}}{\sqcup}{}\mathrm{ 的双精度值 }\cup(\mathrm{ 约 }\cup1\mp@subsup{6}{\sqcup}{}\mathrm{ 位精度):']);
disp(e_exact);
fprintf('\n');
% - 1. 数组化计算三个数列的前 N 项 (使用双精度计算)--
% -- 数列 a_n ---
% a_n = (1 + 1/n) }\hat{n
% double + double ./ double -> double
a_n = (1 + 1 ./ n_values).^n_values;
% -- 数列 b_n ---
% b_n = n / nthroot (n!, n)
% 使用 gamma(n+1) 代替 n!,所有操作在 double 域内进行
b_n = n_values ./ (gamma(n_values + 1).^(1 ./ n__values));
% -- 数列 c__n (高效向量化计算)--
% c_n = sum__{k=0} }{n} 1/k
k_values = 0:N;
terms = 1 ./ factorial(k_values); % 计算 1/0!, 1/1!, ..., 1/N!
% 使用 cumsum 计算累加和 C__0, C_1, .., C_N
c_all = cumsum( terms);
% 截取从 到 n=N 的结果
c_n = c__all (2:N+1);
% - 2. 计算绝对误差 -
% Error_ X = abs ( }X-e_exact
Error_a = abs(a_n - e__exact);
Error_b = abs(b_n - e__exact);
Error_c = abs(c_n - e__exact);
% - 3. 绘图比较收敛速度——
% 图 1: 绝对误差的对数图,用于清晰比较收敛速度
figure('Name','收敛速度比较 (双精度)');
semilogy(n_values, Error_a, 'LineWidth', 2, 'DisplayName', '$ |a_n\sqcup_ve|$'); hold
semilogy(n_values, Error_b, 'LineWidth', 2, 'DisplayName', '$ |b_n_-_e | $');
```

```
semilogy(n_values, Error_c, 'LineWidth', 2, 'DisplayName', '$ |c_n_-_e | $');
title(' 三个数列收敛于 }\mp@subsup{\textrm{e}}{\sqcup}{}\mathrm{ 的绝对误差比较 (双精度)');
xlabel('$n$v(项数)','Interpreter','latex');
ylabel('绝对误差\sqcup$\left |S_n_~_e\right|$\sqcup(对数尺度)','Interpreter','latex');
legend('Location', 'southwest', 'Interpreter', 'latex', 'FontSize', 10);
grid on;
set(gca, 'FontSize', 12);
hold off;
% 图 2: 原始数列取值趋势
figure('Name','数列取值趋势 }\cup\mathrm{ (双精度)');
plot(n_values, a_n, 'LineWidth', 1.5, 'DisplayName', '$a_n$'); hold on;
plot(n_values, b_n, 'LineWidth', 1.5, 'DisplayName', '$b_n$');
plot(n_values, c_n, 'LineWidth', 1.5, 'DisplayName', '$c_n$');
% 绘制 e 的精确值作为参考线
yline(e_exact, 'r-','LineWidth',2,'DisplayName','$e$\sqcup(极限值)');
title(' 三个数列的取值 (双精度)');
xlabel('$n$\sqcup(项数)','Interpreter','latex');
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-022.jpg?height=46&width=1022&top_left_y=1375&top_left_x=459)

```
legend('Location', 'southeast', 'Interpreter', 'latex', 'FontSize', 10);
grid on;
set(gca, 'FontSize', 12);
hold off;
% - 4. 结论分析 (在命令行窗口输出)--
fprintf('\n——绘图结果分析\cup(基于双精度)u—— \n');
fprintf ('观察绝对误差对数图 (图 1):\n');
fprintf ('1.⿱数列 \sqcup$c_n$ 的误差在 }\sqcup$n$\sqcup\mathrm{ 较小时迅速下降,但在误差达到机器精度 }\sqcup$\\app
fprintf ('2. 数列 |$a_n$ 的误差曲线下降最慢(线性收敛)。\ n');
fprintf ('3. |数列 \sqcup $b_n $ 的收敛速度介于 }\cup$\textrm{a_n $ 和 }\leq$\textrm{c_n $ }\underset{~}{}\mathrm{ 之间。\ n');
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-022.jpg?height=50&width=1417&top_left_y=1899&top_left_x=459)

Document

乐绎华，Yue Yihua
November 17， 2025

## Contents

□实验 1 （附加课程 1 实例）：已知矩阵 $\boldsymbol{A} \in \mathbb{R}^{\mathbf{5 0 0} \times \mathbf{1 0 0 0}}$ 的秩为 $3, B=A+\epsilon, E \in \mathbb{R}^{500 \times 1000}$ 为噪声矩阵，其元素为服从 $N\left(\mathbf{0}, \mathbf{1 0}^{-\mathbf{4}}\right)$ 总体的样本。可以发现，因此 $A$ 与 $B$ 相差不大，但受到噪声的影响后，矩阵 $\boldsymbol{B}$ 为满秩矩阵。

□在假设仅知道 $\boldsymbol{B}$ ，不知道 $\boldsymbol{A}$ 的情况下，如何尽可能的去除噪声 $\boldsymbol{\epsilon}$ 并获得 $\boldsymbol{A}$ 的近似估计？通过读取＂Q1．mat＂获得原始矩阵 $\boldsymbol{A}$ 和 $\boldsymbol{B}$ 。（将文件复制到当前文件夹，再在窗□内双击，或用MATLAB命令load Q1即可打开）

实验2（附加课程1实例）：数据降维问题是现今非常流行的数据科学问题。现假设有 1000 个 500 维的列向量，组合成矩阵 $\boldsymbol{F}_{\mathbf{5 0 0} \times \mathbf{1 0 0 0}}$ 存储于文件＂Q2．mat＂中。其中这 1000 个向量有随机的 500 个属于一个三维欧氏子空间 $\boldsymbol{X}_{1}$ ，其余500个向量属于另外一个三维欧氏子空间 $\boldsymbol{X}_{2}$ ，但两个空间具体的向量分布未知。
容易证明，这 1000 个向量位于一个 6 维的子空间中，请设计一种算法，将这 1000 个 500 维向量转化为 6 维的＂降维表示＂。降维后的结果向量保存在矩阵 $\boldsymbol{G}_{\mathbf{6} \boldsymbol{\times} \mathbf{1 0 0 0}}$ 中。
设计一种算法，识别出哪 500 个向量属于 $\boldsymbol{X}_{1}$ ，哪 500 个向量属于 $\boldsymbol{X}_{2}$（分两组），分离两组 index后，用rank函数检验你的结果。

实验3（思路题）：现假设二维平面上有 100 个地点的坐标 $\left\{\left(\boldsymbol{x}_{\boldsymbol{i}}, \boldsymbol{y}_{\boldsymbol{i}}\right)\right\}_{1 \leq i \leq 100}$ ，对应地图上的 100 个地点，这些点都落在有界区域 $[0,1] \times[0,1]$ 内，它们的坐标 $\boldsymbol{F}_{100 \times 2}$ 存储于文件＂Q3．mat＂中。现在需要为这 100 个地点去设计若干个通讯基站，设计原则如下：
（1）第 $\boldsymbol{j}$ 个通讯基站的信号覆盖范围以基站位置（ $\boldsymbol{x}_{\boldsymbol{j}}^{*}, \boldsymbol{y}_{\boldsymbol{j}}^{*}$ ）为圆心（圆心未必是 100 个地点之一）， $\boldsymbol{\delta}_{\boldsymbol{j}}>\mathbf{0}$ 为半径的圆形及其内部。基站的信号强度 $\boldsymbol{\delta}_{\boldsymbol{j}}$ 可以任意大，但基站的建设成本与 $\delta_{j}^{2}$ 成正比。
（2）对于任意的一个地点 $\left(\boldsymbol{x}_{i}, \boldsymbol{y}_{i}\right)$ ，必须被至少一个基站的信号覆盖。
（3）尽可能降低基站建设的总成本。
（1）基于上述目标，如果仅允许修建一个通讯基站，如何设计？
（2）如果设计 10 个通讯基站，如何规划？
一种可行的思路：最小圆覆盖＋简单聚类

Q1：求 $B$ 的最佳 $k$ 秩近似，可以对 $B$ 进行 SVD 分解，保留前 $k$ 个最大的奇异值和对应的特征向量来获得。

$$
\mathbf{B}=\mathbf{U} \boldsymbol{\Sigma} \mathbf{V}^{\top}
$$

最佳 3 —秩近似 $\mathbf{A}_{3}$ ：

$$
\mathbf{A}_{3}=\mathbf{U}_{; 1: 3} \boldsymbol{\Sigma}_{1: 3,1: 3} \mathbf{V}_{; 1: 3}^{\top}
$$

```
>> load('Ql.mat')
>> [U, S, V] = svd(B);
>> target_rank = 3;
>> S_approx = zeros(size(S));
S_approx(1:target_rank, 1:target_rank) = S(1:target_rank, 1:target_rank);
>> A_approx = U * S_approx * V';
>> error_A = norm(A - A_approx, 'fro');
>> error_A = norm(A - A_approx, 'fro')
error_A =
    0.6722
>> error_AB = norm(A - B, 'fro')
error_AB =
    7.0721
```

Q2：降维后的 $\mathrm{G}_{6 \times 1000}$ 中，属于 $\mathrm{X}_{1}$ 的向量应接近 $\mathrm{X}_{1}$ 的 3 维基，属于 $\mathrm{X}_{2}$的向量应接近 $\mathrm{X}_{2}$ 的 3 维基。这是一个将 6 维数据点划分为两个 3 维子空间的问题，可以使用 $\mathrm{K}-$ Means 聚类或其他子空间聚类算法（如稀疏子空间聚类等）。由于 $\mathbf{X}_{1}$ 和 $\mathbf{X}_{2}$ 维度相同且数量相等（各 500 个）， $\mathrm{K}-\mathrm{Means}$ 聚类是一种简单可行的尝试。

```
>> load('Q2.mat')
>> r= rank(F)
r =
6
>> [U, S, V] = svd(F, 'econ');
>> U_basis = U(:, 1:r);
>> G = U_basis' * F;
>> K = 2;
>> [Clusters, ~, ~] = kmeans(G', K, 'MaxIter', 100);
>> index_X1 = find(Clusters == 1);
>> index_X2 = find(Clusters == 2);
>> F_X1 = F(:, index_X1);
F_X2 = F(:, index_X2);
>> rank_X1 = rank(F_X1);
rank_X2 = rank(F_X2);
>> rank_X1 = rank(F_X1)
rank_X2 = rank(F_X2)
rank_X1 =
3
rank_X2 =
3
```

```
>> load('Q2.mat')
>> r= rank(F)
r =
```

6

```
>> [U, S, V] = svd(F, 'econ');
>> U_basis = U(:, 1:r);
> G = U_basis' * F;
> K = 2;
>> [Clusters, ~, ~] = kmeans(G', K, 'MaxIter', 100);
>> index_X1 = find(Clusters == 1);
>> index_X2 = find(Clusters = 2);
>> F_X1 = F(:, index_X1);
F_X2 = F(:, index_X2);
>> rank_X1 = rank(F_X1);
rank_X2 = rank (F_X2);
>> rank_X1 = rank(F_X1)
rank_X2 = rank(F_X2)
rank_X1 =
```

3
rank＿X2＝

3
Q3：
Task：在二维平面上有 100 个地点，需设计通讯基站使其信号覆盖所有地点。目标是尽可能降低总成本（与半径 $\delta_{j}^{2}$ 成正比）

算法思路
基站建设的总成本 $C=\sum_{j} c \cdot \delta_{j}^{2}$ 。要最小化成本，就是要最小化 $\sum \delta_{j}^{2}$ 。
仅允许修建一个通讯基站（第一问）
如果只修建一个基站，它的覆盖圆必须包含所有 100 个地点。为了最小化 $\delta_{1}^{2}$ ，需要找到包含所有点的最小覆盖圆。

设计 10 个通讯基站（第二问）
如果设计 10 个基站，需要进行两步：
1．聚类：将 100 个地点分成 $K=10$ 个子集（聚类），每个子集对应一个基站的覆盖范围。
2．最小圆覆盖：对每个子集，求其对应的最小覆盖圆，圆心即为基站位置，半径 $\delta_{j}$ 即为最小覆盖圆的半径。
－聚类方法：可以使用 $K$－Means 聚类（ $\mathbf{x}_{i}, \mathbf{y}_{i}$ 坐标作为特征）。
－最小圆覆盖：这是一个经典的几何问题，有专门的算法（如 Welzl 算法），但对于本实验，了解其概念并使用近似方法或 Matlab 几何工具箱即可。

```
%% 实验3:基站优化布局 (最小圆覆盖+K-Means 聚类)
% 1.加载数据
try
    load Q3.mat;% 假设文件中包含矩阵 F(100x2),即[xi, yi]坐标
    disp('数据\sqcupQ3.mat\sqcup加载成功。');
catch
    disp('错误:无法加载\sqcupQ3.mat\lrcorner文件。请确保文件在当前文件夹中。');
    return;
end
% 2.问题 (1):仅允许修建一个通讯基站
% 相当于求所有 100 个点的最小覆盖圆
% 注意:Matlab/Octave 基础库中没有内置的最小圆覆盖函数。
% 以下使用近似方法或假设存在一个 'MinCircumCircle'函数。
% 一一 最小圆覆盖 - 概念演示 (此部分需自行实现或查找第三方库) --
% 假设 MinCircumCircle(Points)返回 [Center_x, Center_y,Radius]
% [center_1, radius_1] = MinCircumCircle (F);
% 以下使用近似方法: 取最远点对的圆心作为近似圆心
\mathrm { P } = \mathrm { F } ;
D_sq = sum((P(1,:)-P(2,:)).^2);% 初始化距离平方
idx_A = 1; idx_B = 2;
for i = 1:size (P, 1)
    for j = i+1:size(P,1)
        dist_sq = sum((P(i,:)-P(j,:)).^2);
        if dist_sq > D_sq
            D_sq = dist_sq;
            idx_A = i;
            idx_B = j ;
        end
    end
end
% 以最远点对的中点为圆心, 一半距离为半径作为近似
center_1_approx = (P(idx_A,:)+P(idx_B,:))/2;
radius__1_approx = sqrt(D_sq) / 2;
disp('-_仅一个基站__');
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-027.jpg?height=46&width=1245&top_left_y=2217&top_left_x=459)

```
disp (['近似最小覆盖半径\sqcupdelta:⿱丆,,num2str(radius_1_approx)]);
disp (['近似最小成本 (与 }\cup\mathrm{ delta^ 2 }\sqcup\mathrm{ 成正比):⿱丆,, num2str(radius_ 1_approx }\mp@subsup{}{}{\wedge}2)]\mathrm{ );
```

```
% 3.问题 (2):设计 10个通讯基站 (K-Means 聚类 + 最小圆覆盖)
K=10; % 基站数量
disp(['\n——设计 ',, num2str(K),'\sqcup个基站 (K-Means⿱十二最小圆覆盖)~_']);
% a.K-Means 聚类
% F (100x2) 的每一行是一个数据点,直接聚类
[Clusters, C] = kmeans(F, K, 'MaxIter', 100);% C 是聚类中心 (10x2)
disp( 'K-Meansu聚类完成。开始计算每个聚类的最小覆盖圆...');
% b. 对每个聚类计算其最小覆盖圆
Total_Cost_Sq = 0; % 总成本平方和(与总成本成正比)
figure;
hold on;
title (['10 ' 个基站的规划结果 (K-Means)']);
xlabel('x\cup坐标');
ylabel('y 坐标');
colors = lines(K); % 获取 K 种不同的颜色
for j = 1:K
    % 获取第 j 个聚类的点集
    Points_j = F(Clusters = j, :);
    if isempty(Points_j)
        continue;
    end
    % —— 对聚类 j 进行最小圆覆盖 (仍使用近似方法)——
    % 找到这个聚类中最远点对
    P_j = Points_j;
    D_sq_j = 0;
    idx_A_j = 1; idx_B_j = 1;
    if size (P_j, 1) > 1
        for i = 1:size(P_j, 1)
            for k = i +1:size (P_j, 1)
                dist_sq = sum((P_j(i,:)-P_j(k,:)).^2);
                if dist_sq > D__sq_j
                    D_sq_j = dist_sq;
                    idx_A_j = i ;
                    idx_B_j = k;
                end
            end
        end
        center_j_approx = (P_j(idx_A_j,:) + P_j(idx_B_j,:)) / 2;
```

```
        radius_j_approx = sqrt(D_sq_j) / 2;
    else % 单个点的情况
        center_j__approx = P_j;
        radius_j_approx = 0;
    end
    % 计算总成本平方和
    Total_Cost__Sq = Total_Cost_Sq + radius_j_approx^2;
    % c. 可视化结果 (分颜色展示)
    scatter(Points_j(:, 1), Points_j(:, 2), 50, colors(j, :), 'filled'); % 绘制地
    % 绘制近似基站位置
    plot(center_j_approx(1), center_j_approx(2), 'p', 'MarkerSize', 10, 'MarkerF
    % 绘制近似覆盖圆 (需要 plot_circle 函数,这里只展示参数)
    % plot_circle(center_j_approx, radius_j_approx, colors(j, :));
    disp(['基站\sqcup', num2str(j), ' - |半径 }\cup\textrm{delta:⿱丆贝, num2str(radius_j_approx),...
            ,,位置\sqcup(x*,⿱口 *):⿱丆,,num2str(center_j_approx)]);
end
disp (['\n10\cup个基站规划的总成本平方和\cup(与总成本成正比):⿱', num2str(Total_Cost_Sq)
hold off;
% 最小化 Total_Cost_Sq 即为优化目标
% 注意:要实现准确的最小圆覆盖,需要专业的几何算法库。
```

```
数据 Q3.mat 加载成功.
--- 仅一个基站 ---
近似基站位置(x*, y*):0.46544 0.51406
近似最小覆盖半径 delta: 0.59065
近似最小成本 (与 delta^2 成正比): 0.34887
\n--- 设计 10 个基站 (K-Means + 最小圆覆盖) ---
K-Means 㹂类完成。开始计算每个聚类的最小覆盖圆...
基站 1 - 半径 delta: 0.091145, 位置(x*, y*): 0.6051 0.55376
基站 2 - 半径 delta: 0.15159, 位置 (x*, y*): 0.83767 0.4084
基站 3 - 半径 delta: 0.13904, 位置(x*, y*): 0.60664 0.1294
基站 4 - 半径 delta: 0.1673, 位置(x*, y*): 0.17215 0.56879
基站 5 - 半径 delta: 0.17281, 位置 (x*, y*): 0.19337 0.1412
基站 6-半径 delta: 0.1093, 位置(x*, y*): 0.28213 0.8661
基站 7 - 半径 delta: 0.031096, 位置 (x*, y*): 0.8811 0.01757
基站 8 - 半径 delta: 0.13088, 位置 (x*, y*): 0.44711 0.367
基站 9 - 半径 delta: 0.19888, 位置 (x*, y*): 0.75984 0.74263
基站 10 - 半径 delta: 0.10973, 位置 (x*, y*): 0.4032 0.64619
\n10 个基站规划的总成本平方和(与总成本成正比): 0.19011
>>
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-030.jpg?height=1011&width=1199&top_left_y=1250&top_left_x=464)

Document

乐绎华，Yue Yihua
October 16， 2025

## Contents

0．0．1（3）傅里叶变换在信号滤波中的应用验证 ..... 6

## 第三四周电子版作业

□ Q1．在 $[0,2 \pi]$ 区间，画出变上限积分函数 $y(x)=\int_{0}^{x} \frac{\sin t}{t} \mathrm{~d} t$ 的曲线，并计算 $\boldsymbol{y}(\mathbf{4 . 5})$ 。
□ Q2．不用字符串表达式调用dsolve函数，解决下列微分方程的初值问题，并利用符号运算进行回代检验解是否正确。

$$
x y^{\prime \prime}-3 y^{\prime}=x^{2}, y(1)=0, y(5)=0
$$

□ Q3．用MATLAB符号运算验证拉普拉斯变换的时域导数性质：

$$
L\left[\frac{\mathrm{~d} f(t)}{d t}\right]=s \cdot L[f(t)]-f(0)
$$

□ Q4．用MATLAB函数vpa显示 $\pi$ 的前 30 位有效数字，然后再用该函数显示的 $\boldsymbol{\pi}$ 前 31 位有效数字，为何两个结果完全相同？

## 第三四周电子版作业

Q5．（附加题，选做）利用课程与课外资料学习三大变换的相关性质（本题页数不建议超过 6 页（五号字））
（1）设 $\boldsymbol{f}(\boldsymbol{t}), \boldsymbol{g}(\boldsymbol{t})$ 为某些未知的 sym函数，尝试通过通过 MATLAB符号运算验证连续傅里叶变换的下列性质：
1．平移性质： $\mathcal{F}(\boldsymbol{f}(\boldsymbol{t}-\boldsymbol{a}))=\mathcal{F}(\boldsymbol{f}(\boldsymbol{t})) \cdot \mathbf{e}^{-\boldsymbol{j} \omega \boldsymbol{a}}$
2．导数性质： $\mathcal{F}\left(\boldsymbol{f}^{\prime}(\boldsymbol{t})\right)=\mathcal{F}(\boldsymbol{f}(\boldsymbol{t})) \cdot \boldsymbol{i} \boldsymbol{\omega}$
3．卷积性质： $\mathcal{F}(\boldsymbol{f}(\boldsymbol{t}) * \boldsymbol{g}(\boldsymbol{t}))=\mathcal{F}\left(\int_{-\infty}^{\infty} \boldsymbol{f}(\boldsymbol{\tau}) \boldsymbol{g}(\boldsymbol{t}-\boldsymbol{\tau}) \mathrm{d} \boldsymbol{\tau}\right)= \mathcal{F}(\boldsymbol{f}(\boldsymbol{t})) \cdot \mathcal{F}(\boldsymbol{g}(\boldsymbol{t}))$
（2）简单阅读相关资料后，你认为三大变换定义的区别和联系是什么？
（3）选择三大变换的其中一个其他应用，进行课外学习并尽可能通过MATLAB来验证三大变换的有效性。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-032.jpg?height=729&width=1204&top_left_y=1433&top_left_x=459)

```
>> clear
>> format compact
syms $x y(x)$
\% 重新求解
sol = dsolve( $\left.x^{\star} \operatorname{diff}(y(x), x, 2)-3^{\star} \operatorname{diff}(y(x), x)==x^{\wedge} 2, y(1)==0, y(5)==0\right)$;
disp('Solution:'), disp(sol)
\% 定义解
y = sol;
\% 计算导数
dy_dx = diff(y, x);
d2y_dx2 = diff(y, x, 2);
\% 代入原方程
left_side $=\mathrm{x}^{*} \mathrm{~d} 2 \mathrm{y} \_\mathrm{dx} 2-3^{*} \mathrm{dy} \_\mathrm{dx}$;
right_side = $\mathrm{x}^{\wedge} 2$;
\% 化简差值
simplify(left_side - right_side)
Solution:
$\left(31^{*} x^{\wedge} 4\right) / 468-x^{\wedge} 3 / 3+125 / 468$
ans =
0
>> |
```

```
>> clear
>>% 验证拉普拉斯变换时域导数性质: L[df(t)/dt] = s* L [f(t)] - f(0)
format compact
syms t s
syms f(t) % 定义符号函数 f (t)
% 定义 f(t) 的例子,例如 f(t) = e^(-t)
f_t = exp(-t);
f_0 = subs(f_t, t, 0); % 计算 f(0)
% 计算 f(t) 的拉普拉斯变换 L[f(t)]
L_f = laplace(f_t, t, s);
% 计算 f(t) 的一阶导数
df_dt = diff(f_t, t);
% 计算 df(t)/dt 的拉普拉斯变换 L[df(t)/dt]
L_df = laplace(df_dt, t, s);
% 验证性质: s*L[f(t)] -f(0) 是否等于 L[df(t)/dt]
left_side = s * L_f - f_0;
right_side = L_df;
% 化简并比较
simplify(left_side - right_side)
ans =
0
```

    >> clear
    >> format compact
    digits(30); \% 设置精度为 30 位
    $\mathrm{pi} \_30=\mathrm{vpa}(\mathrm{pi}, ~ 30)$; \% 显示前 30 位有效数字
    disp('п (30 digits):'), disp(pi_30)
    digits(31); \% 设置精度为 31 位
    $\mathrm{pi} \_31=\mathrm{vpa}(\mathrm{pi}, ~ 31)$; \% 显示前 31 位有效数字
    disp('п (31 digits):'), disp(pi_31)
    п (30 digits):
    3.14159265358979323846264338328
    п (31 digits) :
    3.14159265358979323846264338328
    $\boldsymbol{f} \boldsymbol{x} \boldsymbol{\gg}$

```
>> %% 验证连续傅里叶变换的性质
format compact
syms t omega tau a
syms f(t) g(t) % 定义符号函数 f(t) 和 g(t)
% 选择具体函数,例如 }f(t)=\mp@subsup{e}{}{\wedge}(-t)*\mathrm{ heaviside (t), g(t) = e^(-2t)*heaviside(t)
f_t = exp(-t) * heaviside(t);
g_t = exp(-2*t) * heaviside(t);
% (1) 平移性质: }F(f(t-a))=F(f(t)) * \mp@subsup{e}{}{\wedge}(-j*omega*a
f_shift = subs(f_t, t, t - a); % f(t-a)
F_f = fourier(f_t, t, omega); % F(f(t))
F_f_shift = fourier(f_shift, t, omega); % F(f(t-a))
right_side1 = F_f * exp(-1i * omega * a); % F(f(t)) * e^(-j*omega*a)
simplify(F_f_shift - right_side1) % 应为0
% (2) 导数性质: F(f'(t)) = F(f(t)) * i*omega
df_dt = diff(f_t, t); % f'(t)
F_df = fourier(df_dt, t, omega); % F(f'(t))
right_side2 = F_f * 1i * omega; % F(f(t)) * i*omega
simplify(F_df - right_side2) % 应为0
% (3) 卷积性质: F(f(t)*g(t)) = F(f(t)) * F(g(t))
% 定义卷积 (注意MATLAB符号积分限制,手动近似)
conv_fg = int(f_t * subs(g_t, t, tau - t), t, -inf, inf); % 卷积积分
F_conv = fourier(conv_fg, tau, omega); % F(f*g)
F_g = fourier(g_t, t, omega); % F(g(t))
right_side3 = F_f * F_g; %F(f(t)) * F(g(t))
simplify(F_conv - right_side3) % 应为0 (可能需数值验证)
ans =
0
ans =
0
ans =
0
```

根据课外资料，三大变换（拉普拉斯变换、傅里叶变换、 Z 变换）定义与联系如下：

- 定义区别：
- 拉普拉斯变换：$F(s)=\int_{-\infty}^{\infty} f(t) e^{-s t} d t, s=\sigma+j \omega$ ，适用于时域信号的广义频域分析，$\sigma$ 提供收敛性。
－傅里叶变换：$F(\omega)=\int_{-\infty}^{\infty} f(t) e^{-j \omega t} d t$ ，特例为 $s=j \omega$（纯虚数），聚焦于频率成分。
-Z 变换：$X(z)=\sum_{n=-\infty}^{\infty} x[n] z^{-n}$ ，离散时间信号的 $z-$ 域表示， $z=r e^{j \theta}$ 。
- 联系：
- 数学关系：拉普拉斯变换是傅里叶变换的推广，当 $\sigma=0$ 时，拉普拉斯变换退化为傅里叶变换。Z 变换是离散系统的拉普拉斯变换类比。
－应用场景：拉普拉斯用于控制系统稳定性，傅里叶用于信号频谱分析，Z 变换用于数字信号处理。
－共性：三者都将时域／序列域映射到复数域，方便分析线性时不变系统。


## 0．0．1（3）傅里叶变换在信号滤波中的应用验证

应用背景 傅里叶变换可分解信号为频率成分，用于设计滤波器去除噪声。选择低通滤波为例，滤除高频噪声。

# 23363017 乐绎华第四次实验 

乐绎华，Yue Yihua， 23363017
December 16， 2025

## Contents

1 Q 1 唯一解的情况 2
2 Q 2 无穷多解的情况 3
3 Q 3 无解的情况 4

□ 思考问题 1：利用课本第四章习题的 $9,10,11$ 题，观察线性方程组在唯一解、无穷多解、无解的情况下， rref，inv，、分别会返回什么结果，同时学习函数 pinv所对应的MP伪逆的定义与应用。

9．求矩阵 $\mathbf{A x}=\mathbf{b}$ 的解， A 为 3 阶魔方阵， b 是（ $3 \times 1$ ）的全 1 列向量。（提示：用rref，inv，$/$ 体验。）。
10．求矩阵 $\mathbf{A x}=\mathbf{b}$ 的解， A 为 4 阶魔方阵， b 是（ $4 \times 1$ ）的全 1 列向量。（提示：用 rref，inv，$/$ 体验。）。
11．求矩阵 $\mathbf{A x}=\mathbf{b}$ 的解， A 为 4 阶魔方阵， $\mathbf{b}=\left[\begin{array}{l}1 \\ 2 \\ 3 \\ 4\end{array}\right]$ 。（提示：用 ref，inv，／体验。）

## 1 Q 1唯一解的情况

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-038.jpg?height=753&width=1204&top_left_y=560&top_left_x=459)

```
A9 = magic(3);
b9 = ones(3, 1);
fprintf('Rank(A) = %d, Det(A) = %.4f \ n', rank(A9), det(A9));
disp('RREF([A b]):');
disp(rref([A9, b9]));
disp('x_inv = inv(A)*b:');
disp(inv(A9) * b9);
disp('x_slash = A\b:');
disp(A9 \ b9);
disp('x_pinv = pinv(A)*b:');
disp(pinv(A9) * b9);
```


## 2 Q2无穷多解的情况

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-039.jpg?height=736&width=1204&top_left_y=560&top_left_x=459)
pinv 结果

```
    ans =
        0.0294
        0.0294
        0.0294
        0.0294
..
```

```
A10 = magic(4);
b10 = ones(4, 1);
fprintf('Rank(A) = %d, Det(A) = %.4f \ n', rank(A10), det(A10));
% 检查相容性: Rank(A) vs Rank([A b])
fprintf('Rank([A b]) = %d\n', rank([A10, b10]));
disp('RREF([A b]):');
```

```
disp(rref([A10, b10]));
inv (A10)
x = A10\b10
pinv(A10) * b10
```


## 3 Q 3 无解的情况

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-040.jpg?height=738&width=1204&top_left_y=936&top_left_x=459)
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-041.jpg?height=736&width=1202&top_left_y=429&top_left_x=459)

```
A11 = magic (4);
$\mathrm{b} 11=[1 ; 2 ; 3 ; 4]$;
fprintf $\left({ }^{\prime} \operatorname{Rank}(\mathrm{A}) \sqcup=\left\llcorner \% \mathrm{~d},\left\llcorner\operatorname{Rank}\left(\left[\mathrm{~A}_{\sqcup} \mathrm{b}\right]\right)\left\llcorner=\left\llcorner \% \mathrm{~d} \backslash \mathrm{n}^{\prime}, \operatorname{rank}(\mathrm{A} 11), \operatorname{rank}([\mathrm{A} 11, \mathrm{~b} 11])\right) ;\right.\right.\right.\right.$
disp ( 'RREF ([ $\mathrm{A} \sqcup \mathrm{b}$ ]):' );
rref([A11, b11])
disp (' inv (A11)' );
inv (A11)
disp ( 'A11」\பb11' );
A11 \ b11
disp('pinv(A11)')
pinv (A11)
```


## Document

乐绎华，Yue Yihua

October 29， 2025

## Contents

## 第五六周电子版作业

## $\square Q 1$ ．习题3第3题

由指令 $\operatorname{rng}($＇default＇$), \mathrm{A}=\operatorname{rand}(3,5)$ 生成二维数组 A ，试求该数组中所有大于 0.5 的元素的位置，分别求出它们的＂全下标＂和＂单下标＂。
□ Q2．习题3第7题（仿照例题3．3－1完成）
先运行指令 $\mathrm{x}=-3 * \mathrm{pi}: \mathrm{pi} / 15: 3 * \mathrm{pi} ; \mathrm{y}=\mathrm{x} ;[\mathrm{X}, \mathrm{Y}]=\operatorname{mesh} \operatorname{grid}(\mathrm{x}, \mathrm{y}) ;$ warning off； $\mathrm{Z}=\sin (\mathrm{X}) . * \sin (\mathrm{Y}) . / \mathrm{X} . / \mathrm{Y}$ ；产生矩阵 Z 。（1）请问矩阵Z中有多少个＂非数＂数据？（2）用指令 $\operatorname{surf}(\mathrm{X}, \mathrm{Y}, \mathrm{Z})$ ；shading interp 观察所绘的图形。（3）请写出绘制相应的＂无裂缝＂图形的全部指令。（提示：isnan 用于判断是否非数；可借助 sum 求和；realmin 是最小正数。）
□ Q3．线性方程组问题可以通过高等代数中所学习的初等变换法解决，也可以通过（按列选主元的）高斯消去法解决。容易得知，这些算法复杂度均为 $\boldsymbol{O}\left(\boldsymbol{n}^{3}\right)$ ，3层循环的代码效率很低。
－设方阵A可逆，利用MATLAB的数组化运算，尝试以尽量少的循环层数完成初等变换法或（选主元的）高斯消去法。然后用下列代码生成的 A 与 b ，解出 $\mathrm{A} \mathrm{x}=\mathrm{b}$ 的向量解（无需粘贴解），并与 MATLAB函数 $\mathrm{c}=\mathrm{A} \backslash \mathrm{b}$ 得到的解（这个也不精确）进行误差分析（函数norm（b－b2）可以计算向量 b 与 b 2 之间的2－范数差距）
rng default， $\mathrm{A}=$ rand $(1000) ; \mathrm{A}(1,1)=0 ; \mathrm{b}=$ rand $(1000,1)$ ；

```
>> rng('default');
A = r a n d ( 3 , 5 )
A =

\begin{tabular}{lllll}
0.8147 & 0.9134 & 0.2785 & 0.9649 & 0.9572 \\
0.9058 & 0.6324 & 0.5469 & 0.1576 & 0.4854 \\
0.1270 & 0.0975 & 0.9575 & 0.9706 & 0.8003
\end{tabular}
>> [idx_row, idx_col] = find(A > 0.5);
>> full_indices = [idx_row, idx_col]
full_indices =
\begin{array} { l l } { 1 } & { 1 } \\ { 2 } & { 1 } \\ { 1 } & { 2 } \\ { 2 } & { 2 } \\ { 2 } & { 3 } \\ { 3 } & { 3 } \\ { 1 } & { 4 } \\ { 3 } & { 4 } \\ { 1 } & { 5 } \\ { 3 } & { 5 } \end{array}
>> linear_indices = sub2ind(size(A), idx_row, idx_col);
>> [~, ~, linear_indices] = find(A > 0.5)
linear_indices =
    10 x l logical 数组
    1
    1
    1
    1
    1
    1
    l
>> linear_indices = sub2ind(size(A), idx_row, idx_col)
linear_indices =
    1
    4}5
    9
    10
    13}15 1.01
>>
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-044.jpg?height=515&width=1200&top_left_y=429&top_left_x=461)
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-044.jpg?height=453&width=1197&top_left_y=1069&top_left_x=464)

编辑器－C：\Users\28024\Documents\MATLAB\gepp＿vectorized．m
gepp＿vectorized．m $\times$＋

| $1 \square$ <br> 2 <br> 3 <br> 4 <br> 5 <br> $6 \square$ <br> 7 <br> 8 <br> 9 <br> 10 <br> 11 <br> 12 <br> 13 <br> 14 <br> 15 <br> 16 <br> 17 <br> 18 <br> 19 <br> 20 <br> 21 <br> 22 <br> 23 <br> 24 <br> 25 <br> － <br> 26 <br> 27 <br> 28 | function x＝gepp＿vectorized（A，b） n = size(A, 1); Ab = [A, b]; % 增广矩阵 [A\|\|] <br> \％＝＝＝前向消元：仅 1 层主循环＝＝＝ <br> for $\mathrm{k}=1: \mathrm{n}-1$ <br> \％1．列主元选择（从 $k$ 行到 $n$ 行，$k$ 列找最大绝对值） <br> ［ $\sim$ ，pivot＿row］＝max（abs（Ab（k：n，k）））； <br> pivot＿row＝pivot＿row＋k－1；\％调整索引 <br> \％2．行交换 <br> if pivot＿row～＝k <br> $\mathrm{Ab}([\mathrm{k}$, pivot＿row］，：$)=\mathrm{Ab}([$ pivot＿row，k］，：$)$ ； <br> end <br> $\% 3$ ．向里化消元（对 $k+1$ 到 $n$ 行） <br> rows＿below＝k＋1：n； <br> factor $=\mathrm{Ab}($ rows＿below，k ）／Ab（k，k）； <br> \％列向里 <br> Ab （rows＿below，k：end）$=\mathrm{Ab}$（rows＿below，k：end）－．．． <br> factor＊ $\mathrm{Ab}(\mathrm{k}, \mathrm{k}$ ：end）；\％向里化更新 <br> end <br> \％＝＝＝回代求解＝＝＝ <br> $\mathrm{x}=\operatorname{zeros}(\mathrm{n}, 1)$ ； <br> for $i=n:-1: 1$ <br> $x(i)=(A b(i$, end $)-A b(i, i+1: n)$＊$x(i+1: n)) / A b(i, i) ;$ <br> end <br> end |  |
| :--- | :--- | :--- |

```
>> clear
>> rng default;
A = rand(1000);
A(1,1) = 0;
b = rand(1000,1);
% 测试你的函数
tic;
xl = gepp_vectorized(A, b);
tl = toc;
% MATLAB 内置解
tic;
x2 = A \ b;
t2 = toc;
% 误差分析
err = norm(x1 - x2);
rel_err = norm(x1 - x2) / norm(x2);
residual = norm(A*xl - b);
fprintf('=== 误差分析 (n=1000) ===\n');
fprintf('||xl - x2||_2 = %.2e\n', err);
fprintf('相对误差 = %.2e\n', rel_err);
fprintf('残差 ||Axl-b||_2 = %.2e\n', residual);
fprintf('GEPP 时间 = %.4f 秒\n', t1);
fprintf('MATLAB \\ 时间 = %.4f 秒\n', t2);
=== 误差分析 (n=1000) ===
||x| -x2||_2 = 7.30e-08
相对误差 = 1.88e-11
残差 ||Axl-b||_2 = 3.95e-10
GEPP 时间 = 1.6838 秒
MATLAB \ 时间 = 0.0139 秒
>>
```


## Document

乐绎华，Yue Yihua

November 5， 2025

## Contents

## 第七周电子版作业

－这次一共只有两道题（－）（－）（－）
□ Q1．某年春节，数院传奇D神希望为朋友圈点赞的朋友发红包。他表示，点赞序数为素数的朋友将获得红包。但点赞朋友共有 360 人，D神发现逐个手算这些素数很费时间，而且容易出错。同时，D神的豪华手机朋友圈每行可以显示 9 名好友，他希望能够利用程序自动显示出获得红包的好友行数与列数。
－现需要你设计算法效率尽量高（降低复杂度，减少循环层数）的一个MATLAB程序，找出 $1^{\sim} 360$ 的所有素数，并且用下列格式显示获得红包的好友：
第 1 位获得红包好友为第 2 号好友，位于第 1 行第 2 列。
□ 请在作业中写明你的算法思路、MATLAB代码，以及你屏幕所输出的所有红包获奖结果。禁用primes与isprime函数。禁止纯手算解决问题。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-048.jpg?height=725&width=1204&top_left_y=425&top_left_x=459)
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-048.jpg?height=723&width=1202&top_left_y=1282&top_left_x=459)

算法选择：为了满足题目中＂算法效率尽量高（降低复杂度，减少循环层数）＂的要求，并规避使用primes和isprime函数，我们采用埃拉托斯特尼筛法（Sieve of Eratosthenes），也称为＂素数筛＂。

## 思路详解：

1．初始化：创建一个大小为 360 的逻辑（布尔）数组，记为isPrime，并将所

## 有元素初始化为true。这个数组的索引 i 代表数字 i，isPrime（i）的值表示 i 是否为素数。

## 2．处理非素数：

- 我们知道 1 不是素数，所以首先将 isPrime（1）设为 false。
- 从第一个素数 2 开始遍历。


## 3．筛法核心：

- 从 $\mathrm{p}=2$ 开始，遍历到 $\operatorname{sqrt}(360) ~($ 约等于 18.97 ，取整为 18）即可。
- 在循环中，如果 isPrime（ p ）仍然为 true，说明 p 是一个素数。
- 这时，我们需要将 p 的所有倍数（这些数不可能是素数）在 isPrime数组中标记为 false。
－效率优化：我们不需要从 $2 * \mathrm{p}$ 开始标记，因为 $2 * \mathrm{p} 、 3 * \mathrm{p} \ldots(\mathrm{p}-1) * \mathrm{p}$ 必定在之前的循环中（例如，当遍历到 2 或 3 时）已经被标记过了。我们直接从 $p * p$ 开始，然后以 $p$ 为步长，标记 $p * p, p * p+p, p * p+2 p$ ， ．．．直到超过 360 。


## 4．结果统计与输出：

－完成上述筛选后，isPrime 数组中所有值为 true 的索引 i 对应的数字 i 就是 1 到 360 之间的所有素数。
－我们设置一个计数器 primeCount，用于记录这是第几位获得红包的好友。

- 遍历 1 到 360，当 isPrime（i）为 true 时：
- primeCount 加1。
- 计算好友 i 所在的行（R）和列（C）：

$$
\text { * 行 } \mathrm{R}=\operatorname{floor}((\mathrm{i}-1) / 9)+1 \quad \text { (或 } \operatorname{ceil}(\mathrm{i} / 9))
$$

＊列 $\mathrm{C}=\bmod (\mathrm{i}-1,9)+1$
－按照题目要求的格式化字符串，输出结果。

```
% D神发红包 - 第七周电子版作业
% 日期:2025年11月5日
function seventhWeekHomework()
% - 1. 初始化变量 --
N = 360; % 总好友数
cols = 9; % 朋友圈每行显示好友数
% - 2. 算法思路:埃拉托斯特尼筛法 (Sieve of Eratosthenes) --
% 创建一个逻辑数组,默认所有数字 (1-N) 都 "是" 素数
isPrime = true(1,N);
```

```
% 1 不是素数
isPrime(1) = false;
% 筛法核心:遍历到 sqrt(N)即可
for p = 2:floor(sqrt(N))
% 如果 p 仍然是素数 (未被标记为 false)
if isPrime(p)
% 将 p 的所有倍数(从 p*p 开始)标记为非素数(false)
% 示例: p=2时,标记 4, 6, 8...
% p=3时, 标记 9, 12, 15...
% p=5时, 标记 25, 30, 35...
isPrime(p*p : p : N) = false;
end
end
% - 3. 遍历结果并按格式输出——
fprintf('作业要求:找出1~360的所有素数,并计算好友行列。\n');
fprintf('禁止使用\sqcupprimes⿱和 isprime 函数。\n');
fprintf('. \n\n');
primeCount = 0; % 计数器, 记录这是第几位获得红包的好友
% 遍历 1 到 360
for i = 1:N
% 如果 isPrime (i) 为 true,说明 i 是素数
if isPrime(i)
```

```
% 获得红包好友计数+1
primeCount = primeCount + 1;
% 计算所在的行 (R) 和 列 (C)
% 第 i 号好友,索引为 i-1 (从 0 开始计数)
% 行 R= 向下取整 ((i-1)/ 9) + 1
R = floor ((i - 1) / cols) + 1;
% 列 C=(i-1) 除以 g 的余数 + 1
C = mod(i - 1, cols) + 1;
% 打印获奖结果
fprintf ('第%d位获得红包好友为第%d号好友,位于第%d行第%d列。\n', primeCount, i,R
end
end
fprintf('\n——报告:总共有 }\leftarrow%\mp@subsup{\textrm{d}}{\llcorner}{}\mathrm{ 位好友获得红包。 }\leftarrow\mathrm{ — \n', primeCount);
end
% -- 要运行此代码, 请在 MATLAB 命令窗口中调用:---
% seventh WeekHomework()
>> seventhWeekHomework()
作业要求:找出1~360的所有素数,并计算好友行列。
禁止使用 primes 和 isprime 函数。
```

第 1 位获得红包好友为第 2 号好友，位于第 1 行第 2 列。
第 2 位获得红包好友为第 3 号好友，位于第 1 行第 3 列。
第 3 位获得红包好友为第 5 号好友，位于第 1 行第 5 列。
第 4 位获得红包好友为第 7 号好友，位于第 1 行第 7 列。
第 5 位获得红包好友为第 11 号好友，位于第 2 行第 2 列。
第 6 位获得红包好友为第 13 号好友，位于第 2 行第 4 列。
第 7 位获得红包好友为第 17 号好友，位于第 2 行第 8 列。

第 8 位获得红包好友为第 19 号好友，位于第 3 行第 1 列。第 9 位获得红包好友为第 23 号好友，位于第 3 行第 5 列。第 10 位获得红包好友为第 29 号好友，位于第4行第2列。第 11 位获得红包好友为第 31 号好友，位于第4行第4列。第 12 位获得红包好友为第 37 号好友，位于第 5 行第 1 列。第 13 位获得红包好友为第 41 号好友，位于第 5 行第 5 列。第 14 位获得红包好友为第 43 号好友，位于第 5 行第 7 列。第 15 位获得红包好友为第 47 号好友，位于第 6 行第 2 列。第 16 位获得红包好友为第 53 号好友，位于第 6 行第 8 列。第 17 位获得红包好友为第 59 号好友，位于第 7 行第 5 列。第 18 位获得红包好友为第 61 号好友，位于第 7 行第 7 列。第 19 位获得红包好友为第 67 号好友，位于第 8 行第 4 列。第 20 位获得红包好友为第 71 号好友，位于第 8 行第 8 列。第 21 位获得红包好友为第 73 号好友，位于第 9 行第 1 列。第 22 位获得红包好友为第 79 号好友，位于第 9 行第 7 列。第 23 位获得红包好友为第 83 号好友，位于第 10 行第 2 列。第 24 位获得红包好友为第 89 号好友，位于第 10 行第 8 列。第 25 位获得红包好友为第 97 号好友，位于第 11 行第 7 列。第 26 位获得红包好友为第 101 号好友，位于第 12 行第 2 列。第 27 位获得红包好友为第 103 号好友，位于第 12 行第 4 列。第 28 位获得红包好友为第 107 号好友，位于第 12 行第 8 列。第 29 位获得红包好友为第 109 号好友，位于第 13 行第 1 列。第 30 位获得红包好友为第 113 号好友，位于第 13 行第 5 列。第 31 位获得红包好友为第 127 号好友，位于第 15 行第 1 列。第 32 位获得红包好友为第 131 号好友，位于第 15 行第 5 列。第 33 位获得红包好友为第 137 号好友，位于第 16 行第 2 列。第 34 位获得红包好友为第 139 号好友，位于第 16 行第 4 列。第 35 位获得红包好友为第 149 号好友，位于第 17 行第 5 列。第 36 位获得红包好友为第 151 号好友，位于第 17 行第 7 列。第 37 位获得红包好友为第 157 号好友，位于第 18 行第 4 列。第 38 位获得红包好友为第 163 号好友，位于第 19 行第 1 列。第 39 位获得红包好友为第 167 号好友，位于第 19 行第 5 列。第 40 位获得红包好友为第 173 号好友，位于第 20 行第 2 列。第 41 位获得红包好友为第 179 号好友，位于第 20 行第 8 列。第 42 位获得红包好友为第 181 号好友，位于第 21 行第 1 列。第 43 位获得红包好友为第 191 号好友，位于第 22 行第 2 列。第 44 位获得红包好友为第 193 号好友，位于第 22 行第 4 列。第 45 位获得红包好友为第 197 号好友，位于第 22 行第 8 列。第 46 位获得红包好友为第 199 号好友，位于第 23 行第 1 列。第 47 位获得红包好友为第 211 号好友，位于第 24 行第 4 列。第 48 位获得红包好友为第 223 号好友，位于第 25 行第7列。第 49 位获得红包好友为第 227 号好友，位于第 26 行第 2 列。

第 50 位获得红包好友为第 229 号好友，位于第 26 行第 4 列。
第 51 位获得红包好友为第 233 号好友，位于第 26 行第 8 列。
第 52 位获得红包好友为第 239 号好友，位于第 27 行第 5 列。
第 53 位获得红包好友为第 241 号好友，位于第 27 行第 7 列。
第 54 位获得红包好友为第 251 号好友，位于第 28 行第 8 列。
第 55 位获得红包好友为第 257 号好友，位于第 29 行第 5 列。
第 56 位获得红包好友为第 263 号好友，位于第 30 行第 2 列。
第 57 位获得红包好友为第 269 号好友，位于第 30 行第 8 列。
第 58 位获得红包好友为第 271 号好友，位于第 31 行第 1 列。
第 59 位获得红包好友为第 277 号好友，位于第 31 行第 7 列。
第 60 位获得红包好友为第 281 号好友，位于第 32 行第2列。
第 61 位获得红包好友为第 283 号好友，位于第 32 行第 4 列。
第 62 位获得红包好友为第 293 号好友，位于第 33 行第 5 列。
第 63 位获得红包好友为第 307 号好友，位于第 35 行第1列。
第 64 位获得红包好友为第 311 号好友，位于第 35 行第 5 列。
第 65 位获得红包好友为第 313 号好友，位于第 35 行第7列。
第 66 位获得红包好友为第 317 号好友，位于第 36 行第 2 列。
第 67 位获得红包好友为第 331 号好友，位于第 37 行第7列。
第 68 位获得红包好友为第 337 号好友，位于第 38 行第4列。
第 69 位获得红包好友为第 347 号好友，位于第 39 行第 5 列。
第 70 位获得红包好友为第 349 号好友，位于第 39 行第 7 列。
第 71 位获得红包好友为第 353 号好友，位于第 40 行第2列。
第 72 位获得红包好友为第 359 号好友，位于第 40 行第 8 列。
——报告：总共有 72 位好友获得红包。

□ Q2．跳马最少步数计算题：如下图，中国象棋的棋盘有 10 行 9 列，我们需要计算棋子＂马＂走到每个点的最少步数，并将这些结果存储在矩阵 $\boldsymbol{A}_{\mathbf{1 0} \times \mathbf{9}}$ 中。参考结果如比如 $\boldsymbol{A}(\mathbf{1}, \mathbf{2})=\mathbf{0}, \boldsymbol{A}(\mathbf{1}, \mathbf{1})= 3, A(2,4)=1$ 等等。
□ 请在作业中提供一种尽可能效率高的算法，并将算法用MATLAB代码实现。最后将矩阵 $A$ 的计算结果粘贴在作业里。没有修过《数据结构与算法》的同学可以与修过的同学进行必要的交流和学习。允许代码使用任意层循环。

□ 算法关键词：广度优先搜索，静态队列。（本题亦可以使用逐点递归计算，但复杂度会大大提高）
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-054.jpg?height=525&width=495&top_left_y=659&top_left_x=1123)

```
>> seventhWeek_Q2()
Q2. 跳马最少步数计算题 (BFS 算法实现)
计算结果矩阵 A (10x9):

\begin{tabular}{|l|l|l|l|l|l|l|l|l|}
\hline 3 & 0 & 3 & 2 & 3 & 2 & 3 & 4 & 5 \\
\hline 2 & 3 & 2 & 1 & 2 & 3 & 4 & 3 & 4 \\
\hline 1 & 2 & 1 & 4 & 3 & 2 & 3 & 4 & 5 \\
\hline 2 & 3 & 2 & 3 & 2 & 3 & 4 & 3 & 4 \\
\hline 3 & 2 & 3 & 2 & 3 & 4 & 3 & 4 & 5 \\
\hline 4 & 3 & 4 & 3 & 4 & 3 & 4 & 5 & 4 \\
\hline 3 & 4 & 3 & 4 & 3 & 4 & 5 & 4 & 5 \\
\hline 4 & 5 & 4 & 5 & 4 & 5 & 4 & 5 & 6 \\
\hline 5 & 4 & 5 & 4 & 5 & 4 & 5 & 6 & 5 \\
\hline 6 & 5 & 6 & 5 & 6 & 5 & 6 & 5 & 6 \\
\hline
\end{tabular}
$\boldsymbol{f} \boldsymbol{x} \gg$
```

\％Q2．跳马最少步数计算题
\％算法：广度优先搜索（BFS）

```
% 日期:2025年11月5日
function seventhWeek_Q2()
% - 1.初始化 - -
R = 10; % 10行
C = 9; % 9列
% 结果矩阵 A, 全部初始化为 -1 (代表"未访问")
% A(r, c) 将存储从起点到 (r, c) 的最少步数
A = - ones(R, C);
% 起点 (马)
start_r = 1;
start__c = 2;
% 设置起点距离为 0
A(start__r, start__c) = 0;
% - 2. BFS (广度优先搜索) -_
% 算法关键字:静态队列
% 我们用一个预分配的数组和两个指针 (head, tail) 来模拟一个高效的队列
% 队列最大容量为 R*C
queue = zeros(R * C, 2);
head = 1;% 队列头部指针 (指向下一个要读取的元素)
tail = 1;% 队列尾部指针 (指向下一个要插入的位置)
% 将起点入队
queue(tail, :) = [start__r, start__c];
```

```
tail = tail + 1;
% 定义"马"的 8个方向 (dr,dc) = (row_change, col_change)
% 对应 "日"字的八个角
dr = [-2, -2, -1, -1, 1, 1, 2, 2];
dc = [-1, 1, -2, 2, -2, 2, -1, 1];
% 开始 BFS 循环,当队列不为空时 (head < tail)
while head < tail
% 1.出队 (Dequeue)
curr_pos = queue(head, :);
curr_r = curr_pos(1);
curr_c = curr_pos(2);
head = head + 1; % 移动 head 指针
% 2. 获取当前点的距离 (步数)
current_dist = A(curr_r, curr_c);
% 3. 遍历 8个可能的下一步
for i = 1:8
new_r = curr_r + dr(i);
new_c = curr_c + dc(i);
% 4.检查是否有效 (是否在棋盘内)
isValidPos = (new_r >= 1) && (new_r <= R) && ...
(new_c >= 1) && (new_c <= C);
if isValidPos
% 4.1: 检查是否"未访问"(A(new_r, new_c)== -1)
```

```
if A(new_r, new_c) = = 1
% 5. 标记并入队
% 5.1: 记录最短距离
A(new_r, new_c) = current_dist + 1;
% 5.2:将新位置入队 (Enqueue)
queue(tail, :) = [new_r, new_c];
tail = tail + 1;
end
end
end
end
% - 3. 输出结果 - -
fprintf ('Q2.⿱跳马最少步数计算题\sqcup( BFS \sqcup算法实现)\n');
fprintf('. \n');
fprintf('计算结果矩阵 }\lrcorner\mp@subsup{\textrm{A}}{\sqcup}{}(10\times9):\backslashn\backslashn')
% 打印矩阵 A (MATLAB 默认的 'disp'格式)
disp (A);
end
% —— 要运行此代码, 请在 MATLAB 命令窗口中调用: -- 
% seventh Week_Q2()
```

问题分析: 本题要求计算一个 $10 \times 9$ 棋盘上的 "马" 从起点 $(1,2)$ 到达棋盘上
任意其它点的最少步数。

这是一个典型的单源最短路径（Single－Source Shortest Path，SSSP）问题。由于棋盘可以看作一个图（Graph），其中每个格子是一个节点（Node），＂马＂的每一步合法移动是连接两个节点的一条边（Edge）。因为每一步的＂代价＂都

## 是 1，所以这是一个无权图。

算法选择：对于无权图的单源最短路径问题，＊＊广度优先搜索（Breadth－First Search，BFS）＊＊是最高效、最标准的算法。这与题目中的＂算法关键词＂提示一致。

## BFS 思路详解：

## 1．数据结构：

－结果矩阵 $\mathbf{A ( 1 0 x 9 )}$ ：用于存储从起点到每个点（ $r, c$ ）的最少步数。我们将其全部初始化为一个特殊值（例如 -1 ），表示＂尚未访问＂。
－队列（Queue）：用于存放＂待访问＂的节点坐标。BFS 的特性保证了我们总是先处理完距离近的节点，再处理距离远的节点。为了效率，我们使用一个预先分配好大小的数组和两个指针（head 和 tail）来模拟一个静态队列，避免 MATLAB 在循环中动态调整数组大小。

## 2．初始化：

- 创建 $\mathrm{A}=-\operatorname{ones}(10,9)$ 。
- 设置起点：start＿r $=1$ ，start＿c $=2$ 。
- 将起点的步数设为 $0: ~ \mathrm{~A}(1,2)=0$ 。
- 将起点坐标 $[1,2]$ 存入队列。


## 3．定义＂马＂的移动：

－＂马＂有 8 个可能的移动方向（不受＂蹩马腿＂限制，因为棋盘是空的）。我们用两个数组 dr（行变化）和 dc（列变化）来表示这 8 个方向：
－dr $=[-2,-2,-1,-1,1,1,2,2]$
－ $\mathrm{dc}=[-1,1,-2,2,-2,2,-1,1]$

## 4．BFS 循环：

- 当队列不为空时，执行循环：
- 出队（Dequeue）：取出队首的坐标（curr＿r，curr＿c）。
- 获取当前距离：dist $=\mathrm{A}$（curr＿r，curr＿c）。
- 遍历邻居：循环遍历 8 个可能的移动方向：
- 计算新坐标：new＿r $=$ curr＿r $+d r(\mathrm{i})$, new＿c $=c u r r \_\mathrm{c}+\mathrm{dc}(\mathrm{i})$ 。
- 检查有效性：
（a）新坐标（new＿r，new＿c）是否在棋盘内（即 $1<=$ new＿r $<=10$且 $1<=$ new＿c $<=9$ ）？
（b）新坐标是否＂尚未访问＂（即 $\mathrm{A}($ new＿r，new＿c $)==-1$ ）？
－如果有效且未访问：
（a）更新距离：A（new＿r，new＿c）＝dist＋1。
（b）入队（Enqueue）：将新坐标［new＿r，new＿c］放入队尾。
5．结束：当队列为空时，表示所有从起点可达的格子都已被访问并计算了最短距离。矩阵 A 即为最终答案。


## Document

乐绎华，Yue Yihua

November 12， 2025

## Contents

0.1 习题 1 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 3
0.2 习题 2 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 5
0.3 习题 3 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 5
0.4 问题 4 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 7
0.5 习题 5 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 9

## 第八周电子版作业

$\square$ Q1．改编的习题4第4题（题目有改动！，假设符号计算保留 16位小数为真实值，trapz步长自定）

用 integral 求取 $\int_{-5 \pi}^{10 \pi} e^{-|x|}|\sin x| d x$ 的绝对精度为 $10^{-9}$ 的积分，并尝试用 trapz 及符号计算此积分。以符号计算的结果保留 16 位有效数字作为真实值，分析比较函数 integral 与 trapz 运算的误差（提示：注意 integral 指令相对误差控制对绝对精度的影响。）

□ Q2．根据本次课的课件内容，使用复合中矩形公式，计算定积分 $\int_{0}^{1} \frac{1}{1+x^{2}} \mathrm{~d} x$ 的值，并利用积分结果对常数 $\pi$ 进行近似。

□ Q3．使用diff与gradient函数，计算 $f(\boldsymbol{x})=\ln (\mathbf{1}+ x), 0 \leq x \leq 2$ 的近似导数（步长 $x=1 \times 10^{-5}$ ），然后比较 diff与gradient在 $\boldsymbol{f}^{\prime}(\mathbf{1})$ 的误差，以分析方法优劣性。（真实值是显而易见的，不需要符号计算（2））。
（未完，下一页还有选做题）

## 第八周电子版作业

Q4．用二维复合中矩体算法计算下列二重积分

$$
\iint_{D} \frac{x+y}{\sqrt{\left(1+x^{2}+y^{2}\right)^{3}}} \mathrm{~d} x \mathrm{~d} y, \quad\{D: 0 \leq x \leq 1,0 \leq y \leq 1\}
$$

请将积分正方形区域按 $\mathbf{2 0 0 0} \boldsymbol{\times} \mathbf{2 0 0 0}$ 的倍数均匀分成四百万个正方形，对每个正方形取中点函数值即可。并用符号运算获得该二重积分的真实值，再转化为双精度后，输出数值计算的误差。
（注意：该积分与第二课的积分不同）

Q5．利用课件21页下半部分所的二维蒙特卡洛法，设计一套 MATLAB代码，完成常数 $\pi$ 的估计。随机投点个数可以设置为 $\mathbf{1} \times \mathbf{1 0}^{6}$ 个。请避免不必要的循环体的使用。

## 0.1 习题 1

```
>> syms x
>> f_sym = exp(-abs(x)) * abs(sin(x));
>> a = 10*pi
a =
    31.4159
>> b=-5*pi
b =
    -15.7080
>> int(f_sym,x,b,a)
ans =
2*exp(-pi) + 2*exp(-2*pi) + 2*exp(-3*pi) + 2*exp(-4*pi) + (3*exp(-5*pi))/2 + exp(-6*pi) + exp(-7*pi) + e
>> vpa(ans,16)
ans =
1.090331328569942
>> vpa(ans,9)
ans =
1.09033133
fx >>
```

＞＞clear all
＞＞ $\mathrm{f}=$＠（x）exp（－abs（x））．＊abs（sin（x））；
＞＞ $\mathrm{a}=-5^{\star}$ pi；
b＝10＊pi；
\％选择大量采样点 N
$\mathrm{N}=10^{\wedge} 7$ ；\％ 1000 万个点
x＿trapz＝linspace（a，b，N）；
y＿trapz $=f\left(x \_\right.$trapz $) ; \% f$ 是上面定义的匿名函数
\％执行梯形积分
I＿trapz $=$ trapz $\left(\mathrm{x} \_\right.$trapz，y＿trapz $)$

I＿trapz＝
1.0903
$\underline{\mathrm{f}_{\mathrm{v}}} \gg$
＞＞clear all
＞＞\％1．定义符号变量
syms ×
\％2．定义被积函数 $f(x)=\exp (|x|){ }^{*} \operatorname{abs}(\sin (x))$
f＿sym $=\exp (-\mathrm{abs}(\mathrm{x})){ }^{\star}$ abs（sin（x））；
\％3．执行定积分计算
\％I＿sym＝int（f＿sym，x，－5＊pi，10＊pi）；
\％（注：此计算可能需要较长时间，或因为分段复杂而返回一个冗长的表达式）
\％4．使用分段积分简化计算（符号计算的原理）
\％积分 Il：$\left[-5^{*} \mathrm{pi}, 0\right] \Rightarrow|\mathrm{x}|=-\mathrm{x},|\sin (\mathrm{x})|=-\sin (\mathrm{x})$（在 $\left[-(\mathrm{k}+1) \mathrm{pi},-\mathrm{k}^{*} \mathrm{pi}\right]$ 为正）
\％积分 I2：$[0,10 * p i] \Rightarrow|x|=x,|\sin (x)|=\sin (x)$（在 $[k * p i,(k+1) p i]$ 为正）
Il＿integral＿pattern $=$ int（－exp（－x）＊ $\sin (x), x,-($ sym（＇k＇）＋1）＊pi，－sym（＇k＇）＊pi）；
I2＿integral＿pattern＝int（exp（x）＊sin（x），x，sym（＇k＇）＊pi，（sym（＇k＇）＋1）＊pi）；
\％我们可以直接使用 int 函数，让它处理分段
I＿sym $=$ int（f＿sym，$\left.x,-5^{*} p i, 10^{*} p i\right)$ ；
\％5．将符号结果转换为 16 位有效数字的浮点数作为＂真实值＂
I＿exact $=$ vpa $($ I＿sym， 16$)$
I＿exact＝
1.090331328569942
$f_{\underset{\sim}{x}} \gg \mid$

## 0.2 习题 2

```
>> % 1.定义函数和区间
f = @(x) 1 ./ (1 + x.^2);
a = 0;
b = 1;
% 2. 设定子区间数量 n
n = 100;
% 3. 计算步长 h
h = (b - a) / n;
% 4. 计算中点 x_bar_i
% 第 i 个子区间中点为 x_i + h/2,其中 x_i = a + i*h, i=0, 1, n, n-1
% 统一公式:x_bar_i = a + (i + 0.5) * h
i_indices = 0:(n-1);
x_midpoints = a + (i_indices + 0.5) * h;
% 5. 计算函数在所有中点的值
f_midpoints = f(x_midpoints);
% 6. 应用复合中矩形公式 (对函数值求和,然后乘以 h)
I_approx_midpoint = h * sum(f_midpoints);
% 7. 利用积分近似值求 pi 的近似值
pi_approx = 4 * I_approx_midpoint;
% 8. 显示结果
fprintf('--- 复合中矩形公式计算 ---\n');
fprintf('子区间数 n = %d\n', n);
fprintf('积分近似值 I_approx = %.15f\n', I_approx_midpoint);
fprintf('常数 pi 的近促值 pi_approx = %.15f\n', pi_approx);
fprintf('真实 pi 值 = %.15f\n', pi);
fprintf('绝对误差 (pi) = %.15f\n', abs(pi - pi_approx));
--- 复合中矩形公式计䈯 ---
子区间数 n = 100
积分近似值 I_approx = 0.785400246730781
常数 pi 的近似值 pi_approx = 3.141600986923125
真实 pi 值 = 3.141592653589793
绝对误差 (pi) = 0.000008333333332
..I
```


## 0.3 习题 3

\％\％Q3．数值微分比较：diff vs gradient（纯数值版本） clear all；\％清除工作区变量
\％－1．参数设置－
$\mathrm{d}=1 \mathrm{e}-5 ; \quad$ \％步长 $h$

```
X = 0:d:2; % 创建数值数组 X
% 直接使用数值 log 函数计算 Y (不再涉及符号计算)
Y = log(1 + X); % Y 是纯数值数组 (double)
% 真实导数值 }\mp@subsup{f}{}{\prime}(x)=1/(1+x
f_prime_true = 1 / (1 + 1); % 在 x=1 处的真实值
disp(['真实导数值 f','(1):⿱', num2str(f_prime_true)]);
% 找到 x=1 对应的索引 k
k = round (1/d) + 1;
disp( '. ');
%% -- 2. diff 方法 (前向差分)--
% 计算差分 dY/dx。
dY_diff = diff (Y) / d;
% 在 x=1 处的近似值
f_prime_diff_approx = dY_diff (k); % 注意: k 索引可能需要调整为 k-1 或 k,取决于癿
    % 我们沿用 k 索引,将其视为 x_k 处的前向差分。
% 计算误差
error_diff = abs(f_prime_diff_approx - f_prime_true);
disp ('1.\sqcup使用\sqcupdiff }\leq\mathrm{ 函数 (前向差分)');
disp([' 'பப近似值 f f',(1):⿱', num2str(f_prime_diff_approx, 15)]);
disp ([' 'பப 绝对误差:⿱', num2str(error_diff)]);
%% 3. gradient 方法 (中心差分) ---
% 计算梯度 dY/dx。此时 Y 为 double 数组,应调用数值 gradient。
% 如果您的 MATLAB 仍报错,请确保您已经重新启动过 MATLAB。
dY_grad = gradient (Y, d);
% 在 x=1 处的近似值
f_prime_grad_approx = dY_grad(k);
% 计算误差
error_grad = abs(f_prime_grad_approx - f_prime_true);
disp ('2.⿱使用\sqcupgradient 函数 (中心差分)');
disp(['பபப近似值 f ','(1):⿱', num2str(f_prime_grad_approx, 15)]);
disp ([' ' ' = 绝对误差:'', num2str(error_grad)]);
```

```
disp('..');
%% - 4. 误差比较分析 ---
disp ('3.⿱误差比较');
disp(['diff \ / gradient 误差比: ', num2str(error_diff / error_grad)]);
disp ('结论:gradient\sqcup函数 (中心差分) 具有更高的精度,误差小约 }6\sqcup\mathrm{ 个数量级 }(O(\mp@subsup{d}{}{2})
    真实导数值 f'(1): 0.5
    1. 使用 diff 函数(前向差分)
        近似值 f'(1):0.499998750014274
        绝对误差: 1.25e-06
    2. 使用 gradient 函数 (中心差分)
        近似值 f'(1): 0.500000000005551
        绝对误差: 5.5511e-12
    3. 误差比较
    diff / gradient 误差比: 225177.4099
    结论:gradient函数(中心差分)具有更高的精度,误差小约6个数量级(O(d2)vs O(d))。
fx >> |
```

gradient 函数更好．

## 0.4 问题 4

```
%% Q4. 二维复合中矩体积分计算与误差分析 (简化代码)
clear all;% 清除所有变量
clc;
% - 1. 符号运算:计算真实值 I_true--
disp ('-_ 1.\lrcorner符号运算:计算真实值 |__true__');
syms x y;
% 定义符号被积函数 f_sym
f_sym = (x + y) / sqrt ((1 + x^2 + y^2)^3);
% 计算二重积分的符号解
I_true_sym = int(int(f_sym, y, 0, 1), x, 0, 1);
% 将符号结果强制转换为高精度的数值 (这解决了符号积分无法完全解析的问题)
I_true = double (I_true_sym);
disp(['符号结果\sqcupI_true_sym:⿱丆, char(I_true_sym)]);
disp(['双精度真实值\sqcupI_true:⿱丆, num2str(I_true, 17)]);
```

```
disp('
```

$\_\_\_\_$

```
');
%% -- 2. 数值计算: 二维复合中矩体 I_approx --
disp ('- ' 2. 数值计算: 2000 x 2000 复合中矩体凝');
% 参数设置
N = 2000;
d = 1/N; % 步长 }
Delta_A = d^2; % 子正方形面积
% 构造中点坐标向量
%x_i = d/2, 3d/2, ..., 1-d/2
x_midpoints = d/2: d : 1-d/2;
y_midpoints = x_midpoints;
% 定义数值函数句柄 f_num
f_num = @(x,y)((x+y)./sqrt((1+x.\mp@subsup{.}{}{\wedge}2+y.\mp@subsup{}{}{\wedge}2).^3));
% 使用 meshgrid 和向量化计算函数值
[X_grid, Y_grid] = meshgrid(x__midpoints, y__midpoints);
% 计算近似积分值 (中矩体规则)
I_approx = sum(sum(f_num(X_grid, Y_grid))) * Delta_A;
disp (['数值计算近似值 \sqcup I_approx: ', num2str(I_approx, 17)]);
disp( '. ');
%% - 3. 误差分析 ---
disp ('-_3.u误差分析__');
% 计算绝对误差
error = abs(I_approx - I_true);
disp (['数值计算绝对误差\sqcup|I_approx 
```

```
--- 1.符号运算:计算真实值 I_true ---
符号结果 I_true_sym: int (((\mp@subsup{x}{}{\wedge}2+1\mp@subsup{)}{}{\wedge}3\mp@subsup{)}{}{\wedge}(1/2)/(\mp@subsup{x}{}{\wedge}2+1\mp@subsup{)}{}{\wedge}2+(((\mp@subsup{x}{}{\wedge}2+2\mp@subsup{)}{}{\wedge}3\mp@subsup{)}{}{\wedge}(1/2\mp@subsup{)}{}{*}(x/(\mp@subsup{x}{}{\wedge}2+1)-1))/(\mp@subsup{x}{}{\wedge}2+2)
双精度真实值 I_true: 0.44578927711426936
-----------------------------------
--- 2. 数值计算: 2000 x2000 复合中矩体 ---
数值计算近似值 I_approx: 0.44578929720666921
----------------------------------
--- 3. 误差分析 ---
数值计算绝对误差 | |_approx - I_true|: 2.0092e-08
>>
```


## 0.5 习题 5

```
%% Q5. 利用二维蒙特卡洛法估计常数 Pi ()
clear all;
clc;
% - 1. 参数设置 - 
N=1e6;% 总随机投点数 (1,000,000)
disp (['总投点数 }\mp@subsup{\textrm{N}}{\sqcup}{}=\llcorner,,\boldsymbol{num2str(N)]);
% -- 2. 生成随机坐标 (向量化) ---
% 生成 N 个 x 坐标和 N 个 y 坐标,范围都在[0, 1] 均匀分布。
% X 和 Y 都是 1 x N 的向量 (或者 N x 1, 取决于 rand的默认行为,但这里用行向量更清
X = rand(1,N);
Y= rand(1,N);
% - 3. 判断是否落入圆内 (向量化) ---
% 圆心 (a, b) = (0.5, 0.5), 半径 }r=0.
a = 0.5;
b = 0.5;
r = 0.5;
% 圆的方程:(x-a)^2 +(y-b)^2 <=r^2
% distance_squared 是一个 1 x N 的向量,存储了每个点到圆心的距离平方
distance_squared = (X - a).^2 + (Y - b).^2;
% is_inside 是一个逻辑向量 (logical array), TRUE/1 表示点在圆内
is_inside = (distance_squared <= r^2);
% - 4. 统计圆内点数 Na (向量化) -
% MATLAB/Octave 中, 对逻辑数组求和可以直接统计 TRUE/1 的个数。
Na = sum(is_inside);
disp ([,落在圆内的点数 }\mp@subsup{\textrm{Na}}{\sqcup=}{},\mathrm{ , num2str (Na)]);
```

```
% -- 5. 估计 Pi 值 --
pi_approx = 4 * (Na / N);
% 真实值 (用于比较)
pi_true = pi;
disp('. ');
disp([' Pi 的蒙特卡洛估计值:⿱丆, num2str(pi_approx, 10)]);
disp(['MATLAB\sqcup内置\sqcupPi\sqcup真实值:⿱丆,,num2str(pi_true,10)]);
% 计算估计误差
error = abs(pi_approx - pi_true);
disp (['估计绝对误差:⿱', num2str(error, 4)]);
```

```
总投点数 N=1000000
落在圆内的点数 Na = 785412
------------------------------------
Pi 的蒙特卡洛估计值:3.141648
MATLAB 内置 Pi 真实值:3.141592654
估计绝对误差: 5.535e-05
fx >>
```


## Document

乐绎华，Yue Yihua

November 19， 2025

## Contents

□ Q1．利用改进的欧拉法解微分方程初值问题 $\boldsymbol{y}^{\prime}=\boldsymbol{x}+\boldsymbol{y}, \boldsymbol{x} \in [0,1], \boldsymbol{y}(0)=0$ 。（在作业中写上真实函数求解过程（别说你没修过常微分方程（i）），实现的代码和最后计算出的 $\boldsymbol{y}(\mathbf{1})$误差即可）

The solution of $y^{\prime}-y=0$ is $y=c e^{x}$ ；let $y=c(x) e^{x}$ ，then $c^{\prime}(x) e^{x}=x$ ； $c(x)=(-1-x) e^{-x}+C$ ．Since $y(0)=0$ ，we have $c=1$ ，thus the solution of $y^{\prime}-y=x, y(0)=0$ is $y(x)=-x-1+e^{x}$ ．

```
>> clear
>> d = 1e-5;
x = 0:d:1;
>> y = zeros(1,length(x));
>> yp=@(X,Y) X+Y;
>> y(1)=0;
>> for i = 2:length(x)
temp = y(i - 1)+d*yp(x(i - 1),y(i - 1));
y(i)=y(i-1)+d/2*(yp(x(i-1),y(i-1))+yp(x(i),temp));
end
>> y_exact = exp (x)-x-1;
>> error = y(end)- y__exact(1)
error =
    0.7183
>> error = y(end) - y_exact(end)
```

```
error =
```

$-4.5307 \mathrm{e}-11$
Note 0．1．y＿exact is defined to be a row vector．

□ Q2．小球斜抛运动轨迹的数值建模、求解与绘制问题（虽然我们知道轨迹其实就是抛物线，详情见下页）

□ Q 2 ．小球水平初速度 $v_{0}=2 m / s$ ，垂直初速度 $v_{1}=2 m / s$ ，高度 $h=10 m$ ，重力加速度 $g=-10 m / s^{2}$ ，斜面倾角 $\theta= \mathbf{3 0}^{\boldsymbol{\circ}}$ ，使用MATLAB构造微分方程组，利用欧拉法同时模拟小球的速度变化与运行轨迹（不得直接人工求解与代入速度与位移公式），然后结合斜面方程，计算出斜面落点坐标 （ $\boldsymbol{s}_{\mathbf{0}}, \boldsymbol{s}_{\mathbf{1}}$ ），与降落时的速度（ $\boldsymbol{v}_{\mathbf{0}}^{*}, \boldsymbol{v}_{\mathbf{1}}^{*}$ ）。（写出MATLAB数值模拟、计算、和最终的近似计算结果，误差分析选做，真实值可以来自于抛物线计算）
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-070.jpg?height=467&width=663&top_left_y=1325&top_left_x=818)
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-071.jpg?height=719&width=1202&top_left_y=429&top_left_x=459)

```
>> clear all
>> %% 小球斜抛运动数值模拟(欧拉法)
% 1.参数设置
v0 = 2; % 初始水平速度 v_x (m/s)
v1 = 2; % 初始垂直速度 v_y (m/s)
h = 10; % 初始高度 y (m)
g = -10; % 重力加速度(m/s`2)
theta = 30; % 斜面倾角 (度)
dt = 0.001; % 时间步长 (s)
tan_theta = tan(deg2rad(theta));% 斜面斜率
% 2. 初始化
% 预分配空间 (假设最大迭代次数为 5000)
MaxIter = 5000;
x = zeros(1, MaxIter);
y = zeros(1, MaxIter);
vx = zeros(1, MaxIter);
vy = zeros(1, MaxIter);
time = zeros(1, MaxIter);
% 初始条件 (k=1)
x(1) = 0;
y(1) = h;
vx(1) = v0;
```

```
vy(1) = v1;
time(1) = 0;
% 3. 欧拉法迭代与撞击检测
k = 1;
is_impact = false;
while k < MaxIter
    k = k + 1;
    % (k-1) 时刻的状态
    xk_prev = x(k-1);
    yk_prev = y(k-1);
    vxk_prev = vx(k-1);
    vyk_prev = vy(k-1);
    % 欧拉法更新速度 (k 时刻)
    vx(k) = vxk_prev; % dv_x/dt = 0
    vy(k) = vyk_prev + g * dt; % dv_y/dt = g
    % 欧拉法更新位置 (k 时刻)
    x(k) = xk_prev + vxk_prev * dt;
    y(k) = yk_prev + vyk_prev * dt;
    time(k) = time(k-1) + dt;
    % 撞击条件检查:当前位置 y(k) 是否低于或等于斜面 y_slope_k
    y_slope_k = x(k) * tan_theta;
    if y(k) <= y_slope_k
        is_impact = true;
        break;
    end
end
% 4. 精确落点计算(线性插值)
if is_impact
    % 截断数组到实际使用的长度 k
    x = x(1:k);
    y = y(1:k);
    vx = vx(1:k);
    vy = vy(1:k);
    time = time(1:k);
    % 使用线性插值计算更精确的撞击时间 dt_extra (0<dt_extra<dt)
```

```
% 公式推导:dt_extra*(vy_{k-1} - vx_{k-1}* tan_theta)=x_{k-1}* tan_the
num = x(k-1) * tan_theta - y(k-1);
den = vy(k-1) - vx(k-1) * tan_theta;
dt_extra = num / den;
if dt__extra > 0 && dt__extra < dt
    t_impact = time(k-1) + dt__extra;
    % 计算撞击时的位置(s0,s1)
    s0 = x(k-1) + vx(k-1) * dt__extra;
    s1 = y(k-1) + vy(k-1) * dt_extra;
    % 计算撞击时的速度(v0*,v1*)
    v0_star = vx( k -1); % vx 是常数
    v1_star = vy(k-1)+g*dt_extra;%vy 是线性变化
    % 修正数组,将撞击点作为最后一个点用于绘图
    x (k) = s0;
    y(k) = s1;
    vx(k) = v0__star;
    vy(k) = v1_star;
    time(k) = t__impact;
else
    % 如果插值失败,则使用 k 时的近似值
    s0 = x(k); s1 = y(k);
    v0_star = vx(k); v1_star = vy(k);
    t_impact = time(k);
end
% 5. 结果输出
fprintf('--- 小球斜抛运动数值模拟结果(欧拉法)-\n');
fprintf ('撞击时间 T = %.4f s \n', t__impact);
fprintf('斜面落点坐标 (s0, s1)=(%.4f m,%.4f m)\n', s0, s1);
fprintf('落点时的速度(v0*,v1*)=(%.4f m/s, %.4f m/s)\n', v0__star, v1_star
%6. 绘图
figure;
plot(x,y,'b-','LineWidth',2,'DisplayName','小球轨迹(欧拉法)');
hold on;
% 绘制斜面 (从 x=0 到落点 s0)
x_slope = [0, max(s0, 0)];
```

```
    y_slope = [0, max(s1, 0)];
    plot(x_slope, y_slope, 'r--','LineWidth', 2,'DisplayName','斜面(0 =
    % 绘制撞击点
    plot(s0, s1, 'ko', 'MarkerFaceColor', 'k', 'MarkerSize', 8, 'DisplayName', '
    title('小球斜抛运动轨迹数值模拟');
    xlabel('水平位移 x (m)');
    ylabel('垂直位移 y (m)');
    legend('show', 'Location', 'best');
    grid on;
    axis equal;% 确保斜率和轨迹比例正确
    hold off ;
else
    fprintf ('错误:迭代次数不足以检测到撞击,请增大 MaxIter。\n');
end
- 小球斜抛运动数值模拟结果 (欧拉法)-
撞击时间 T = 1.5018 s
斜面落点坐标 (s0, s1)=(3.0036 m,1.7341 m)
落点时的速度 (v0*, v1*) = (2.0000 m/s, - 13.0180 m/s)
>>
```

Document

乐绎华，Yue Yihua
November 26， 2025

## Contents

## 第十一周电子版作业

□ Q1．设矩阵 $\boldsymbol{A}=\left[\begin{array}{ccc}\mathbf{1} & \mathbf{1} & \mathbf{1} \\ \mathbf{1} & \mathbf{2} & \mathbf{3} \\ \mathbf{2} & \mathbf{1} & -\mathbf{1}\end{array}\right]$ ，请用MATLAB函数计算矩阵 $\boldsymbol{A}$ 的1－范
数， 2 －范数，$\infty$－范数，Frobenius范数，核范数以及谱半径。
□ Q2．线性反问题 $\boldsymbol{A} \boldsymbol{x}=\overrightarrow{\boldsymbol{b}}$ 中，病态矩阵 $\boldsymbol{A}$ 往往非常常见。请根据数值分析或其他相关资料。简单描述什么叫做矩阵的条件数，以及高条件数病态矩阵对反问题求解的影响。
□ 然后，尝试用plot函数绘制 $1^{\sim} 50$ 阶希尔伯特矩阵（见第五课例6．1－3）的条件数变化图，证明其为病态矩阵。（提示：病态矩阵使用常规方法计算条件数会不准）
$\square \mathrm{Q} 3$. 习题4第10题，使用MATLAB函数A\b，inv（A）＊b与rref分别得到了什么结果，为什么？请解释原因。并且将线性方程组的通解表示出来。

求矩阵 $\mathbf{A x}=\mathbf{b}$ 的解， A 为 4 阶魔方阵， b 是（ $4 \times 1$ ）的全 1 列向量。

```
> A = [1 1 1; 1 2 3; 2 1 -1];
>> norm(A, 1)
ans =
```

```
>> norm(A, 2)
ans =

4.1126
```

```
>> norm(A, inf)
ans =
```

6

```
>> norm(A, 'fro')
ans =
```

4.7958
＞＞svd doc
错误使用 svd
第一个输入必须为单精度值或双精度值。

```
>> doc svd
>> nuclear_norm = sum(svd(A))
nuclear_norm =
    6.6763
>> doc eig
>> spectral_radius = max(abs(eig(A)))
spectral_radius =
```


### 3.7813

Q2：
定义：矩阵 $A$ 的条件数 $\operatorname{cond}(A)$ 是其范数 $\|A\|$ 与其逆矩阵的范数 $\left\|A^{-1}\right\|$的乘积：

$$
\operatorname{cond}(A)=\|A\| \cdot\left\|A^{-1}\right\|
$$

为什么高条件数导致反问题求解不稳定？
首先有限维空间范数等价，不妨考虑 $\|\cdot\|_{2}$ ，我们有 $\|A\|_{2} \cdot\left\|A^{-1}\right\|_{2} \gg 1$ ，这可能有 $\left\|A^{-1}\right\|_{2} \gg 1 。\left\|A^{-1}\right\|_{2}=\frac{1}{\sigma_{\min }}$ ，也就是 $A$ 的最小奇异值很小，这说明 $A$很接近奇异矩阵。

病态矩阵是一个其条件数（Condition Number）很大的矩阵。

$$
\boldsymbol{A} \text { 是病态矩阵 } \Longleftrightarrow \operatorname{cond}(\boldsymbol{A}) \gg 1
$$

其中，条件数 $\operatorname{cond}(\boldsymbol{A})$ 是衡量线性方程组 $\boldsymbol{A x}=\mathbf{b}$ 在求解过程中对输入数据（b或 $\boldsymbol{A}$ ）的微小扰动敏感程度的指标。

病态矩阵本质上是数值不稳定的，因为：几何意义（接近奇异）：
－高条件数意味着矩阵 $A$ 接近奇异（不可逆），即其最小奇异值 $\sigma_{\min }$ 趋近于零。
－代数意义（几乎线性相关）：这导致 $A$ 的列向量（或行向量）几乎线性相关。
－数值后果（误差放大）：对方程组 $A \mathbf{x}=\mathbf{b}$ 来说，输入数据 $\mathbf{b}$ 中一个很小的误差 $\delta \mathbf{b}$ 会被条件数放大，导致解 $\mathbf{x}$ 产生一个巨大的误差 $\delta \mathbf{x}_{\circ}$

$$
\frac{\|\delta \mathbf{x}\|}{\|\mathbf{x}\|} \leq \operatorname{cond}(A) \cdot \frac{\|\delta \mathbf{b}\|}{\|\mathbf{b}\|}
$$

简而言之，病态矩阵就是那些对输入中的微小误差表现出极度敏感性，从而导致数值求解结果不可信的矩阵。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-077.jpg?height=739&width=1207&top_left_y=1269&top_left_x=458)

```
N=50; % 矩阵的最大阶数
cond_values = zeros(N,1);% 存储条件数
for n = 1:N
    H = hilb (n); % 生成 n 阶 Hilbert 矩阵
```

```
    % 计算 2-条件数 (默认)
    cond_values (n) = cond (H);
end
% 绘制条件数变化图
figure;
semilogy(1:N, cond_values, '-o', 'LineWidth', 1.5);
xlabel('矩阵阶数 n');
ylabel('条件数cond_2(H_n)');
title ('Hilbert 矩阵的条件数随阶数 n 的变化');
grid on;
```

－证明其为病态矩阵：从图中可以看出，随着阶数 $n$ 的增加，Hilbert 矩阵的条件数呈指数级快速增长。
－例如，当 $n=15$ 时， $\operatorname{cond}_{2}\left(H_{15}\right)$ 已经超过 $10^{17}$ ，这远大于标准的双精度浮点数 $\varepsilon \approx 10^{-16}$ 的倒数 $10^{16}$ 。
－结论：由于 $\operatorname{cond}\left(H_{n}\right)$ 迅速变得非常大，Hilbert 矩阵是一个典型的病态矩阵，这证明了病态矩阵随着阶数的增大条件数会急剧增加，使得直接求解线性方程组变得极其困难。

Q3：
为什么三种方法得到＂一样＂的数值解？
虽然 A 是奇异的（秩为 3），方程组仍有解（ b 在 A 的列空间中），属于无穷多解的情况。
$\mathrm{A} \backslash \mathrm{b}$ 使用了基于 QR 分解的最小二乘／最小范数解算法，对奇异阵也能正确处理，返回的是无穷多个解中 2 －范数最小的那一个（即基本解系中自由变量为 0 的特解）。
$\operatorname{inv}(\mathrm{A}) * \mathrm{~b}$ 理论上在奇异时不合法，MATLAB 仍然硬算伪逆（实际上用了 pinv），但会给出警告。数值上碰巧和 $\mathrm{A} \backslash \mathrm{b}$ 得到同一个特解（因为默认伪逆也是最小范数解）。
rref（［A b］）最清楚地告诉我们：方程组有一个自由变量（对应第 4 列），秩 $=3$ ，前 3 个变量是主元变量，第 4 个是自由变量。

```
>> A = magic (4)
A =

\begin{tabular}{rrrr}
16 & 2 & 3 & 13 \\
5 & 11 & 10 & 8 \\
9 & 7 & 6 & 12 \\
4 & 14 & 15 & 1
\end{tabular}
>> b = ones (4,1);
>> rank(A)
ans =
```

$\gg \mathrm{x} 1=\mathrm{A} \backslash \mathrm{b}$
警告：矩阵接近奇异值，或者缩放不良。结果可能不准确。RCOND＝ $1.306145 \mathrm{e}-17$ 。
$\mathrm{x} 1=$
0.0588
0.1176
－0．0588
0
$\gg \mathrm{x} 2=\operatorname{inv}(\mathrm{A}) * \mathrm{~b}$
警告：矩阵接近奇异值，或者缩放不良。结果可能不准确。RCOND＝ $1.306145 \mathrm{e}-17$ 。
x2＝
0.0469
0.1875
－0．0625
－0．0156
$\gg[\mathrm{R}, \mathrm{jb}]=\operatorname{rref}([\mathrm{A} \mathrm{b}])$
$\mathrm{R}=$

| 1.0000 | 0 | 0 | 1.0000 | 0.0588 |
| ---: | ---: | ---: | ---: | ---: |
| 0 | 1.0000 | 0 | 3.0000 | 0.1176 |
| 0 | 0 | 1.0000 | -3.0000 | -0.0588 |
| 0 | 0 | 0 | 0 | 0 |

jb＝
$\begin{array}{lll}1 & 2 & 3\end{array}$
＞＞
1．$x 1=A \backslash b$
得到 $\approx[0.0588 ; 0.1176 ;-0.0588 ; 0]^{\top}$
→ 这是 MATLAB 当前版本采用的 QR 带列选主元分解得到的＂最小范数

解＂。注意第 4 个分量正好是 0 （被当作自由变量），这是一种合理选择，但数值已经严重失真。
1.

$$
x 2=\operatorname{inv}(A) * b
$$

得到 $\approx[0.0469 ; 0.1875 ;-0.0625 ;-0.0156]^{\top}$ ，完全不对。
$\operatorname{inv}(A)$ 在奇异阵时实际算的是伪逆，但因为条件数 $\approx 10^{17}$ ，误差被放大了 $10^{17}$ 倍，得到的根本不是任何意义下的真解。两次警告 RCOND $\approx 1.3 \mathrm{e}-17$ 就是在告诉你：这个逆根本不可信。

3． $\operatorname{rref}([\mathrm{Ab}])$ 给出的结果最接近＂真相＂：
主元列 $\mathrm{jb}=\left[\begin{array}{lll}1 & 2 & 3\end{array}\right]$ ，自由变量是 $\mathrm{x}_{4}$ 。所以通解仍然是：

$$
\left\{\begin{array}{l}
x_{1}+x_{4}=0.0588 \\
x_{2}+3 x_{4}=0.1176 \\
x_{3}-3 x_{4}=-0.0588
\end{array} \Rightarrow x=\left[\begin{array}{c}
0.0588 \\
0.1176 \\
-0.0588 \\
0
\end{array}\right]+t\left[\begin{array}{c}
-1 \\
-3 \\
3 \\
1
\end{array}\right], \quad t \in \mathbb{R}\right.
$$

这个形式和 $\mathrm{A} \backslash \mathrm{b}$ 完全一致（只是自由变量基向量取了相反号）。

## 23363017；乐绎华；第 9 次作业

乐绎华，Yue Yihua， 23363017
December 4， 2025

## Contents

## 第十二周电子版作业

□ Q1．习题6第3题（写出M函数源代码与测试结果，注意格式）
编写一个函数M文件，它的功能：没有输入量时，画出单位圆（见图p6－1）；输入量是大于 2 的自然数 N 时，绘制正 N 边形，图名应反映显示多边形的真实边数（见图p6－ 2）；输入量是＂非自然数＂时，给出＂出错提示＂。此外，函数M文件应有H1行、帮助说明和程序编写人姓名。（提示：nargin，error，int2str）
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-081.jpg?height=347&width=317&top_left_y=1495&top_left_x=605)
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-081.jpg?height=346&width=362&top_left_y=1491&top_left_x=1140)
function draw＿shape（N）
\％DRAW＿SHAPE 绘制单位圆或正多边形
\％用法：
\％draw＿shape（ ）－不带输入参数时，绘制一个单位圆。
$\% \quad d$ raw＿shape $(N)-$ 输入参数为大于 2 的自然数 $N$ 时，绘制正 $N$ 边形。
\％
\％如果输入不符合要求（非自然数或小于等于 2），程序将报错。

```
%
% 程序编写人:[你的名字/Gemini]
% 编写日期: 2025-12-03
% 判断输入参数的个数
if nargin = 0
    % - 情况 1: 没有输入量,画出单位圆 --
    t = linspace ( 0, 2* pi, 100); % 生成 0到 2p i的 100个点,保证圆滑
    x = (os ( t);
    y = sin(t);
    figure; % 新建图形窗口
    plot(x,y,'r-','LineWidth',2);%红色实线,线宽为2
    axis equal;% 保证坐标轴比例一致,使圆看起来是圆的
    title('Circle');% 设置图名
    grid on; % 显示网格 (可选)
elseif nargin == 1
    % -- 情况2: 有一个输入量 N__
    % 验证输入量是否为"天于 2的自然数"
    % isnumeric: 检查是否为数字
    % isscalar: 检查是否为标量 (单个数值)
    % floor (N)==N: 检查是否为整数
    % N>2: 检查是否大于2
    if isnumeric (N) && isscalar (N) && floor (N) = N && N > 2
        % 绘制正 N 边形
        % 正N边形的顶点分布在圆周上, 分为N等分
        % 我们需要 N+1 个点来闭合多边形 (起点和终点重合)
        theta = linspace ( 0, 2*pi, N+1);
        x = (os (theta);
        y = sin(theta);
        figure;
        plot(x,y,'r-','LineWidth', 2);%红色实线
        axis equal;
        % 使用 int2str 将数字转换为字符串,拼接标题
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-082.jpg?height=47&width=974&top_left_y=2083&top_left_x=713)

```
        grid on;
    else
        % ——情况 3: 输入量是"非自然数"或不满足条件——
        error('出错提示:\sqcup输入必须是大于 }\mp@subsup{2}{}{~}\mathrm{ 的自然数 (整数)!');
```

```
        end
    else
        % 输入参数过多
        error('出错提示:\sqcup输入参数过多,请提供 }\sqcup\mp@subsup{0}{\sqcup}{}\mathrm{ 个或 }\cup\mp@subsup{1}{\sqcup}{}\mathrm{ 个参数。');
    end
end
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-083.jpg?height=735&width=1204&top_left_y=842&top_left_x=459)

## 第十二周电子版作业

□ Q2．分别使用MATLAB函数 fminbnd，自己完成的黄金分割法与自己完成的牛顿迭代法，完成—元函数 $f(x)=3 x^{2}- \sin \boldsymbol{x}-\mathbf{e}^{\boldsymbol{x}}$ 在 $\boldsymbol{x} \in[\mathbf{0}, \mathbf{1}]$ 之间最小值的计算。注意 $\boldsymbol{f}(\boldsymbol{x})$ 在 $\boldsymbol{x} \in [0,1]$ 是单峰函数并且是凸函数，所以各种方法均应收敛。
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-084.jpg?height=722&width=1203&top_left_y=428&top_left_x=460)

```
> f = @(x) 3 * x.^2 - sin(x) - exp(x);
    figure;
    fplot(f, [0, 1], 'LineWidth', 2);
    grid on;
% 直接求解
    [x1, fval] = fminbnd(f, 0, 1)
```

    x1 =
    $$
0.4026
$$

fval＝
-1.4013
＞＞\％—— 第二部分：自编黄金分割法——
\％定义区间和精度
$\mathrm{a}=0$ ；
b＝1；
tol＝1e－6；\％精度要求
\％黄金分割比率

```
phi = (sqrt(5) - 1) / 2;
% 初始化内部试探点
x1 = b - phi * (b - a);
x2 = a + phi * (b - a);
f1 = f(x1);
f2 = f(x2);
while (b - a) > tol
    if f1 < f2
        % 最小值在左侧,舍弃右边 [x2, b]
        b = x2;
        x2 = x1;
        f2 = f1;
        x1 = b - phi * (b - a);
        f1 = f(x1);
    else
        % 最小值在右侧,舍弃左边 [a, x1]
        a = x1;
        x1 = x2;
        f1 = f2;
        x2 = a + phi * (b - a);
        f2 = f(x2);
    end
end
x_golden = (a + b) / 2;
f_golden = f (x__golden);
fprintf('=== 方法2: 黄金分割法===\n');
fprintf('最优解 x = %.6f \ n', x_golden);
fprintf('最小值 f(x)=%.6f \n \n', f_golden);
= 方法 2: 黄金分割法=
最优解 x = 0.402632
最小值 f(x)=-1.401260
>> % 一 第三部分: 自编牛顿迭代法——
% 定义导数函数
\begin{array} { l l l } { d f = @ ( x ) ~ 6 * x - \operatorname { c o s ( x ) - e x p ( x ) ; ~ } } & { \% } & { \text { 二阶导数} } \\ { d d f = @ ( x ) 6 + \operatorname { s i n ( x ) - e x p ( x ) ; ~ } } & { \% } & { \text { 二阶导数} } \end{array}
% 初始猜测(在 [0,1] 区间内任选,如 0.5)
x0 = 0.5;
err = 1;
tol = 1e-6;
```

```
max_iter = 100;
iter = 0;
while err > tol && iter < max_iter
    % 牛顿迭代公式:x_new = x_old - f'(x)/ f',(x)
    x_new = x0 - df(x0) / ddf(x0);
    % 计算误差
    err = abs(x_new - x0);
    % 更新 x0
    x0 = x_new;
    iter = iter + 1;
end
x_newton = x0;
f_newton = f(x__newton);
fprintf('=== 方法3: 牛顿迭代法===\n');
fprintf ('迭代次数:%d\n', iter);
fprintf('最优解x x = %.6f \n', x_newton);
fprintf('最小值 f(x)=%.6f \n', f_newton);
＝方法3：牛顿迭代法＝
迭代次数：3
最优解 $\mathrm{x}=0.402631$
最小值 $\mathrm{f}(\mathrm{x})=-1.401260$
＞＞
```

fminbnd
$\mathrm{x} 1=$
0.4026
fval $=$
－1．4013
$===$ 方法 2：黄金分割法 $===$ 最优解 $\mathrm{x}=0.402632$ 最小值 $\mathrm{f}(\mathrm{x})=-1.401260$
$===$ 方法 3：牛顿迭代法 $===$ 迭代次数： 3 最优解 $\mathrm{x}=0.402631$ 最小值 $\mathrm{f}(\mathrm{x})=-1.401260$

□ Q3．多元函数的最小值问题有时会加上各种不同的约束条件 （等式或不等式条件），从而演化为条件极值问题。请尝试利用MATLAB帮助系统理解函数 fmincon 的基本使用方法，并利用这个函数求解最优化问题 $\left\{\begin{array}{l}\min _{x, y, z} \sin x+y+\mathbf{e}^{z} \\ x^{2}+y^{2}+z^{2}=1 \\ x+y \geq-0.5\end{array}\right.$ ，初始点可以设为 $\left(\boldsymbol{x}_{\mathbf{0}}, \boldsymbol{y}_{\mathbf{0}}, \boldsymbol{z}_{\mathbf{0}}\right)=(\mathbf{1}, \mathbf{0}, \mathbf{0})$ 。提示：这个问题没有线性等式约束，需要用空矩阵［］作为线性不等式约束参数。
（未完，下一页有小选做题）
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-087.jpg?height=734&width=1202&top_left_y=1067&top_left_x=459)

```
% —— Q3: 使用 fmincon 求解多元约束优化 —— 
clc; clear;
% 1. 定义目标函数 (匿名函数形式)
% x(1)对应 x, x (2) 对应 }y,x(3)\mathrm{ 对应 }
fun = @ (x) sin(x(1)) + x(2) + exp(x(3));
% 2. 定义初始猜测点
x0 = [1; 0; 0];
```

```
% 3. 定义线性不等式约束 A*x<=b
% 原式:x+y>=-0.5 => -x = y<= 0.5
% 对应系数矩阵 A=[-1, -1, 0], b=0.5
A = [-1, -1, 0];
b = 0.5;
% 4.定义线性等式约束 Aeq*x=beq (题目没有,设为空)
Aeq = [];
beq = [];
% 5. 定义变量上下界(题目没有,设为空)
lb = [];
ub = [];
% 6. 定义非线性约束 (需要调用下方定义的函数)
nonlcon = @mycon;
% 7. 调用 fmincon 求解
% 语法:fmincon(fun, x0, A, b, Aeq, beq, lb, ub, nonlcon)
[x_opt, f_val] = fmincon(fun, x0, A, b, Aeq, beq, lb, ub, nonlcon);
% 输出结果
fprintf('=\sqcupQ3}\mathrm{ 计算结果 }\textrm{v===\n');
fprintf('最优解: sx=%.4f, }\sqcupy=%.4f, \sqcupz=%.4f \n', x_opt(1), x_opt(2), x_opt(3)); 
fprintf ('函数最小值: }\cup%.4f\n', f_val); 
% - 非线性约束函数 - -
function [c, ceq] = mycon(x)
    % c 是非线性不等式 c(x)<=0 (本题没有,为空)
    c = [];
    % ceq 是非线性等式 ceq (x) = 0
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-088.jpg?height=51&width=1174&top_left_y=1791&top_left_x=541)

```
    ceq = x(1)^2 + x(2)^2 + x(3)^2 - 1;
end
```


## 第十二周电子版作业

$\square Q 4$ ．（小选做） $\boldsymbol{l}_{\mathbf{1}}$ 正则化问题在计算与应用数学的最优化领域，数据科学的压缩感知，统计的Lasso问题中都有很重要的应用价值。本题请利用自己编写的迭代算法求解下列模型：
$\min _{\vec{x}} \frac{1}{2}\|A \vec{x}-\vec{b}\|_{2}^{2}+\lambda\|B \vec{x}\|_{1}$ 的解。其中，目标向量 $\vec{x}$ 为 4 维列向量，$A$ 为 $4 \times 4$ 矩阵，$B=\left[\begin{array}{cccc}1 & -1 & 0 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 0 & 1 & -1\end{array}\right], \vec{b}$ 为 4 维列向量， $\boldsymbol{\lambda}>\mathbf{0}$ 为常参数。先设 $\boldsymbol{\lambda}=\mathbf{0 . 0 5}$ ，则具体定义格式如下： rng default
$\mathrm{A}=\operatorname{rand}(4) ; \mathrm{B}=[1,-1,0,0 ; 0,1,-1,0 ; 0,0,1,-1]$ ；
$\mathrm{b}=\operatorname{rand}(4,1) ;$ lambda $=0.05$ ；
通过算法得到问题的解后，尝试令 $\boldsymbol{\lambda} \rightarrow \mathbf{0}$ 或 $\boldsymbol{\lambda} \rightarrow+\infty$ ，观察最值点 $\overrightarrow{\boldsymbol{x}}$ 的变化情况。（提示：使用函数 fminunc计算这个题目的结果有时不准确。由于 1 －范数不可导，可以尝试使用交替乘子迭代法（ADMM）或近端梯度算法或其他算法来解决这个问题。）

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-089.jpg?height=736&width=1204&top_left_y=1480&top_left_x=459)

```
% —— Q4: 使用 ADMM 求解 L1 正则化问题 ——
clc; clear;
% 1. 初始化数据 (题目给定)
rng default
A = rand (4);
B = [1,-1,0,0; 0,1,-1,0; 0,0,1,-1];
b = rand (4,1);
% 2. 定义不同的 lambda 进行观察
lambda_vals = [0, 0.05, 100]; % 分别对应:无正则、题目要求、强正则
fprintf('= \Q4 _ ADMM_求解结果 }\leftarrow==\\textrm{n}')
fprintf('%-10s 犊显示)');}
fprintf('. \n');
for lambda = lambda__vals
    % 调用自写的 ADMM 求解函数
    [x_opt, iter] = admm_solver(A, B, b, lambda);
    % 输出结果
    fprintf (},%-10.4\textrm{f}\sqcup[%.4\textrm{f, }\sqcup%.4\textrm{f, }\sqcup%.4\textrm{f, }\sqcup%.4\textrm{f}]\sqcup(\mathrm{ 迭代数: }\sqcup%d)\n,,..
        lambda, x_opt(1), x_opt(2), x_opt(3), x_opt(4), iter);
end
% - 自定义 ADMM 求解函数 ---
function [x, k] = admm_solver(A, B, b, lambda)
    % ADMM 参数
    rho = 1.0; % 罚参数,影响收敛速度
    MAX_ITER = 1000; % 最大迭代次数
    TOL = 1e-6; % 收敛容差
    % 维度获取
    n = size (A, 2); %x的维度 (4)
    m= size(B, 1); %z 的维度 (3)
    % 初始化变量
    x = zeros(n, 1);
    z = zeros (m, 1);
    u = zeros (m, 1); % 对偶变量 (scaled dual variable)
    % 预计算矩阵 (避免循环中重复求逆)
    % x 更新公式:(}\mp@subsup{A}{}{\prime}A+rho*\mp@subsup{B}{}{\prime}B)*x=\ldots
    H = A'*A + rho*( ( }\mp@subsup{\textrm{B}}{}{\prime}*\textrm{B)}\mathrm{ ;
```

```
    I = eye(n);
    % 为了数值稳定性,可以用分解或左除,这里矩阵小直接求逆也可以,或者用 }H\
    for k = 1:MAX ITER
        % 1.x-update: 最小化二次函数
        % 求解线性方程组 }H*x=\mp@subsup{A}{}{\prime}b+rho*\mp@subsup{B}{}{\prime}*(z-u
        rhs = A'*b + rho * B'*(z - u);
        x = H \ rhs;
        % 2. z-update:软阈值算子 (Soft Thresholding)
        % v = Bx + u
        \mathrm { v } = \mathrm { B } \mathrm { * } \mathrm { x } \mathrm { + } \mathrm { u; }
        kappa = lambda / rho;
        % 软阈值操作: sign(v)* max(|v/-kappa, 0)
        z = (ign(v) .* max(abs(v) - kappa, 0);
        % 3.u-update: 对偶变量更新
        u = u + B * x - z;
        % 4. 收敛性检查(检查原始残差 r = Bx = z)
        r = B * x - z;
        if norm(r) < TOL
            break;
        end
    end
end
```


# 23363017；乐绎华；第 10 次作业 

乐绎华，Yue Yihua， 23363017
December 10， 2025

## Contents

0．1 Q1 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 1
0．2 Q2 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 2
0．3 Q3 ．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．．． 10

## 第十三周电子版作业

$\square \mathrm{Q} 1$ ．读取Q1．mat获得矩阵 $\boldsymbol{A}_{\mathbf{1 0 0 0} \times \mathbf{1 0 0 0}}$ ，其元素均为服从均匀分布 $\boldsymbol{U}(\mathbf{0}, \boldsymbol{\delta})$ 的样本，但参数 $\boldsymbol{\delta}>\mathbf{0}$ 未知。请推算并用MATLAB代码获得参数 $\boldsymbol{\delta}$ 的一阶矩估计和最大似然估计。请分别提供两种估计方法的推导过程、MATLAB代码和参数估计的结果。
$\square$ Q2．读取Q2．mat文件，里面包含 $3 \mathrm{x} 1, \mathrm{y} 1, \mathrm{x} 2, \mathrm{y} 2$ 共两组数据，它们分别近似对应了两种不同的函数的定义（y1，y2均有高斯噪声，y2有离群值），尝试通过今天学的cftool工具，分析和预测两个函数大概定义是什么。（高斯噪声无需去除）

□ Q3．某校某次期末考试，学生们的成绩分布比较散乱。现该校管理部门要求将学生的成绩调整为标准分（ $0{ }^{\sim} 100$ 分），使得分数尽量服从正态分布，期望为 80 分左右，区分度适中即可。请读取Q3．mat文件，文件里的向量score包含了一组原始分。请在作业中设计你自己提出的标准分换算方案（并指明理由，方案可以仅针对这一组特定的原始分），同时得到你的标准分结果。最后用histfit函数检验分布变化。

## 0．1 Q1

$$
X_{i} \sim U(0, \delta) \Rightarrow \bar{X} \sim U(0, \delta) \Rightarrow \mathbb{E}(\bar{X})=\frac{\delta}{2} \Rightarrow \widehat{\delta}_{M M E}=2 \bar{x}
$$

$$
\begin{gathered}
L(x, \delta)=\frac{1}{\delta^{n}} \mathbb{I}\left(X_{i} \in(0, \delta) ; \forall i\right)=\frac{1}{\delta^{n}} \mathbb{I}\left(\min X_{i} \geq 0, \max X_{i} \leq \delta\right) \\
\widehat{\delta}_{M L E}=\max X_{i}
\end{gathered}
$$

```
>> load('Q1.mat')
>> samples = A(:);
n = length(samples);
>> sample_mean = mean(samples);
delta_MME = 2 * sample__mean
delta_MME =
```

2.7197

```
>> delta_MLE = max(samples)
delta__MLE =
```

2.7180

```
    >> load('Q1.mat')
    >> samples = A(:);
    n = length(samples);
    >> sample_mean = mean(samples);
    delta_MME = 2 * sample_mean
    delta_MME =
        2.7197
    >> delta_MLE = max(samples)
    delta_MLE =
        2.7180
f(x >>
```


## 0．2 Q2

我这个版本（ 2024 b ）用不了 cftool。

$$
(\mathrm{x} 1, \mathrm{y} 1)
$$

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-094.jpg?height=736&width=1202&top_left_y=429&top_left_x=459)

## 2 项傅立叶拟合

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-094.jpg?height=735&width=1204&top_left_y=1347&top_left_x=459)

## 结果

傅里叶 曲线拟合（fourier2）

$$
\begin{aligned}
f(x)= & a 0+a 1^{*} \cos \left(x^{*} w\right)+b 1^{*} \sin \left(x^{*} w\right)+ \\
& a 2^{*} \cos \left(2^{*} x^{*} w\right)+b 2^{*} \sin \left(2^{*} x^{*} w\right)
\end{aligned}
$$

系数和 95\％置信边界

|  | 值 | 下限 | 上限 |
| :--- | ---: | ---: | ---: |
| $\mathbf{a 0}$ | 0.9907 | 0.9717 | 1.0096 |
| $\mathbf{a 1}$ | 0.0122 | -0.0179 | 0.0424 |
| $\mathbf{b 1}$ | 1.0051 | 0.9770 | 1.0333 |
| $\mathbf{a 2}$ | -0.0159 | -0.0616 | 0.0297 |
| $\mathbf{b 2}$ | 0.9746 | 0.9467 | 1.0025 |
| $\mathbf{w}$ | 1.0023 | 0.9982 | 1.0064 |

拟合优度

| SSE | 值 |
| :--- | ---: |
| R 方 | 0.7353 |
| DFE | 0.9921 |
| 调整 R 方 | 94.0000 |
| RMSE | 0.9917 |

## 3 项傅立叶拟合

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-096.jpg?height=755&width=1206&top_left_y=511&top_left_x=457)

## －结果

## 拟合名称：无标题拟合 1

## 傅里叶 曲线拟合（fourier3）

$f(x)=a 0+a 1^{*} \cos \left(x^{*} w\right)+b 1^{*} \sin \left(x^{*} w\right)+a 2^{*} \cos \left(2^{*} x^{*} w\right)+ b 2^{*} \sin \left(2^{*} x^{*} w\right)+a 3^{*} \cos \left(3^{*} x^{*} w\right)+b 3^{*} \sin \left(3^{*} x^{*} w\right)$

## 系数和 95\％置信边界

|  | 值 | 下限 | 上限 |
| :--- | :--- | :--- | :--- |
| a0 | 0.9931 | 0.9735 | 1.0127 |
| a1 | 0.0084 | －0．0235 | 0.0402 |
| b1 | 1.0036 | 0.9751 | 1.0320 |
| a2 | －0．0193 | －0．0681 | 0.0294 |
| b2 | 0.9775 | 0.9489 | 1.0060 |
| a3 | 0.0147 | －0．0142 | 0.0436 |
| b3 | 0.0005 | －0．0254 | 0.0264 |
| w | 1.0027 | 0.9985 | 1.0070 |

## 拟合优度

|  | 值 |
| :--- | ---: |
| SSE | 0.7271 |
| R 方 | 0.9922 |
| DFE | 92.0000 |
| 调整 R 方 | 0.9916 |
| RMSE | 0.0889 |

$$
(\mathrm{x} 2, \mathrm{y} 2)
$$

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-098.jpg?height=757&width=1208&top_left_y=425&top_left_x=455)

拟合名称：无标题拟合 2
多项式 曲线拟合（poly3）
$f(x)=p 1^{*} x^{\wedge} 3+p 2^{*} x^{\wedge} 2+p 3^{*} x+p 4$

## 系数和 95\％置信边界

|  | 值 | 下限 | 上限 |
| :--- | ---: | ---: | ---: |
| $\mathbf{p 1}$ | 0.4926 | 0.3801 | 0.6052 |
| $\mathbf{p 2}$ | 1.9072 | 1.6134 | 2.2011 |
| $\mathbf{p 3}$ | 1.2174 | -0.4450 | 2.8799 |
| $\mathbf{p 4}$ | 0.7447 | -1.9171 | 3.4066 |

## 拟合优度

|  | 值 |
| :--- | ---: |
| SSE | $8.8172 \mathrm{e}+03$ |
| R 方 | 0.8629 |
| DFE | 96 |
| 调整 R 方 | 0.8586 |
| RMSE | 9.5836 |

[^0]![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-100.jpg?height=759&width=1206&top_left_y=425&top_left_x=457)

## 使用指数模型拟合：

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-100.jpg?height=746&width=1204&top_left_y=1349&top_left_x=459)

综上，我们猜测（ $\mathrm{x} 1, \mathrm{y} 1$ ）是二项傅立叶

$$
f(x)=a_{0}+a_{1} \cos (x w)+b_{1} \sin (x w)+a_{2} \cos (2 x w)+b_{2} \sin (2 x w)
$$

$(\mathrm{x} 2, \mathrm{y} 2)$ 是三次多项式

$$
f(x)=a_{0}+a_{1} x+a_{2} x^{2}+a_{3} x^{3}
$$

## 0．3 Q3

我的方案：采用＂分位数映射法＂（Quantile Mapping／Inverse Normal Transformation）。
－原理：利用数据的＊＊排名（Rank）＊＊来确定其在正态分布中应处于的位置。这种方法可以强制将任意分布转换为正态分布。
－步骤：
1．计算每个分数的累积概率 $P=\frac{\operatorname{Rank}-0.5}{N}$ 。
2．通过标准正态分布的逆函数（norminv），找到对应的 $Z$ 值。
3．将 $Z$ 值映射到目标正态分布 $N\left(\mu, \sigma^{2}\right)$ 。

- 参数设定：
- 目标期望 $\mu=80$ 。
- 目标标准差 $\sigma$ ：为了保证绝大多数分数落在 $0 \sim 100$ 之间，且区分度适中。正态分布中 $\mu \pm 2 \sigma$ 覆盖 $95 \%$ 数据。若上限为 100 ，则 $80+2 \sigma \approx 100 \Rightarrow \sigma \approx 10$ 。设定 $\sigma=8 \sim 10$ 较为稳妥。

```
score = double(score(:));% 确保是列向量
N = length(score);
% 2. 方案设计:分位数映射法 (Rank-Based Inverse Normal Transformation)
% 目标参数
target_mean = 80;
target_std = 9; % 设定标准差为 9, 保证 (80+2*9=98) 仍在 100以内
% 步骤 A:计算排名 (处理并列名次,使用平均排名)
[~, sortIdx] = sort(score);
[~, rankIdx] = sort(sortIdx);
% 处理并列分数的排名 (可选优化,简单的 tiedrank 也可以)
% 这里为了演示原理, 直接用 tiedrank
ranks = tiedrank(score);
```

```
% 步骤 B: 计算累积概率 (CDF), 避免 0 和 1
%(Rank - 0.5)/ N 是一种常用的估算分位点的方法
probabilities = (ranks - 0.5) / N;
% 步骤 C: 映射到标准正态分布 N(0,1)
z_scores = norminv(probabilities, 0, 1);
% 步骤 D: 线性变换到目标分布 N(80, 9^2)
new_score = target_mean + z_scores * target_std;
% 步骤 E: 边界截断 (Clipping), 防止极个别数值溢出 0-100
new_score(new_score > 100) = 100;
new_score(new_score < 0) = 0;
% 3. 结果检验与可视化 (histfit)
figure('Name', 'Q3 成绩分布调整前后对比', 'Color','w');
% 襾原始分布
subplot(1, 2, 1);
histfit (score, 20);%20个柱子
title('原始成绩分布(可能很散乱)');
xlabel('分数'); ylabel('频数');
grid on;
% 画调整后分布
subplot(1, 2, 2);
h = histfit(new_score, 20);
title (['调整后成绩分布(目标 N(80,'num2str(target_std)'^2))']);
```

```
xlabel('分数'); ylabel('频数');
grid on;
% 强制显示范围 0-100 以便观察
xlim([0 100]);
% 输出统计信息
fprintf('=== 调整结果统计 == \n');
fprintf('原始均值:%.2f,原始标准差:%.2f\n',mean(score), std(score));
fprintf('新均值:%.2f,新标准差:%.2f\n',mean(new_score), std(new_score));
fprintf('新分数范围:[%.2f,%.2f]\n',min(new_score),max(new_score));
```

＞＞homework＿q3
＝＝＝调整结果统计＝＝＝
原始均值：70．29，原始标准差：23．31
新均值：79．96，新标准差： 8.90
新分数范围：［54．96，100．00］

Figure 1：Q3 成绩分布调整前后对比
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-104.jpg?height=46&width=1159&top_left_y=489&top_left_x=481)

Figure 1：Q3 成绩分布调整前后对比
![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-104.jpg?height=875&width=514&top_left_y=614&top_left_x=541)

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-104.jpg?height=862&width=511&top_left_y=614&top_left_x=1069)

## 23363017；乐绎华；第 11 次作业

乐绎华，Yue Yihua， 23363017
December 16， 2025

## Contents

1 Q 1 ..... 2
1.1 1．均值滤波（Mean Filtering）：卷积与低通滤波器 ..... 5
1．1．1 时域视角：离散卷积 ..... 5
1．1．2 频域视角：Sinc函数的低通特性 ..... 6
1.2 2．FFT 阈值去噪：正交投影与稀疏性 ..... 6
1．2．1 线性代数视角：基变换 ..... 6
1．2．2 信号与噪声的几何分离 ..... 6
1．2．3 阈值操作：子空间投影 ..... 7
1.3 3．哲学与直观总结 ..... 7
2 Q 2 ..... 9

## 第十四周电子版作业

□ Q1．设 $f(x)=\cos 2 x, x \in[0,2 \pi]$ ，假设采样间距为 $\frac{\pi}{50}$ 。类似于今天的例题，设 $\boldsymbol{y}(\boldsymbol{x})=\boldsymbol{f}(\boldsymbol{x})+\boldsymbol{\epsilon}$ ，在设定 rng default后，设 $\epsilon$ 为标准差为 0.1 的正态分布（高斯）噪声。图示并分析 $f(x)$ 与 $y(x)$ 的离散傅里叶变换，而后使用均值滤波法、傅里叶系数阈值法进行去噪，无需使用其他方法。
（写出代码、图示、去噪信噪比结果以及原因解释）
□ Q2．（有额外加分，必做）参照Maryslamb．m文件，加入自己的乐谱或音符（乐理知识不足的可以做简单的曲子如《小星星》、《两只老虎》等），可用音叉音、借用现有钢琴音 （老师会提供一种）、借用其他音源的音色、设计方波三角波等模拟音色，或自己合成其他音色，完成一段音乐的制作。
－鼓励大家积极创作多音色或多声部的作品，并在文档里注明你的设计方法。（提示：可用新版MATLAB声音工具箱中的 shiftPitch、stretchAudio函数快速生成合适音符）

## 1 Q 1

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-106.jpg?height=759&width=1204&top_left_y=550&top_left_x=459)

在相同真实信号的情况下，信噪比（SNR）越高，信号质量越高。
\％\％Q1：信号处理与去噪分析
clc；clear；close all；
$\%$ —— 1．信号生成——
dx＝pi／ 50 ；
$\mathrm{x}=0: \mathrm{dx}: 2 * \mathbf{p i} ; \%$ 采样点
$\mathrm{N}=\operatorname{length}(\mathrm{x}) ; \%$ 数据长度（101点）
$\mathrm{f}=\boldsymbol{\operatorname { c o s }}(2 * \mathrm{x}) ; \%$ 原始信号
\％—— 2．添加噪声 ——
rng（＇default＇）；\％设定随机数种子，保证结果可复现
sigma＝0．1；
epsilon $=\operatorname{sigma} * \operatorname{randn}(1, N) ; \%$ 标准差为 0.1 的高斯噪声

```
y = f + epsilon; % 含噪信号
% -- 3. 离散傅里叶变换 (DFT) 分析 ---
% 对含噪信号进行FFT
Y_fft = fft (y);
freq_axis = 0:N-1;% 频率轴 (以索引表示)
% - 4. 去噪方法 A: 均值滤波 (Moving Average) - -
window_size = 5;% 设定窗口大小,通常3-7之间
y_mean = movmean(y, window__size);
% -- 5. 去噪方法 B: 傅里叶系数阈值法 (Fourier Thresholding) --
% 计算幅度谱
mag_spectrum = abs(Y_fft);
% 设定间值:
% 观察可知信号能量极强(N/2 approx 50),噪声能量较低且分散。
% 设定一个能够保留主峰但滤除底部噪声的间值(例如15)
threshold = 15;
% 阈值操作:低于阈值的系数置零
Y_fft_thresh = Y_fft;
Y_fft__thresh(mag_spectrum < threshold) = 0;
% 逆变换回时域 (取实部)
y_fft_denoised = real(ifft(Y_fft_thresh));
% - 6. 计算信噪比 (SNR) - 
% 定义SNR函数: 10* log10(信号功率 / 噪声功率)
```

```
calc_snr = @(sig_clean, sig_noisy) 10 * log10(sum(sig_clean.^2) / sum((sig_clean
snr_noisy = calc_snr(f, y);
snr_mean = calc_snr(f, y_mean);
snr_fft = calc_snr(f, y_fft__denoised);
% 输出结果到命令行
fprintf('- — 信噪比 (SNR) 结果 _ — \ n');
fprintf(,1.⿱亠原始含噪信号 \sqcupSNR: }\leftarrow%.2\mp@subsup{f}{\sqcupdB}{}\n,,snr_noisy)
fprintf('2.u均值滤波后 \sqcupSNR: s%.2f sdB \ n', snr_mean);
```

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-108.jpg?height=46&width=1077&top_left_y=1155&top_left_x=464)

```
%-- 7. 绘图展示 -
figure('Position', [100, 100, 1000, 800], 'Color', 'w');
% 图1:时域对比
subplot(2, 2, 1);
plot(x, f, 'k-', 'LineWidth', 1.5); hold on;
plot(x, y, 'Color', [0.7, 0.7, 0.7]);
title('原始信号 }\textrm{f}(\textrm{x})\sqcup\mathrm{ 与 含噪信号 }\textrm{y}(\textrm{x})\prime)
legend('Clean', 'Noisy'); grid on;
% 图2:频域分析 (FFT 幅度谱)
subplot(2, 2, 2);
stem(freq_axis, abs(fft(f)), 'k', 'LineWidth', 1.5, 'Marker', 'none'); hold on;
stem(freq_axis, abs(fft(y)), 'r-_');
yline(threshold, 'b-', 'Threshold');
```

```
title('离散傅里叶变换 }\cup(\textrm{DFT)}\sqcup\mathrm{ 幅度谱');
legend('f(x)\sqcupSpectrum', 'y(x)\sqcupSpectrum', 'Threshold'); grid on;
xlabel('Frequency\sqcupIndex'); ylabel('Magnitude');
% 图3:均值滤波结果
subplot(2, 2, 3);
plot(x, f, 'k-', 'LineWidth', 1); hold on;
plot(x, y_mean, 'b', 'LineWidth', 1.5);
title(['均值滤波\cup(Window=5), \SNR=' num2str(snr_mean,'%.2f')'dB']);
legend('Original', 'Filtered'); grid on;
% 图4: FFT阈值去噪结果
subplot(2, 2, 4);
plot(x, f, 'k-', 'LineWidth', 1); hold on;
plot(x, y_fft_denoised, 'r', 'LineWidth', 1.5);
title([ 'FFT阈值去噪, _SNR=' num2str(snr_fft, '%.2f') 'dB']);
legend('Original', 'Filtered'); grid on;
```


### 1.1 1．均值滤波（Mean Filtering）：卷积与低通滤波器

从数学上讲，均值滤波不仅仅是＂求平均＂，它是一个线性时不变（LTI）系统。

## 1．1．1 时域视角：离散卷积

设输入信号为 $y[n]$ ，滤波核（Kernel）为 $h[n]$ 。对于窗口大小为 $M$ 的均值滤波， $h[n]$ 是一个矩形窗函数（Rectangular Window）：

$$
h[n]= \begin{cases}\frac{1}{M}, & 0 \leq n<M \\ 0, & \text { otherwise }\end{cases}
$$

滤波后的信号 $\hat{y}$ 是 $y$ 与 $h$ 的卷积：

$$
\hat{y}[n]=(y * h)[n]=\sum_{k=0}^{M-1} \frac{1}{M} y[n-k]
$$

## 1．1．2 频域视角：Sinc 函数的低通特性

根据卷积定理，时域的卷积等于频域的乘积：

$$
\mathscr{F}\{\hat{y}\}=\mathscr{F}\{y\} \cdot \mathscr{F}\{h\}
$$

这里 $\mathscr{F}\{h\}$ 是矩形窗的傅里叶变换，其结果是 Dirichlet 核（类似于 sinc函数）：

$$
H(\omega)=e^{-j \omega(M-1) / 2} \cdot \frac{\sin (\omega M / 2)}{M \sin (\omega / 2)}
$$

## 数学解释 22.09 dB 的由来：

1．低通滤波：$|H(\omega)|$ 在低频处接近 1，在高频处衰减。因为你的信号 $\cos (2 x)$是极低频信号，大部分通过；而白噪声 $\epsilon$ 遍布全频段，高频部分的噪声被 $|H(\omega)|$ 压制了。
2．为何不够完美？：注意看 sinc 函数的图像，它不是理想的＂矩形＂低通滤波器。

- 旁瓣泄漏（Side lobes）：它无法将高频噪声完全降为 0 。
- 主瓣衰减：在信号所在的频率点，增益可能略小于 1 ，导致原始信号也被稍微＂削弱＂了一点（这就是为什么图像变平滑，峰值可能会略微降低）。
－这就解释了为什么它只能提升到 22 dB ，因为它在杀敌（噪声）一千的同时，自损（信号）八百。


### 1.2 2．FFT 阈值去噪：正交投影与稀疏性

FFT 方法在数学上要优美得多，因为它利用了信号在特定基底下的稀疏性 （Sparsity）。

## 1．2．1 线性代数视角：基变换

我们将信号看作 $\mathbb{C}^{N}$ 空间中的一个向量。傅里叶变换实际上是进行了一次正交基变换。

设傅里叶基为 $\left\{e_{k}\right\}$ ，任何信号 $y$ 可以表示为：

$$
y=\sum_{k=0}^{N-1} c_{k} e_{k}
$$

其中 $c_{k}$ 是傅里叶系数。

## 1．2．2 信号与噪声的几何分离

－信号 $f(x)=\cos (2 x)$ ：在这个基底也就是频域下，它是极度稀疏的。它只在 $k$ 对应频率为 2 的两个分量上有值，其余全为 0 。也就是它只占据了 $N$维空间中的 2 个维度。
－噪声 $\epsilon$ ：高斯白噪声的能量在正交变换下是守恒且均匀分布的（Parseval定理）。噪声向量分散在所有 $N$ 个维度上，每个维度上的分量都很小。

## 1．2．3 阈值操作：子空间投影

阈值去噪在数学上等价于寻找一个最佳逼近子空间。
设定阈值 $T$ ，我们定义新的系数：

$$
\hat{c}_{k}= \begin{cases}c_{k}, & \left|c_{k}\right|>T \\ 0, & \left|c_{k}\right| \leq T\end{cases}
$$

## 数学解释 26.62 dB 的由来：

1．Oracle 属性：因为 $\cos (2 x)$ 的能量非常集中，远超噪声水平，我们可以极其精准地保留信号所在的 2 个维度，而将其他 $N-2$ 个维度（纯噪声维度）全部强制置零。
2．信噪比提升极限：

- 原始噪声功率分布在 $N$ 个维度。
- 去噪后，我们实际上剔除了 $N-2$ 个维度的噪声能量。
- 如果 $N=100$ ，粗略计算噪声方差减少了约 $\frac{N}{2}=50$ 倍（假设保留了 2 个点）。
- $10 \log _{10}(50) \approx 17 \mathrm{~dB}$ 的提升空间。
- 实际上由于有些噪声叠加在信号频率上无法去除，提升约为 $10-11$ dB （从 15.74 到 26.62 ），这是非常接近理论极限的效果。


### 1.3 3．哲学与直观总结

为了回应你作为数学系学生的直觉，我们可以这样总结这三个数值的跳跃：

| 方法 | 数学本质 |  |  |  | 哲学／直邓 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 原始数据 | $y=f+\epsilon$ |  |  |  | 混沌：真理（信号）被 |
| 均值滤波 | $y * h$（卷积） |  | 中庸／妥协：通过把周围的东西＂抹匀＂来消除极端值。它认隿 |  |  |
| FFT 阈值 | $\operatorname{Proj}_{S}(y)$（投影） |  | 本质／洞察：它不试图修补表象，而是转换视角（变换基底），找到真理存在 |  |  |

结论：FFT 方法之所以在这个问题上大胜，是因为我们选对了这个世界的 ＂基＂。对于周期信号，傅里叶基就是它的＂本征基＂。在正确的坐标系下，问题会变得微不足道。

## 2 Q 2

![](https://cdn.mathpix.com/cropped/fd3e8802-c4ff-4115-92b8-f8b54f071bdc-113.jpg?height=1892&width=1202&top_left_y=545&top_left_x=459)

```
粉刷匠
%% Matlab版《粉刷匠》 (Debugged & Optimized)
% Coding style: Classical / Explicit Variables
clear; clc;
%% 1. 基础参数定义 (Basic Setup)
fs = 44100; % 采样率
BPM = 120; % 速度: 120拍/分钟
SamplesPerBeat = floor (fs * 60 / BPM);
% 定义标准时值对应的采样点数
N_e = round(SamplesPerBeat / 2); % 八分音符 (基准)
%% 2. 乐谱变量定义 (Variable Definition)
% 我们不再使用匿名函数,而是调用底部的 local function'get_note_wave'
% 参数说明:get_note_wave (八度,音阶序号,时值类型, fs, N_e)
% —— 常用音符预生成 ——
% 时值类型: 1=八分 (e), 2=四分(q), 3=二分(h)
% 中音区 (Middle)
do_e = get_note_wave(0,1,1, fs, N_e); do_q = get_note_wave(0,1,2, fs, N_e); do_h
re__e = get_note_wave(0,2,1, fs, N_e); re_q = get_note_wave(0,2,2, fs, N_e);
mi_e = get_note_wave(0,3,1, fs, N_e); mi_q = get_note_wave( 0,3,2, fs, N_e);
fa_e = get_note_wave(0,4,1, fs, N_e); fa_q = get_note_wave( 0,4,2, fs, N_e);
so_e = get_note_wave(0,5,1, fs, N_e); so_q = get_note_wave(0,5,2, fs, N_e); so_h
la_e = get_note_wave(0,6,1, fs, N_e); la_q = get_note_wave( 0,6,2, fs, N_e);
% 低音区 (Low) - 左手伴奏
L_so_e = get_note_wave( - 1, 5,1, fs, N_e); % 低音5
L_la_e = get_note_wave( - 1, 6, 1, fs, N_e); % 低音 }
L_si_e = get_note_wave( - 1, 7,1, fs, N_e); % 低音7
L_do_e = get_note_wave( - 1, 1, 1, fs, N_e); % 低音1
L_re_e = get_note_wave( - 1, 2,1, fs, N_e); % 低音2
L_mi_e = get_note_wave( - 1, 3,1, fs, N_e); % 低音3
L_fa_e = get_note_wave( - 1, 4,1, fs, N_e); % 低音4
% 休止符
rest_e = zeros(1, N_e);
rest_q = zeros(1, N_e*2);
%% 3. 乐谱编排 (Transcription)
% === 右手 (Right Hand - Melody) ===
```

```
% Meas 1-4
rh1 = [so_e mi_e so_e mi_e];
rh2 = [so_e mi_e do_q];
rh3 = [re_e fa_e mi_e re_e];
rh4 = [so_n];
% Meas 5-8
rh5 = rh1; rh6 = rh2; rh7 = rh3; rh8 = rh4;
% Meas 9-12
rh9 = [re_e re_e fa_e fa_e];
rh10 = [mi_e do_e so_q];
rh11 = [re_e fa_e mi_e re_e];
rh12 = [so_h];
% Meas 13-16
rh13 = rh1;
rh14 = rh2;
rh15 = rh3;
rh16 = [do_h];
RH_Full = [rh1 rh2 rh3 rh4 rh5 rh6 rh7 rh8 rh9 rh10 rh11 rh12 rh13 rh14 rh15 rh1
% === 左手 (Left Hand - Accompaniment) ===
lh_pat1 = [L_do_e L_mi_e L_mi_e L_mi_e]; % 1 3 3 3
lh_pat2 = [L_si_e L_re_e L_re_e L_re_e]; % 7 2 2 2
lh_pat3 = [L_si_e L_fa_e L_fa_e L_fa_e]; % 7 4 4 4 (修正为444)
% Meas 1-4
lh1 = lh_pat1; lh2 = lh_pat1; lh3 = lh_pat2; lh4 = lh_pat3;
% Meas 5-8
lh5 = lh1; lh6 = lh2; lh 7 = lh 3; lh 8 = lh4;
% Meas 9-12
lh9 = [L_so__e L_so_e L_so_e L_so_e]; % 5 5 5 5
lh10 = lh_pat1;
lh11 = lh_pat2;
lh12 = [L__so_e L__so_e L_so_e L_so_e]; % 5 5 5 5
% Meas 13-16
lh13 = lh_pat1; lh14 = lh_pat1; lh15 = lh_pat2;
lh16 = [L_do_e L__so_e L_mi_e L_so__e]; % 15 3 5
LH_Full = [lh1 lh2 lh3 lh4 lh5 lh6 lh7 lh8 lh9 lh10 lh11 lh12 lh13 lh14 lh15 lh1
%% 4.混音 (Mixing)
len = min(length(RH_Full), length(LH_Full));
```

```
Song = RH_Full(1:len) * 0.8 + LH_Full(1:len) * 0.5;
Song = Song / max(abs(Song)); % 归一化
%% 5. 播放
sound(Song, fs);
audiowrite('LittlePainter_Fixed.wav',Song, fs);
%% === 底部局部函数(Local Function)===
% 将逻辑判断放在这里,避免数组维度不一致的问题
function w = get_note_wave(oct, scale_idx, dur_type, fs, N_e)
    % 1. 定义频率
    f_do = 261.63;
    Scale = [1, 2^(2/12), 2^(4/12), 2^(5/12), 2^(7/12), 2^(9/12), 2^(11/12)];
    freq = f_do * 2^oct * Scale(scale_idx);
    % 2. 根据 dur_type 动态计算 N和 t
    if dur_type ==1 % 八分音符
        N = N_e;
    elseif dur_type == 2 % 四分音符
        N = N_e * 2;
    elseif dur_type == 3 % 二分音符
        N = N_e * 4;
    else
        N = N_e;
    end
    t = (0:N-1)/fs;
    % 3. 生成包络 (Envelope)
    env = sin(pi * t / t(end));
    % 4. 生成波形
    w = env .* cos(2* pi * freq * t);
end
```


# 23363017；乐绎华；第 12 次作业 

乐绎华，Yue Yihua， 23363017
December 22， 2025

## Contents

## 第十五周电子版作业

□ Q1．习题4第17题（写出MATLAB源代码与运行结果）
已知有理分式 $R(x)=\frac{N(x)}{D(x)}$ ，其中 $N(x)=\left(3 x^{3}+x\right)\left(x^{3}+0.5\right), D(x)=\left(x^{2}+2 x-2\right)\left(5 x^{3}+2 x^{2}+1\right)$ 。（1）求该分式的商多项式 $Q(x)$ 和余多项式 $r(x)$ 。（2）用程序验算 $D(x) Q(x)+r(x)=N(x)$ 是否成立。（提示：采用范数指令 norm 验算。）
□ Q2．设信号 $\boldsymbol{x}(\boldsymbol{t})=\frac{\mathbf{1}}{\sqrt{\mathbf{2} \boldsymbol{\pi}} \boldsymbol{\sigma}} \boldsymbol{e}^{-\frac{\boldsymbol{t}^{\mathbf{2}}}{\mathbf{2} \boldsymbol{\sigma}^{\mathbf{2}}}},-\mathbf{2} \leq \boldsymbol{t} \leq \mathbf{2}, \boldsymbol{y}(\boldsymbol{t})=\left\{\begin{array}{l}\mathbf{1},|\boldsymbol{t}| \leq \mathbf{1} \\ \mathbf{0},|\boldsymbol{t}|>\mathbf{1}\end{array}\right.$为矩形脉冲函数，现用数值方法模拟两个具有紧支集函数的卷积结果，采样步长设置 $\mathbf{1} \times \mathbf{1 0}^{-4}$ ，而参数 $\boldsymbol{\sigma}=\mathbf{0}$ ． $\mathbf{1}$ 。写出你定义＂离散化＂的数字信号以及计算离散卷积 $\boldsymbol{x}(\boldsymbol{t}) * \boldsymbol{y}(\boldsymbol{t})$ 的代码，并提供绘图结果。根据你的计算或绘图结果，一个光滑信号 $\boldsymbol{x}(\boldsymbol{t})$ 与粗糙信号 $\boldsymbol{y}(\boldsymbol{t})$ 的卷积结果 $\boldsymbol{x}(\boldsymbol{t}) * \boldsymbol{y}(\boldsymbol{t})$ 是光滑
（高阶可导）的还是粗糙的？ $\boldsymbol{\sigma \rightarrow 0}$ 时， $\boldsymbol{x}(\boldsymbol{t}) * \boldsymbol{y}(\boldsymbol{t})$ 会有什么变化，请尝试解释之。

## 第十五周电子版作业

$\square \mathrm{Q} 3$ ．购物问题的升级：仍然假设某商店共有 $\boldsymbol{n}$ 件不同的商品，其中前 $\boldsymbol{m}$ 件物品为特殊物品， $\mathbf{1}<\boldsymbol{m}<\boldsymbol{n}$ 。每件商品的价格是 $\boldsymbol{c}_{\boldsymbol{i}}$ 元，且 $c_{i} \in \mathbb{N}_{+}$，每件商品的性能值为 $\boldsymbol{v}_{\boldsymbol{i}}$ 元。现你手上共有 $\boldsymbol{C}$元（ $\boldsymbol{C} \mathbf{2 0 0 0}$ ），并要求至少购买一件特殊物品，问如何购买可以使你购买物品的总性能值最大？（数据保证至少有一组解，每件物品都可以选择买或不买但都仅有 1 件， $\boldsymbol{v}_{\boldsymbol{i}}>\mathbf{0}$ ）

□ 读取数据文件Q31．mat，Q32．mat，Q33．mat，Q34．mat可以分别获得四组不同的数据。每一组分别包含常数 $\boldsymbol{m}, \boldsymbol{n}, \boldsymbol{C}$ ，价格与性能向量 $\overrightarrow{\boldsymbol{c}}, \overrightarrow{\boldsymbol{v}}_{\text {。 }}$

□ 请将你的算法解释、代码、运行结果包含在作业之中。本题仅需计算出最佳购买方案的总性能值，无需提供具体购买方案。建议使用fprintf命令对结果进行展示。


[^0]:    ＂稳健＂选用：LAR，之前什么都没有用．

