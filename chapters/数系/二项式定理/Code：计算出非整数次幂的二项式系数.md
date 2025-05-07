# Code：计算出非整数次幂的二项式系数

## 打开实验文件

### 在线调试环境

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。


```python
from math import gamma

def generalized_binomial_coefficient(n, k):
    return gamma(n + 1) / (gamma(k + 1) * gamma(n - k + 1))

# 示例
n, k = 5.5, 2
print(generalized_binomial_coefficient(n, k))  # 输出一个浮点数
```

### 计算出非整数次幂的二项式的数值
```python
import math
from math import gamma

def generalized_binomial_coefficient(n, k):
    return gamma(n + 1) / (gamma(k + 1) * gamma(n - k + 1))

n = 1/2
coefficient_1 = generalized_binomial_coefficient(n, 0)
coefficient_2 = generalized_binomial_coefficient(n, 1)
coefficient_3 = generalized_binomial_coefficient(n, 2)
coefficient_4 = generalized_binomial_coefficient(n, 3)
coefficient_5 = generalized_binomial_coefficient(n, 4)
coefficient_6 = generalized_binomial_coefficient(n, 5)
coefficient_7 = generalized_binomial_coefficient(n, 6)
coefficient_8 = generalized_binomial_coefficient(n, 7)
coefficient_9 = generalized_binomial_coefficient(n, 8)

a = 1
b = 0.25
print(math.pow((a + b),n))

item1 = coefficient_1 * math.pow(a,n) * math.pow(b,0)
item2 = coefficient_2 * math.pow(a,n-1) * math.pow(b,1)
item3 = coefficient_3 * math.pow(a,n-2) * math.pow(b,2)
item4 = coefficient_4 * math.pow(a,n-4) * math.pow(b,3)
item5 = coefficient_5 * math.pow(a,n-5) * math.pow(b,4)
item6 = coefficient_6 * math.pow(a,n-6) * math.pow(b,5)
item7 = coefficient_7 * math.pow(a,n-7) * math.pow(b,6)
item8 = coefficient_8 * math.pow(a,n-8) * math.pow(b,7)
item9 = coefficient_9 * math.pow(a,n-9) * math.pow(b,8)

sum1 = item1+item2
print(sum1)
sum2 = sum1+item3
print(sum2)
sum3 = sum2+item4
print(sum3)
sum4 = sum3+item5
print(sum4)
sum5 = sum4+item6
print(sum5)
sum6 = sum5+item7
print(sum6)
sum7 = sum6+item8
print(sum7)
sum8 = sum7+item9
print(sum8)
```

```python
import math
from math import gamma

def generalized_binomial_coefficient(n, k):
    return gamma(n + 1) / (gamma(k + 1) * gamma(n - k + 1))

n = 1/2
a = 1
b = 0.25

print(math.pow((a + b), n))

# 使用列表生成式计算系数
coefficients = [generalized_binomial_coefficient(n, k) for k in range(9)]

# 计算各项并求和
items = [coefficients[k] * math.pow(a, n - k) * math.pow(b, k) for k in range(9)]
sum_result = sum(items)

print(sum_result)
```