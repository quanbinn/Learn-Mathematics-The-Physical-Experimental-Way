# Code：判断一个整数是否是素数

## 打开实验文件

### 在线调试环境

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

#### 判断一个整数是否是素数

```python
print(15%2)
print(15%3)
print(15%4) 
print(15%5)
print(15%6)
print(15%7)
print(15%8)
print(15%9)
print(15%10)
print(15%11)
print(15%12)
print(15%13)
print(15%14)
```

```python
def is_prime(n):
  for i in range(2,n):
    if (n%i) == 0:
      return False
  return True

is_prime(15)
```

#### 使用埃拉托斯特尼筛法打印出小于某个正整数的所有素数

```python
def SieveOfEratosthenes(num):
    prime = [True for i in range(num+1)]     # print(prime)

    p = 2
    while (p * p <= num):     
        if (prime[p] == True):               # If prime[p] is not changed, then it is a prime            
            for i in range(p * p, num+1, p): # Updating all multiples of p
                prime[i] = False
        p += 1
  
    for p in range(2, num+1):                # Print all prime numbers
        if prime[p]:
            print(p)
  
num = 50
SieveOfEratosthenes(num)
```

## 参考文献及资料

1. 维基百科
	- [Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) | [埃拉托斯特尼筛法](https://zh.wikipedia.org/wiki/埃拉托斯特尼筛法)

2. [Python Program for Sieve of Eratosthenes](https://www.geeksforgeeks.org/python-program-for-sieve-of-eratosthenes/)

