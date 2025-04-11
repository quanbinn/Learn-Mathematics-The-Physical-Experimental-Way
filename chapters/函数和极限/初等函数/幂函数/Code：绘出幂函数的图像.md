# Code：绘出幂函数的图像

## 打开实验文件

### 在线调试环境1

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(-2.5, 2.5, num=51)
print(x)

y = np.power(x,2) 
print(y)

plt.scatter(x, y)
plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(-2.5, 2.5, num=51)
print(x)

y = np.power(x+1,2)
print(y)

plt.scatter(x, y)
plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(-2.5, 2.5, num=51)
print(x)

y = np.power(x,2)+1
print(y)

plt.scatter(x, y)
plt.show()
```