# Code：在线计算无限系列数的和

## 打开实验文件

### 在线调试环境

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

```python
# 计算出下列无限系列数的和：
# 1/(2**0) + 1/(2**1) + 1/(2**2) + 1/(2**3) + ... + 1/(2**(n-1)) + 1/(2**n)

n = 100
sum = 0

for i in range(0,n):
    sum += 1/(2**i)

print(sum)
```




