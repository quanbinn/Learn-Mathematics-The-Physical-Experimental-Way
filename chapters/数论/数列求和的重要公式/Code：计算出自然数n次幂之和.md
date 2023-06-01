# Code：计算出自然数n次幂之和

## 打开实验文件

### 在线调试环境1 

- 单击右方的[Python Tutor](https://pythontutor.com/visualize.html#mode=edit)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击空白栏下方的按键“Visualize Execution”。

### 在线调试环境2

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 自然数1次幂的和

```python
n = 50
sum = 0

for i in range(1,n+1):
    sum += i**1
    print(sum)

def sum_by_formula_1(n):
    sum_by_formula = (n*(n+1))/2
    return sum_by_formula

print(sum_by_formula_1(n))
```

### 自然数2次幂的和

```python
n = 50
sum = 0
    
for i in range(1,n+1):
    sum += i**2
    print(sum)    

def sum_by_formula_2(n):
    sum_by_formula = (n*(n+1)*(2*n+1))/6
    return sum_by_formula

print(sum_by_formula_2(n))  
```

### 自然数3次幂的和

```python
n = 50
sum = 0
    
for i in range(1,n+1):
    sum += i**3
    print(sum)    

def sum_by_formula_3(n):
    sum_by_formula = ((n**2)*(n**2+2*n+1))/4
    return sum_by_formula

print(sum_by_formula_3(n))    
```



