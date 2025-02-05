# Code：枚举出每一个排列和组合的集合

## 打开实验文件

### 在线调试环境

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

#### 排列
```python
from itertools import permutations
seq = permutations([2,0,1,9,20,19])
print(seq)
for p in list(seq):
   print(p)
```

#### 组合
```python

```

## 参考文献及资料

1. [在Python中的排列组合](https://deepinout.com/python/python-top-articles-python/1694866127_j_permutation-and-combination-in-python.html)
2. [Python 高效计算组合和排列](https://geek-docs.com/python/python-ask-answer/303_python_counting_combinations_and_permutations_efficiently.html)