# Code：计算矩阵转置

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
# Takes in a matrix and outputs the transpose of the matrix
def transpose(matrix):
    matrix_transpose = []
    # Loop through columns on outside loop
    for c in range(len(matrix[0])):
        new_row = []
        # Loop through columns on inner loop
        for r in range(len(matrix)):
            # Column values will be filled by what were each row before
            new_row.append(matrix[r][c])
        matrix_transpose.append(new_row)
    
    return matrix_transpose

# Copy of the previously made dot_product() function
def dot_product(vectorA, vectorB):
    result = 0
    
    for i in range(len(vectorA)):
        result += vectorA[i] * vectorB[i]
        
    return result

# Takes in two matrices and outputs the product of the two matrices
def matrix_multiplication(matrixA, matrixB):
    product = []

    # Take the transpose of matrixB and store the result
    transposeB = transpose(matrixB)
    
    # Use a nested for loop to iterate through the rows
    # of matrix A and the rows of the tranpose of matrix B
    for r1 in range(len(matrixA)):
        new_row = []
        for r2 in range(len(transposeB)):
            # Calculate the dot product between each row of matrix A
            # with each row in the transpose of matrix B
            dp = dot_product(matrixA[r1], transposeB[r2])
            new_row.append(dp)
        # Store the results in the product variable
        product.append(new_row)

    return product

# Run the code in the cell below to test the implementation.

assert matrix_multiplication([[5, 3, 1], 
                              [6, 2, 7]], 
                             [[4, 2], 
                              [8, 1], 
                              [7, 4]]) == [[51, 17], 
                                           [89, 42]]

assert matrix_multiplication([[5]], [[4]]) == [[20]]

assert matrix_multiplication([[2, 8, 1, 2, 9],
                             [7, 9, 1, 10, 5],
                             [8, 4, 11, 98, 2],
                             [5, 5, 4, 4, 1]], 
                             [[4], 
                              [2], 
                              [17], 
                              [80], 
                              [2]]) == [[219], [873], [8071], [420]]


assert matrix_multiplication([[2, 8, 1, 2, 9],
                             [7, 9, 1, 10, 5],
                             [8, 4, 11, 98, 2],
                             [5, 5, 4, 4, 1]], 
                             [[4, 1, 2], 
                              [2, 3, 1], 
                              [17, 8, 1], 
                              [1, 3, 0], 
                              [2, 1, 4]]) == [[61, 49, 49], [83, 77, 44], [329, 404, 39], [104, 65, 23]]
```

## 参考文献及资料

1. [Coding the Transpose (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/9e37fd67-d8ca-458b-8a34-926cf8342af0)
