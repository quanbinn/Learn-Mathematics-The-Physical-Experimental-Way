# Code：在线调试向量的基本运算

## 打开实验文件

单击右方的[在线代码段](https://pythontutor.com/live.html#code=class%20Vector%3A%0A%20%20%20%20def%20__init__%28self,%20coordinates%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20not%20coordinates%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%0A%20%20%20%20%20%20%20%20%20%20%20%20self.coordinates%20%3D%20tuple%28coordinates%29%0A%20%20%20%20%20%20%20%20%20%20%20%20self.dimension%20%3D%20len%28coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%28'The%20coordinates%20must%20be%20nonempty'%29%0A%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%20'Vector%3A%20%7B%7D'.format%28self.coordinates%29%0A%0Adef%20__eq__%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20self.coordinates%20%3D%3D%20v.coordinates%0A%0Apoint1%20%3D%20Vector%28%5B1,2,3%5D%29%0Aprint%28point1%29%0Apoint2%20%3D%20Vector%28%5B1,2,3%5D%29%0Apoint3%20%3D%20Vector%28%5B-1,2,3%5D%29%0A%0Aprint%28point1%20%3D%3D%20point2%29%0Aprint%28point1%20%3D%3D%20point3%29&cumulative=false&curInstr=29&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false), 浏览器里会打开一个页面，如下图所示。

```python
class Vector:
	def __init__(self, coordinates):
		try:
			if not coordinates:
				raise ValueError
			self.coordinates = tuple(coordinates)
			self.dimension = len(coordinates)

		except ValueError:
			raise ValueError('The coordinates must be nonempty')

	def __str__(self):
		return 'Vector: {}'.format(self.coordinates)

def __eq__(self, v):
		return self.coordinates == v.coordinates

point1 = Vector([1,2,3])
print(point1)
point2 = Vector([1,2,3])
point3 = Vector([-1,2,3])

print(point1 == point2)
print(point1 == point3)
```

单击右方的[在线代码段](https://pythontutor.com/live.html#code=class%20Vector%3A%0A%20%20%20%20def%20__init__%28self,%20coordinates%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20not%20coordinates%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%0A%20%20%20%20%20%20%20%20%20%20%20%20self.coordinates%20%3D%20tuple%28coordinates%29%0A%20%20%20%20%20%20%20%20%20%20%20%20self.dimension%20%3D%20len%28coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%28'The%20coordinates%20must%20be%20nonempty'%29%0A%0A%20%20%20%20def%20plus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20nepoint2_coordinates%20%3D%20%5Bx%2By%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28nepoint2_coordinates%29%0A%20%20%20%20def%20minus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20nepoint2_coordinates%20%3D%20%5Bx-y%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28nepoint2_coordinates%29%20%20%20%0A%20%20%20%20def%20times_scalar%28self,%20c%29%3A%0A%20%20%20%20%20%20%20%20nepoint2_coordinates%20%3D%20%5Bc*x%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28nepoint2_coordinates%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%20'Vector%3A%20%7B%7D'.format%28self.coordinates%29%0A%0A%20%20%20%20def%20__eq__%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20self.coordinates%20%3D%3D%20v.coordinates%0A%0Apoint1%20%3D%20Vector%28%5B8.218,-9.341%5D%29%0Apoint2%20%3D%20Vector%28%5B-1.129,2.111%5D%29%0Aprint%28point1.plus%28point2%29%29%0A%0Apoint3%20%3D%20Vector%28%5B7.119,8.215%5D%29%0Apoint4%20%3D%20Vector%28%5B-8.223,0.878%5D%29%0Aprint%28point3.minus%28point4%29%29%0A%0Apoint5%20%3D%20Vector%28%5B1.671,-1.012,-0.318%5D%29%0Ac%20%3D%207.41%0Aprint%28point5.times_scalar%28c%29%29&cumulative=false&curInstr=95&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false), 浏览器里会打开一个页面，如下图所示。

```python
class Vector:
	def __init__(self, coordinates):
		try:
			if not coordinates:
				raise ValueError
			self.coordinates = tuple(coordinates)
			self.dimension = len(coordinates)

		except ValueError:
			raise ValueError('The coordinates must be nonempty')

	def plus(self, v):
		nepoint2_coordinates = [x+y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(nepoint2_coordinates)
	def minus(self, v):
		nepoint2_coordinates = [x-y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(nepoint2_coordinates)   
	def times_scalar(self, c):
		nepoint2_coordinates = [c*x for x in self.coordinates]
		return Vector(nepoint2_coordinates)				 

	def __str__(self):
		return 'Vector: {}'.format(self.coordinates)

	def __eq__(self, v):
		return self.coordinates == v.coordinates

point1 = Vector([8.218,-9.341])
point2 = Vector([-1.129,2.111])
print(point1.plus(point2))

point3 = Vector([7.119,8.215])
point4 = Vector([-8.223,0.878])
print(point3.minus(point4))

point5 = Vector([1.671,-1.012,-0.318])
c = 7.41
print(point5.times_scalar(c))
```

单击右方的[在线代码段](https://pythontutor.com/live.html#code=from%20math%20import%20sqrt%0A%0Aclass%20Vector%3A%0A%20%20%20%20def%20__init__%28self,%20coordinates%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20not%20coordinates%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%0A%20%20%20%20%20%20%20%20%20%20%20%20self.coordinates%20%3D%20tuple%28coordinates%29%0A%20%20%20%20%20%20%20%20%20%20%20%20self.dimension%20%3D%20len%28coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%28'The%20coordinates%20must%20be%20nonempty'%29%0A%0A%20%20%20%20def%20magnitude%28self%29%3A%0A%20%20%20%20%20%20%20%20coordinates_squared%20%3D%20%5Bx**2%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20sqrt%28sum%28coordinates_squared%29%29%0A%0A%20%20%20%20def%20normalized%28self%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20magnitude%20%3D%20self.magnitude%28%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.times_scalar%281/magnitude%29%0A%0A%20%20%20%20%20%20%20%20except%20ZeroDivsionError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28'Cannot%20normalize%20the%20zero%20vector'%29%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20plus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx%2By%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%0A%20%20%20%20def%20minus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx-y%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%0A%20%20%20%20def%20times_scalar%28self,%20c%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bc*x%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%20'Vector%3A%20%7B%7D'.format%28self.coordinates%29%0A%0A%20%20%20%20def%20__eq__%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20self.coordinates%20%3D%3D%20v.coordinates%0A%0Apoint1%20%3D%20Vector%28%5B-0.221,%207.437%5D%29%0Aprint%28point1.magnitude%28%29%29%0A%0Apoint2%20%3D%20Vector%28%5B8.813,%20-1.331,%20-6.247%5D%29%0Aprint%28point2.magnitude%28%29%29%0A%0Apoint3%20%3D%20Vector%28%5B5.581,%20-2.136%5D%29%0Aprint%28point3.normalized%28%29%29%0A%0Apoint4%20%3D%20Vector%28%5B1.996,%203.108,%20-4.554%5D%29%0Aprint%28point4.normalized%28%29%29&cumulative=false&curInstr=119&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false), 浏览器里会打开一个页面，如下图所示。

```python
from math import sqrt

class Vector:
	def __init__(self, coordinates):
		try:
			if not coordinates:
				raise ValueError
			self.coordinates = tuple(coordinates)
			self.dimension = len(coordinates)

		except ValueError:
			raise ValueError('The coordinates must be nonempty')

	def magnitude(self):
		coordinates_squared = [x**2 for x in self.coordinates]
		return sqrt(sum(coordinates_squared))

	def normalized(self):
		try:
			magnitude = self.magnitude()
			return self.times_scalar(1/magnitude)

		except ZeroDivsionError:
			raise Exception('Cannot normalize the zero vector')			

	def plus(self, v):
		new_coordinates = [x+y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(new_coordinates)
	def minus(self, v):
		new_coordinates = [x-y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(new_coordinates)   
	def times_scalar(self, c):
		new_coordinates = [c*x for x in self.coordinates]
		return Vector(new_coordinates)				 

	def __str__(self):
		return 'Vector: {}'.format(self.coordinates)

	def __eq__(self, v):
		return self.coordinates == v.coordinates

point1 = Vector([-0.221, 7.437])
print(point1.magnitude())

point2 = Vector([8.813, -1.331, -6.247])
print(point2.magnitude())

point3 = Vector([5.581, -2.136])
print(point3.normalized())

point4 = Vector([1.996, 3.108, -4.554])
print(point4.normalized())
```

## 参考文献及资料

1. [Linear Algebra Refresher Course from **Udacity.com**](https://classroom.udacity.com/courses/ud953/lessons/4374471116/concepts/45834932630923)