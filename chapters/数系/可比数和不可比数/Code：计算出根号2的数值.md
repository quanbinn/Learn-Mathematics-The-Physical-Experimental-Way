# Code：计算出根号2的数值

## 打开实验文件

### 在线调试环境1 

- 单击右方的[Python Tutor](https://pythontutor.com/visualize.html#mode=edit)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击空白栏下方的按键“Visualize Execution”。

### 在线调试环境2

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

```python
import math

print(round(math.sqrt(21), 8))
print(round(math.sqrt(22), 8))
print(round(math.sqrt(23), 8))
print(round(math.sqrt(24), 8))
print(round(math.sqrt(25), 8))
print(round(math.sqrt(26), 8))
print(round(math.sqrt(27), 8))
print(round(math.sqrt(28), 8))
print(round(math.sqrt(29), 8))
print(round(math.sqrt(30), 8))
```

```python
import math

for i in range(1,100):
    print(round(math.pow(i, 1 / 2), 8))
	## print(round(math.pow(i, 1 / 3), 8))
	## print(round(math.pow(i, 1 / 4), 8))
	## print(round(math.pow(i, 1 / 5), 8))
```python

```python
import math

for i in range(0,101):
    print(round(math.pow(10, i / 100), 8))
```python

## 参考文献及资料

1. 维基百科
	- [Division (mathematics)](https://en.wikipedia.org/wiki/Division_(mathematics)) | [除法](https://zh.wikipedia.org/wiki/除法) 
	- [Remainder](https://en.wikipedia.org/wiki/Remainder) | [余数](https://zh.wikipedia.org/wiki/%E4%BD%99%E6%95%B0) 
	- [Modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic) | [模算数](https://zh.wikipedia.org/wiki/%E6%A8%A1%E7%AE%97%E6%95%B8) 
	- [Modulo operation](https://en.wikipedia.org/wiki/Modulo_operation) |  [模除](https://zh.wikipedia.org/wiki/%E6%A8%A1%E9%99%A4) 

2. [模运算](https://baike.baidu.com/item/%E6%A8%A1%E8%BF%90%E7%AE%97/4376110) 


