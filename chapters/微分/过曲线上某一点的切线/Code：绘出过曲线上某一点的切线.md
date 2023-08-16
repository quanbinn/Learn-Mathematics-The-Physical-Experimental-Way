# Code：绘出过曲线上某一点的切线

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

def f(x):
	return 2*x**2

x = np.arange(0, 5, 0.001) # np.arange(start, stop, step) to give us smoother line
y = f(x)

plt.plot(x, y)
plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np

def f(x):
	return 2*x**2

x = np.arange(0, 5, 0.001) # np.arange(start, stop, step) to give us smoother line
y = f(x)

plt.plot(x, y)


p2_delta = 0.0001	# The point and the "close enough" point
x1 = 2
x2 = x1+p2_delta

y1 = f(x1)
y2 = f(x2)

print((x1, y1), (x2, y2))

approximate_derivative = (y2-y1)/(x2-x1)	# Derivative approximation and y-intercept for the tangent line
b = y2 - approximate_derivative*x2

# We put the tangent line calculation into a function so we can call
# it multiple times for different values of x
# approximate_derivative and b are constant for given function
# thus calculated once above this function
def tangent_line(x):
    return approximate_derivative*x + b

# plotting the tangent line
# +/- 0.9 to draw the tangent line on our graph
# then we calculate the y for given x using the tangent line function
# Matplotlib will draw a line for us through these points
to_plot = [x1-0.9, x1, x1+0.9]
plt.plot(to_plot, [tangent_line(i) for i in to_plot])

print('Approximate derivative for f(x)',
	f'where x = {x1} is {approximate_derivative}')

plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np

def f(x):
	return 2*x**2

x = np.arange(0, 5, 0.001) # np.arange(start, stop, step) to give us smoother line
y = f(x)

plt.plot(x, y)

colors = ['k','g','r','b','c']

def approximate_tangent_line(x, approximate_derivative):
	return (approximate_derivative*x) + b

for i in range(5):
	p2_delta = 0.0001
	x1 = i
	x2 = x1+p2_delta

	y1 = f(x1)
	y2 = f(x2)

	print((x1, y1), (x2, y2))
	approximate_derivative = (y2-y1)/(x2-x1)
	b = y2-(approximate_derivative*x2)

	to_plot = [x1-0.9, x1, x1+0.9]

	plt.scatter(x1, y1, c=colors[i])
	plt.plot([point for point in to_plot],
		[approximate_tangent_line(point, approximate_derivative)
			for point in to_plot],
		c=colors[i])
	print('Approximate derivative for f(x)',
		f'where x = {x1} is {approximate_derivative}')

plt.show()
```