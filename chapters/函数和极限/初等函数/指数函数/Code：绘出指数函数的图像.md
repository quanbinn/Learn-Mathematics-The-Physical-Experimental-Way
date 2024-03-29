# Code：绘出指数函数与对数函数的图像

## 打开实验文件

### 在线调试环境1

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### y = e<sup>x</sup>

```python
import numpy as np
import math
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

print(math.e)

x = np.linspace(0,1,21)
print(x)
y = math.e**x
print(y)

plt.scatter(x,y)
plt.show()
```

### y = log<sub>e</sub>x

```python
import numpy as np
import math
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

print(math.e)

x = np.linspace(0,math.e,21)
print(x)
y = np.log(x)
print(y)

plt.scatter(x,y)
plt.show()
```

## 参考文献及资料

1. [math.log(x[, base]) from **docs.python.org**](https://docs.python.org/3/library/math.html)
2. [Python math.log() Method](https://www.w3schools.com/python/ref_math_log.asp) 
3. [numpy.log](https://numpy.org/doc/stable/reference/generated/numpy.log.html) 
