# Code：在线绘出不规则曲线的轮廓

## 打开实验文件

### 在线调试环境1

- 单机右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境2

- 单机右方的[Python Online Compiler](https://www.alphacodingskills.com/compile-python-online.php)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面“Run Code”下侧的深蓝色的空白栏中， 然后单击上方的按键“Run Code”。

### B样条曲线
```python
import matplotlib.pyplot as plt
import numpy as np
from mpmath import diff

# 计算基函数，i为控制顶点序号，k为次数，u为代入的值，NodeVector为节点向量
# 该函数返回第i+1个k次基函数在u处的值

def b_spline_basis(i, k, u, nodeVector):
    # nodeVector = np.mat(nodeVector)  # 将输入的节点转化成能够计算的数组
    # k=0时，定义一次基函数
    if k == 0:
        if (nodeVector[i] < u) & (u <= nodeVector[i + 1]):  # 若u在两个节点之间，函数之为1，否则为0
            result = 1
        else:
            result = 0
    else:
        # 计算支撑区间长度
        length1 = nodeVector[i + k] - nodeVector[i]
        length2 = nodeVector[i + k + 1] - nodeVector[i + 1]
        # 定义基函数中的两个系数
        if length1 == 0:  # 特别定义 0/0 = 0
            alpha = 0
        else:
            alpha = (u - nodeVector[i]) / length1
        if length2 == 0:
            beta = 0
        else:
            beta = (nodeVector[i + k + 1] - u) / length2
    # 递归定义
        result = alpha * b_spline_basis(i, k - 1, u, nodeVector) + beta * b_spline_basis(i + 1, k - 1, u, nodeVector)
    return result

# 画B样条函数图像
def draw_b_spline(n,k,nodeVector,X,Y):
    plt.figure()
    basis_i = np.zeros(100)  # 存放第i个基函数
    rx = np.zeros(100)  # 存放B样条的横坐标
    ry = np.zeros(100)
    for i in range(n + 1):  # 计算第i个B样条基函数，
        U = np.linspace(nodeVector[k], nodeVector[n+1], 100)  # 在节点向量收尾之间取100个点，u在这些点中取值
        j = 0
        for u in U:
            nodeVector = np.array(nodeVector)
            basis_i[j] = b_spline_basis(i, k, u, nodeVector)  # 计算取u时的基函数的值
            j = j + 1
        rx = rx + X[i] * basis_i
        ry = ry + Y[i] * basis_i
        # plt.plot(U,basis_i)
        print(basis_i)
    print(rx)
    print(ry)
    plt.plot(X,Y)
    plt.plot(rx, ry)
    plt.show()

if __name__ == '__main__':
    n = 7
    k = 3
    nodeVector = [0, 0, 0, 0, 1, 2, 3, 4, 5, 5, 5, 5]
    X = [0, 1, 2, 3, 4, 5, 6, 7]
    Y = [0, 3, 1, 3, 1, 4, 0, 5]
    draw_b_spline(n,k,nodeVector,X,Y)
```

## 参考文献及资料

1. [Python绘制B样条曲线（De Boor Cox）](https://blog.csdn.net/weixin_40583586/article/details/110736484/) 



