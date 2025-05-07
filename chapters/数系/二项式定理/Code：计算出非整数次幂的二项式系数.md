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