# Code：绘出圆的轮廓

## 打开实验文件

### 在线调试环境1

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### 圆形
```python
import numpy as np 
import matplotlib.pyplot as plt 
plt.gca().set_aspect( 1 ) 
 
radian = np.linspace( 0 , 2 * np.pi , 13 ) 
radius = 10
 
x = radius * np.cos( radian ) 
y = radius * np.sin( radian ) 

plt.scatter( 0 + x, 0 + y ) # add the x and y value of center point 
# plt.scatter( 5 + x, 5 + y ) # add the x and y value of center point 
plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Circle](https://en.wikipedia.org/wiki/Circle) 
	- [圆](https://zh.wikipedia.org/wiki/%E5%9C%86)  

2. [6 Ways to Plot a Circle in Matplotlib](https://www.pythonpool.com/matplotlib-circle/)