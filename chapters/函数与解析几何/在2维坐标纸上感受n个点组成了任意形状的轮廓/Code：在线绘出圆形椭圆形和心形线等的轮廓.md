# Code：在线绘出圆形椭圆形和心形线等的轮廓

## 打开实验文件

### 在线调试环境1

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单机右方的[Python Online Compiler](https://www.alphacodingskills.com/compile-python-online.php)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面“Run Code”下侧的深蓝色的空白栏中， 然后单击上方的按键“Run Code”。

### 圆形
```python
import numpy as np 
import matplotlib.pyplot as plt 
 
angle = np.linspace( 0 , 2 * np.pi , 35 ) 
radius = 0.4
 
x = radius * np.cos( angle ) 
y = radius * np.sin( angle ) 

plt.gca().set_aspect( 1 ) 

plt.scatter( x, y ) 
plt.show()
```

### 椭圆形
```python
import numpy as np
from matplotlib import pyplot as plt
from math import pi

u=1.     #x-position of the center
v=0.5    #y-position of the center
a=2.     #radius on the x-axis
b=1.5    #radius on the y-axis

t = np.linspace(0, 2*pi, 100)
plt.scatter( u+a*np.cos(t) , v+b*np.sin(t) ) # plt.plot( u+a*np.cos(t) , v+b*np.sin(t) ) 
plt.grid(color='lightgray',linestyle='--')
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

t = np.linspace(0,360,360)

x =10*np.cos(np.radians(t)) #10 is minor axis of ellipse
y = 50*np.sin(np.radians(t)) #50 is major axis of ellipse

plt.scatter(x,y) # plt.plot(x,y)
plt.show()
```

## 参考文献及资料

1. [Plot Ellipse with matplotlib.pyplot (Python)](https://stackoverflow.com/questions/10952060/plot-ellipse-with-matplotlib-pyplot-python)
2. [How to Plot ellipse in python](https://www.engineerknow.com/2021/03/how-to-plot-ellipse-in-python.html)
3. [6 Ways to Plot a Circle in Matplotlib](https://www.pythonpool.com/matplotlib-circle/)


