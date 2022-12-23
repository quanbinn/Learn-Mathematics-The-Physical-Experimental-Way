# Code：在线绘出线段

## 打开实验文件

### 在线调试环境1

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单机右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### y = -2x
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

x = np.linspace(start = -5, stop = 5, num = 6)
print(x)
y = -2*x
print(y)

plt.scatter(x, y) # plt.plot(x,y)
plt.show()
```

### y = 2x
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

x = np.linspace(start = -5, stop = 5, num = 6)
print(x)
y = 2*x
print(y)

plt.scatter(x, y) # plt.plot(x,y)
plt.show()
```

### y = x + 5
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

x = np.linspace(start = -5, stop = 5, num = 6)
print(x)
y = x + 5
print(y)

plt.scatter(x, y) # plt.plot(x,y)
plt.show()
```

## 参考文献及资料

1. [matplotlib：tutorials](https://matplotlib.org/tutorials/index.html)
2. [Pyplot tutorial](https://matplotlib.org/3.1.1/tutorials/introductory/pyplot.html#sphx-glr-tutorials-introductory-pyplot-py)
3. [matplotlib.pyplot.gca](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.gca.html)
4. [matplotlib.axes.Axes.set_aspect](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.axes.Axes.set_aspect.html#matplotlib.axes.Axes.set_aspect)


