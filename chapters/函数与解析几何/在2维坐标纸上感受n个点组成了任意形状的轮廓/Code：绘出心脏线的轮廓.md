# Code：在线绘出心脏线的轮廓

## 打开实验文件

### 在线调试环境1

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### 心脏线
```python
import numpy as np
from matplotlib import pyplot as plt

radian = np.linspace(0, 2*np.pi, 18)

r = 5 - 5 * np.sin(radian)

plt.polar(radian, r, 'r')
plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Cardioid](https://en.wikipedia.org/wiki/Cardioid) 
	- [心脏线](https://zh.wikipedia.org/wiki/%E5%BF%83%E8%84%8F%E7%BA%BF) 

2. [Python Program to Plot Cardioid Curve](https://www.codesansar.com/python-programming-examples/plot-cardioid-curve.htm)
3. [心脏线](https://baike.baidu.com/item/%E5%BF%83%E8%84%8F%E7%BA%BF/10323843?fromtitle=%E5%BF%83%E5%BD%A2%E7%BA%BF&fromid=10018818)