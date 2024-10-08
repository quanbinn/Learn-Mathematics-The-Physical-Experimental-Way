# Code：绘出sin(x)和cos(x)的图像

## 打开实验文件

### 在线调试环境1

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

### sin(x)
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2 * np.pi, num=50)
print(x)
y = np.sin(x)
print(y)
plt.scatter(x, y)

plt.show()
```

### cos(x)
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2 * np.pi, num=50)
print(x)
y = np.cos(x)
print(y)
plt.scatter(x, y)

plt.show()
```

### sin(x)和cos(x)
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2 * np.pi, num=50)
print(x)
y1 = np.sin(x)
print(y1)
plt.scatter(x, y1)

y2 = np.cos(x)
print(y2)
plt.scatter(x, y2)

plt.show()
```