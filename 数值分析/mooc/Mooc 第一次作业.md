# Mooc 第一次作业

### 1

根据求根公式
$$
x = \frac {-b\pm \sqrt{b^2-4ac}} {2a}
$$
可得原方程$x^2 - 24x+8 =0$的解为
$$
x = \frac {24\pm\sqrt{24^2-4*1*8}} {2} = 12\pm\sqrt{136}, \sqrt{136}\approx11.662
$$
即
$$
\left\{  
             \begin{array}{**lr**}  
             x_1=12+\sqrt{136}\approx23.662\\
             x_2 =12-\sqrt{136}\approx0.338,仅有三位有效数字\\
             \end{array}  
\right.
$$
根据维达定理有：
$$
x_1+x_2 = \frac c a = 8\\
$$
故可得:
$$
x_2 = \frac 8 x_1 = 8/23.662\approx0.338094
$$
综上述，所有结果保留四位有效数字得:
$$
\left\{  
             \begin{array}{**lr**}  
             x_1=23.66\\
             x_2 =0.3380\\
             \end{array}  
\right.
$$

### 2

$$
x^* =\pi \approx3.14159=0.314159\times10^1
$$

所以有
$$
\varepsilon_1 = |x^*-x_1|\approx0.00059 \\
0.5\times10^{-3}\leq\varepsilon_1 \leq0.5\times10^{-2}
$$
故$x_1=3.141$有3位有效数字

同理有
$$
\varepsilon_1 = |x^*-x_2|\approx0.00041 \\
\varepsilon_1 \leq0.5\times10^{-3}
$$
故$x_2 = 3.1412$有4位有效数字

综上所述$x_1$有3位有效数字，$x_2$有4位有效数字

### 3

设需要$n$位有效数字，根据相对误差定义：
$$
\varepsilon_r = \frac {|x^*-x|} {|x|}\le0.01\%
$$
由于$x=\sqrt{10}\le3.2=0.32\times10^1$：
$$
\varepsilon \le0.01\%|x|\le0.32\times10^{1-4}\le0.5\times10^{1-n}
$$
可得$n=4$，故需要取4位有效数字