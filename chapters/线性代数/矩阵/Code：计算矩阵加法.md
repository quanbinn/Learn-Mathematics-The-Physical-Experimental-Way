# Code：在线计算矩阵加法

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
vector = [11, 11, 0] ### Assign the vector <11, 11, 0> to the variable v
print(vector)

### Assign the vector  <11, 11, 0> to the variable matrixVector1 (matrix: a list of lists) 
matrixVector1 = [
    [11, 11, 0]
]
print(matrixVector1)

### Assign the vector <11, 11, 0> to the variable matrixVector2 (matrix: a list of lists)
matrixVector2 = [
    [11],
    [11],
    [0]
]
print(matrixVector2)

### Assign the following matrix to the variable matrix
### 0 0 0 
### 9 0 0
### 0 9 3

matrix = [
    [0, 0, 0],
    [9, 0, 0],
    [0, 9, 3]
]
print(matrix)

matrix[1][2] = 5 ### In matrix, change the value in the second row last column from 0 to 5
print(matrix)

def matrix_print(matrix):
    for i in range(len(matrix)):
        for j in range(len(matrix[0])):
            m_ij = matrix[i][j]
            print(m_ij, '\t', end="")
        print('\n') # prints a new line
    return

matrix = [
    [0, 0, 0],
    [9, 0, 0],
    [0, 9, 3]
]

matrix_print(matrix)
```

```python
def matrix_addition(matrixA, matrixB):

    matrixSum = []    # initialize matrix to hold the results
    row = []     # matrix to hold a row for appending sums of each element
    
    # For loop within a for loop to iterate over the matrices
    for r in range(len(matrixA)):
        row = [] # reset the list
        for c in range(len(matrixA[0])):
            row.append(matrixA[r][c] + matrixB[r][c]) # add the matrices
        matrixSum.append(row)
    
    return matrixSum

print(matrix_addition([[10]],
                      [[2]]))
                                                   
print(matrix_addition([[10,1]],
                      [[2,7]]))
                      
print(matrix_addition([[10,1,0]],
                      [[2,7,0]]))
                      
print(matrix_addition([[0,0,0]],
                      [[11,0,0]]))
                      
print(matrix_addition([[0,0,0],
                       [7.5,0,0]],
                      [[9,9,6],
                       [9,9,6]]))
                       
print(matrix_addition([[5,0,0],
                       [0,7.5,0],
                       [8.5,6.9,4.5]],
                     [[5,5,0],
                       [5,5,0],
                       [5,5,0]]))
                       
print(matrix_addition([[0,0,0],
                       [12,0,0],
                       [12,12,0],
                       [0,12,0],
                       [0,0,12],
                       [12,0,12],
                       [12,12,12],
                       [0,12,12]],
                      [[9,5,6],
                       [9,5,6],
                       [9,5,6],
                       [9,5,6],
                       [9,5,6],
                       [9,5,6],
                       [9,5,6],
                       [9,5,6]]))
```

## 参考文献及资料

1. [Coding Matrices (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/b135d1f5-04e4-4e63-bed8-cf3b0a2849e9)
2. [Coding Matrix Addition (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/873b4c43-91ff-40ba-885c-96e6bed65afd)
