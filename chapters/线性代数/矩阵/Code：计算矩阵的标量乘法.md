# Code：在线计算矩阵的标量乘法

## 开始做代码实验

### 在线调试环境1

- 单击右方的[pythontutor](https://pythontutor.com/visualize.html#mode=edit)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这段python代码拷贝到这个页面中间的空白栏中， 然后单击左下方的按键“Visualize Execution”。

### 在线调试环境2

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境3

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

```python
def scalarMultiplication(multiplier,matrix):
    result = []
    for i in range(len(matrix)):
        row = matrix[i]
        new_row = [] # empty row for now
        for j in range(len(row)):
            matrix_ij = matrix[i][j]
            result_ij = multiplier * matrix_ij
            new_row.append(result_ij)
        result.append(new_row)
    print(result)
    
scalarMultiplication(7.41, [[1.671,-1.012,-0.318]])
scalarMultiplication(1.4, [[0,2,3],[7,-3,0]])
scalarMultiplication(2, [[0,0,0],[-5,7.5,0],[3.5,6.9,4.5]])
```

## 参考文献及资料

1. [immersive linear algebra(Chapter 6: The Matrix)](http://immersivemath.com/ila/ch06_matrices/ch06.html)

2. [Scalar Multiplication of Vector | Linear Algebra using Python](https://www.includehelp.com/python/scalar-multiplication-of-vector.aspx)
