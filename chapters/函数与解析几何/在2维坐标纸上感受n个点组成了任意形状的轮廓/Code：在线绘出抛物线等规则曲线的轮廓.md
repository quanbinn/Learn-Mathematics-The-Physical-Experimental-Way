# Code：在线绘出抛物线等规则曲线的轮廓

## 打开实验文件

### 在线调试环境1

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单机右方的[Python Online Compiler](https://www.alphacodingskills.com/compile-python-online.php)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面“Run Code”下侧的深蓝色的空白栏中， 然后单击上方的按键“Run Code”。

### y = x**2
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

x = np.linspace(-4,4,9)
print(x)
y = x**2
print(y)

plt.scatter(x,y)
plt.show()
```

### y = 1/x
```python
import numpy as np
import matplotlib.pyplot as plt
plt.gca().set_aspect( 1 ) 

x = np.linspace(-10,-0.1,200)
print(x)
y = 1/x
print(y)

plt.scatter(x,y)
plt.show()

x = np.linspace(0.1,10,200)
print(x)
y = 1/x
print(y)

plt.scatter(x,y)
plt.show()
```

## 参考文献及资料

1. [matplotlib：tutorials](https://matplotlib.org/tutorials/index.html)

