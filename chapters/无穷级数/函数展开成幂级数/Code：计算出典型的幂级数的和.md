# Code：计算出典型的幂级数的和

## 打开实验文件

### 在线调试环境

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

```python
import math

n = 11
sum = 0

for i in range(1,n):
    sum = 1 + (1/2)*i - (1/8)*i ** 2 + (1/16)*i**3 - (5/128)*i**4 + (7/256)*i**5 - (27/1024)*i**6
    print(i)
    print(math.sqrt(1+i))
    print(sum)
```

```python
import math

i = 0.999999
print(math.sqrt(1+i))

sum = 1 + (1/2)*i - (1/8)*i ** 2 + (1/16)*i**3 - (5/128)*i**4 + (7/256)*i**5 +  - (27/1024)*i**6
print(sum)
```