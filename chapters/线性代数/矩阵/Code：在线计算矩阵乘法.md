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
import math

radian = math.pi/6

matrix2dRotation1 = [[math.cos(radian),-math.sin(radian)],
          [math.sin(radian),math.cos(radian)]
         ]   
         
print(matrix2dRotation1)

matrix2dRotation2 = [[round(math.cos(radian),2),round(-math.sin(radian),2)],
          [round(math.sin(radian),2),round(math.cos(radian),2)]
         ]   
         
print(matrix2dRotation2)

matrix3dRotation1 = [[math.cos(radian),-math.sin(radian),0],
          [math.sin(radian),math.cos(radian),0],
          [0,0,1]
         ]   

print(matrix3dRotation1)

matrix3dRotation2 = [[round(math.cos(radian),2),round(-math.sin(radian),2),round(0,2)],
          [round(math.sin(radian),2),round(math.cos(radian),2),round(0,2)],
          [round(0,2),round(0,2),round(1,2)]
         ]   
         
print(matrix3dRotation2)
```

```python
import math

radian = math.pi/6

matrix3dRotation2 = [[round(math.cos(radian),2),round(-math.sin(radian),2),round(0,2)],
          [round(math.sin(radian),2),round(math.cos(radian),2),round(0,2)],
          [round(0,2),round(0,2),round(1,2)]
         ]   
         
print(matrix3dRotation2)

# Receives a matrix and a column number. 
# The output is the column in the form of a list
def get_column(matrix, column_number):
    column = []
    for r in range(len(matrix)):
        column.append(matrix[r][column_number])

    return column

# Run this code to test your get_column function
print(get_column((matrix3dRotation2),0))
print(get_column((matrix3dRotation2),1))
print(get_column((matrix3dRotation2),2))
```

```python
def dot_product(vector_one, vector_two):
    result = 0
    
    for i in range(len(vector_two)):
        result += vector_one[i] * vector_two[i]

    return result

print(dot_product([4, 5, 1], [2, 1, 5]))
```

```python
import math

radian = math.pi*3/4

matrix2dRotation = [[round(math.cos(radian),2),round(-math.sin(radian),2)],
          [round(math.sin(radian),2),round(math.cos(radian),2)]
         ]   

matrix3dRotation = [[round(math.cos(radian),2),round(-math.sin(radian),2),round(0,2)],
          [round(math.sin(radian),2),round(math.cos(radian),2),round(0,2)],
          [round(0,2),round(0,2),round(1,2)]
         ]   

def get_row(matrix, row): return matrix[row]

def get_column(matrix, column_number):
    column = []
    for r in range(len(matrix)):
        column.append(matrix[r][column_number])

    return column

def dot_product(vector_one, vector_two):
    result = 0
    
    for i in range(len(vector_two)):
        result += vector_one[i] * vector_two[i]

    return result
    
# Takes two matrices,multiplies them together and then returns the results.
def matrix_multiplication(matrixA, matrixB):
    
    # Store the number of rows in A and the number of columns in B.
    # This will be the size of the output matrix
    m_rows = len(matrixA)
    p_columns = len(matrixB[0])
    
    result = []   # empty list that will hold the product of AxB

    
    # For loop within a for loop. The outside for loop will 
    # iterate through m_rows. The inside for loop will iterate 
    # through p_columns.
    for r in range(m_rows):
        row_result = []     # Accumulate the values of a row (reset each loop)
        rowA = get_row(matrixA, r)        # Grab current A row
        
        for c in range(p_columns):
            colB = get_column(matrixB, c)      # Grab current B column
            dot_prod = dot_product(rowA, colB)     # Calculate the dot product of the A row and the B column
            row_result.append(dot_prod)            # And append to row_result
    
        result.append(row_result)        # Add the row_result to the result matrix

    return result

# print(matrix_multiplication([[10.83,1.91]],matrix2dRotation)) #radian = -math.pi/6

# print(matrix_multiplication([[3.0,0.5,0],
#                     [8.3,7.3,0]
#                                     ], matrix3dRotation))   #radian = -math.pi/3

#print(matrix_multiplication([[1.0,5.9,0],    
#                     [9.8,1.7,0],
#                     [7.8,9.3,6]
#                        ], matrix3dRotation))   #radian = -math.pi/2

print(matrix_multiplication([[1.7,1.7,0],
                     [10.7,1.7,0],
                     [10.7,10.7,0],
                     [1.7,10.7,0],
                     [1.7,1.7,9],
                     [10.7,1.7,9],
                     [10.7,10.7,9],
                     [1.7,10.7,9]
                          ], matrix3dRotation)) # radian = math.pi*3/4(135 degrees)
```

## 参考文献及资料

1. [Coding Matrix Multiplication (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/f33a989b-a8cb-4473-94f9-3c42d06749b3)