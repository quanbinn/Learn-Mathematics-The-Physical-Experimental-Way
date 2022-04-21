# Code：在线计算矩阵乘法

### 在线调试环境1

- 单击右方的[pythontutor](https://pythontutor.com/visualize.html#mode=edit)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这段python代码拷贝到这个页面中间的空白栏中， 然后单击左下方的按键“Visualize Execution”。

### 在线调试环境2

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境3

- 单击右方的[Python Online Compiler](https://www.alphacodingskills.com/compile-python-online.php)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面“Run Code”下侧的深蓝色的空白栏中， 然后单击上方的按键“Run Code”。

```python
def get_row(matrix, row):
    return matrix[row]

# Receives a matrix and a column number.
# The output should be the column in the form of a list
def get_column(matrix, column_number):
    column = []
    for r in range(len(matrix)):
        column.append(matrix[r][column_number])

    return column

# Run this code to test your get_column function
assert get_column([[1, 2, 4], 
                   [7, 8, 1], 
                   [5, 2, 1]], 1) == [2, 8, 2]

assert get_column([[5]], 0) == [5]

# Has two vectors as inputs and outputs the dot product of the 
# two vectors. First, it does element-wise
# multiplication and then sum the results. 

def dot_product(vector_one, vector_two):
    result = 0
    
    for i in range(len(vector_one)):
        result += vector_one[i] * vector_two[i]

    return result

# Run this cell to test your results

assert dot_product([4, 5, 1], [2, 1, 5]) == 18
assert dot_product([6], [7]) == 42

# Takes two matrices,multiplies them together and then returns
# the results.
def matrix_multiplication(matrixA, matrixB):
    
    # Store the number of rows in A and the number of columns in B.
    # This will be the size of the output matrix
    m_rows = len(matrixA)
    p_columns = len(matrixB[0])
    
    # empty list that will hold the product of AxB
    result = []

    
    # For loop within a for loop. The outside for loop will 
    # iterate through m_rows. The inside for loop will iterate 
    # through p_columns.
    for r in range(m_rows):
        # Accumulate the values of a row (reset each loop)
        row_result = []
        # Grab current A row
        rowA = get_row(matrixA, r)
        
        for c in range(p_columns):
            # Grab current B column
            colB = get_column(matrixB, c)
            # Calculate the dot product of the A row and the B column
            dot_prod = dot_product(rowA, colB)
            # And append to row_result
            row_result.append(dot_prod)
    
        # Add the row_result to the result matrix
        result.append(row_result)

    return result

# Run this code cell to test your results
assert matrix_multiplication([[5], [2]], [[5, 1]]) == [[25, 5], [10, 2]]
assert matrix_multiplication([[5, 1]], [[5], [2]]) == [[27]]
assert matrix_multiplication([[4]], [[3]]) == [[12]]
assert matrix_multiplication([[2, 1, 8, 2, 1], [5, 6, 4, 2, 1]], [[1, 7, 2], [2, 6, 3], [3, 1, 1], [1, 20, 1], [7, 4, 16]]) == [[37, 72, 33], [38, 119, 50]]
```

## 参考文献及资料

1. [Coding Matrix Multiplication (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/f33a989b-a8cb-4473-94f9-3c42d06749b3)