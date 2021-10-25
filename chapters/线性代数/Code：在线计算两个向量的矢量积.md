# Code：在线计算两个向量的矢量积

## 打开实验文件

单击右方的[在线代码段](https://pythontutor.com/live.html#code=from%20math%20import%20sqrt,%20acos,%20pi%0A%0Aclass%20Vector%3A%0A%20%20%20%20CANNOT_NORMALIZE_ZERO_VECTOR_MSG%20%3D%20'Cannot%20normalize%20the%20zero%20vector'%0A%0A%20%20%20%20def%20__init__%28self,%20coordinates%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20not%20coordinates%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%0A%20%20%20%20%20%20%20%20%20%20%20%20self.coordinates%20%3D%20tuple%28%5Bx%20for%20x%20in%20coordinates%5D%29%0A%20%20%20%20%20%20%20%20%20%20%20%20self.dimension%20%3D%20len%28self.coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%28'The%20coordinates%20must%20be%20nonempty'%29%0A%0A%20%20%20%20def%20magnitude%28self%29%3A%0A%20%20%20%20%20%20%20%20coordinates_squared%20%3D%20%5Bx**2%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20sqrt%28sum%28coordinates_squared%29%29%0A%0A%20%20%20%20def%20normalized%28self%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20magnitude%20%3D%20self.magnitude%28%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.times_scalar%281/magnitude%29%0A%20%20%20%20%20%20%20%20except%20ZeroDivsionError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG%29%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20def%20plus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx%2By%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%0A%20%20%20%20def%20minus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx-y%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%0A%20%20%20%20def%20times_scalar%28self,%20c%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bc*x%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20area_of_triangle_with%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20self.area_of_parallelogram_with%28v%29%20/%202.0%0A%0A%20%20%20%20def%20area_of_parallelogram_with%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20cross_product%20%3D%20self.cross%28v%29%0A%20%20%20%20%20%20%20%20return%20cross_product.magnitude%28%29%0A%0A%20%20%20%20def%20cross%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20x_1,%20y_1,%20z_1%20%3D%20self.coordinates%0A%20%20%20%20%20%20%20%20%20%20%20%20x_2,%20y_2,%20z_2%20%3D%20v.coordinates%0A%20%20%20%20%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5B%20y_1*z_2%20-%20y_2*z_1,%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20-%28x_1*z_2%20-%20x_2*z_1%29,%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20x_1*y_2%20-%20x_2*y_1%20%20%20%20%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%20as%20e%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20msg%20%3D%20str%28e%29%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20msg%20%3D%3D%20'need%20more%20than%202%20values%20to%20unpack'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self_embedded_in_R3%20%3D%20Vector%28self.coordinates%20%2B%20%28'0',%29%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20v_embedded_in_R3%20%3D%20Vector%28v.coordinates%20%2B%20%28'0',%29%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20self_embedded_in_R3.cross%28v_embedded_in_R3%29%0A%20%20%20%20%20%20%20%20%20%20%20%20elif%20%28msg%20%3D%3D%20'too%20many%20values%20to%20unpack'%20or%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20msg%20%3D%3D%20'need%20more%20than%201%20value%20to%20unpack'%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28self.ONLY_DEFINED_IN_TWO_THREE_DIMS_MSG%29%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20e%0A%0A%20%20%20%20def%20component_orthogonal_to%28self,%20basis%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20projection%20%3D%20self.component_parallel_to%28basis%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.minus%28projection%29%0A%0A%20%20%20%20%20%20%20%20except%20Exception%20as%20e%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20str%28e%29%20%3D%3D%20self.NO_UNIQUE_PARALLEL_COMPONENT_MSG%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28self.NO_UNIQUE_PARALLEL_COMPONENT_MSG%29%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20e%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%20'Vector%3A%20%7B%7D'.format%28self.coordinates%29%0A%0Av%20%3D%20Vector%28%5B8.462,%207.893,%200%5D%29%0Aw%20%3D%20Vector%28%5B6.984,%20-5.975,%200%5D%29%0Aprint%28'%231%3A',%20v.cross%28w%29%29%0Aprint%28'%232%3A',%20v.area_of_parallelogram_with%28w%29%29%0Aprint%28'%233%3A',%20v.area_of_triangle_with%28w%29%29&cumulative=false&curInstr=128&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false), 浏览器里会打开一个页面，如下图所示。

```python
from math import sqrt, acos, pi

class Vector:
	CANNOT_NORMALIZE_ZERO_VECTOR_MSG = 'Cannot normalize the zero vector'

	def __init__(self, coordinates):
		try:
			if not coordinates:
				raise ValueError
			self.coordinates = tuple([x for x in coordinates])
			self.dimension = len(self.coordinates)

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
			raise Exception(self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG)		
				
	def plus(self, v):
		new_coordinates = [x+y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(new_coordinates)
	def minus(self, v):
		new_coordinates = [x-y for x,y in zip(self.coordinates, v.coordinates)]
		return Vector(new_coordinates)   
	def times_scalar(self, c):
		new_coordinates = [c*x for x in self.coordinates]
		return Vector(new_coordinates)				 

	def dot(self, v):
		return sum([x*y for x,y in zip(self.coordinates, v.coordinates)])

	def angle_with(self, v, in_degrees=False):
		try:
			u1 = self.normalized()
			u2 = v.normalized()
			angle_in_radians = acos(round(u1.dot(u2),10)) # angle_in_radians = acos(u1.dot(u2))

			if in_degrees:
				degrees_per_radian = 180 / pi
				return angle_in_radians * degrees_per_radian
			else: 
				return angle_in_radians

		except Exception as e:
			if str(e) == self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG:
				raise Exception('Cannot compute an angle with the zero vector')
			else:
				raise e

	def area_of_triangle_with(self, v):
		return self.area_of_parallelogram_with(v) / 2.0

	def area_of_parallelogram_with(self, v):
		cross_product = self.cross(v)
		return cross_product.magnitude()

	def cross(self, v):
		try:
			x_1, y_1, z_1 = self.coordinates
			x_2, y_2, z_2 = v.coordinates
			new_coordinates = [ y_1*z_2 - y_2*z_1,
							  -(x_1*z_2 - x_2*z_1),
							    x_1*y_2 - x_2*y_1	]
			return Vector(new_coordinates)

		except ValueError as e:
			msg = str(e)
			if msg == 'need more than 2 values to unpack':
				self_embedded_in_R3 = Vector(self.coordinates + ('0',))
				v_embedded_in_R3 = Vector(v.coordinates + ('0',))
				return self_embedded_in_R3.cross(v_embedded_in_R3)
			elif (msg == 'too many values to unpack' or
				  msg == 'need more than 1 value to unpack'):
				raise Exception(self.ONLY_DEFINED_IN_TWO_THREE_DIMS_MSG)
			else:
				raise e

	def component_orthogonal_to(self, basis):
		try:
			projection = self.component_parallel_to(basis)
			return self.minus(projection)

		except Exception as e:
			if str(e) == self.NO_UNIQUE_PARALLEL_COMPONENT_MSG:
				raise Exception(self.NO_UNIQUE_PARALLEL_COMPONENT_MSG)
			else:
				raise e

	def component_parallel_to(self, basis):
		try:
			u = basis.normalized()
			weight = self.dot(u)
			return u.times_scalar(weight)

		except Exception as e:
			if str(e) == self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG:
				raise Exception(self.NO_UNIQUE_PARALLEL_COMPONENT_MSG)
			else:
				raise e

	def is_orthogonal_to(self, v, tolerance=1e-10):
		return abs(self.dot(v)) < tolerance

	def is_parallel_to(self, v):
		return ( self.is_zero() or
				v.is_zero() or
				self.angle_with(v) == 0 or
				self.angle_with(v) == pi )

	def is_zero(self, tolerance=1e-10):
		return self.magnitude() < tolerance

	def __str__(self):
		return 'Vector: {}'.format(self.coordinates)

	def __eq__(self, v):
		return self.coordinates == v.coordinates

vector1 = Vector([8.462, 7.893, -8.187])
vector2 = Vector([6.984, -5.975, 4.778])
print('#1:', vector1.cross(vector2))

vector1 = Vector([-8.987, -9.838, 5.031])
vector2 = Vector([-4.268, -1.861, -8.866])
print('#2:', vector1.area_of_parallelogram_with(vector2))

vector1 = Vector([1.5, 9.547, 3.691])
vector2 = Vector([-6.007, 0.124, 5.772])
print('#3:', vector1.area_of_triangle_with(vector2))
```

## 参考文献及资料

1. [**14.Coding Cross Products** of Linear Algebra Refresher Course from **Udacity.com**](https://classroom.udacity.com/courses/ud953/lessons/4374471116/concepts/45834932680923)
2. [Parallelogram](https://en.wikipedia.org/wiki/Parallelogram)
3. [Parallelogram law](https://en.wikipedia.org/wiki/Parallelogram_law)