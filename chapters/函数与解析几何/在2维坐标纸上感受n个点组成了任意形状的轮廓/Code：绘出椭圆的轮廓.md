# Code：在线绘出椭圆的轮廓

## 打开实验文件

### 在线调试环境1

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单机右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### 椭圆形
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

angle = np.linspace(0,360,13)
print(angle)

x =0 + 10 * np.cos(np.radians(angle)) # 15 is the major axis of ellipse
y =0 + 5 * np.sin(np.radians(angle)) # 5 is minor axis of ellipse

plt.scatter(x,y) 
plt.show()
```

```python
import numpy as np
from matplotlib import pyplot as plt
from math import pi
plt.gca().set_aspect( 1 ) 

u = 4     # x-position of the center
v = 3    # y-position of the center
a = 10     # radius on the x-axis
b = 5    # radius on the y-axis

radian = np.linspace(0, 2*pi, 35)

plt.grid(color='lightgray',linestyle='--')

plt.scatter( u + a*np.cos(radian) , v + b*np.sin(radian) )
plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Ellipse](https://en.wikipedia.org/wiki/Ellipse) 
	- [椭圆](https://zh.wikipedia.org/wiki/%E6%A4%AD%E5%9C%86) 

2. [Plot Ellipse with matplotlib.pyplot (Python)](https://stackoverflow.com/questions/10952060/plot-ellipse-with-matplotlib-pyplot-python)
3. [How to Plot ellipse in python](https://www.engineerknow.com/2021/03/how-to-plot-ellipse-in-python.html)