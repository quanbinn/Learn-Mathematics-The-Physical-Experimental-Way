# Code：在线计算两个向量的数量积和角度

## 打开实验文件

单击右方的[在线代码段](https://pythontutor.com/live.html#code=from%20math%20import%20sqrt,%20acos,%20pi%0A%0Aclass%20Vector%3A%0A%20%20%20%20CANNOT_NORMALIZE_ZERO_VECTOR_MSG%20%3D%20'Cannot%20normalize%20the%20zero%20vector'%0A%0A%20%20%20%20def%20__init__%28self,%20coordinates%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20not%20coordinates%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%0A%20%20%20%20%20%20%20%20%20%20%20%20self.coordinates%20%3D%20tuple%28%5Bx%20for%20x%20in%20coordinates%5D%29%0A%20%20%20%20%20%20%20%20%20%20%20%20self.dimension%20%3D%20len%28self.coordinates%29%0A%0A%20%20%20%20%20%20%20%20except%20ValueError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20ValueError%28'The%20coordinates%20must%20be%20nonempty'%29%0A%0A%20%20%20%20%20%20%20%20except%20TypeError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20TypeError%28'The%20coordinates%20must%20be%20an%20iterable'%29%0A%0A%20%20%20%20def%20magnitude%28self%29%3A%0A%20%20%20%20%20%20%20%20coordinates_squared%20%3D%20%5Bx**2%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20sqrt%28sum%28coordinates_squared%29%29%0A%0A%20%20%20%20def%20normalized%28self%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20magnitude%20%3D%20self.magnitude%28%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.times_scalar%281./magnitude%29%0A%20%20%20%20%20%20%20%20except%20ZeroDivsionError%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG%29%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20plus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx%2By%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%0A%20%20%20%20def%20minus%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bx-y%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%0A%20%20%20%20def%20times_scalar%28self,%20c%29%3A%0A%20%20%20%20%20%20%20%20new_coordinates%20%3D%20%5Bc*x%20for%20x%20in%20self.coordinates%5D%0A%20%20%20%20%20%20%20%20return%20Vector%28new_coordinates%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20def%20dot%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20sum%28%5Bx*y%20for%20x,y%20in%20zip%28self.coordinates,%20v.coordinates%29%5D%29%0A%0A%20%20%20%20def%20angle_with%28self,%20v,%20in_degrees%3DFalse%29%3A%0A%20%20%20%20%20%20%20%20try%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20u1%20%3D%20self.normalized%28%29%0A%20%20%20%20%20%20%20%20%20%20%20%20u2%20%3D%20v.normalized%28%29%0A%20%20%20%20%20%20%20%20%20%20%20%20angle_in_radians%20%3D%20acos%28u1.dot%28u2%29%29%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20in_degrees%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20degrees_per_radian%20%3D%20180.%20/%20pi%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20angle_in_radians%20*%20degrees_per_radian%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20angle_in_radians%0A%0A%20%20%20%20%20%20%20%20except%20Exception%20as%20e%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20str%28e%29%20%3D%3D%20self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20Exception%28'Cannot%20compute%20an%20angle%20with%20the%20zero%20vector'%29%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20raise%20e%0A%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%20'Vector%3A%20%7B%7D'.format%28self.coordinates%29%0A%0A%0A%20%20%20%20def%20__eq__%28self,%20v%29%3A%0A%20%20%20%20%20%20%20%20return%20self.coordinates%20%3D%3D%20v.coordinates%0A%0Av%20%3D%20Vector%28%5B7.887,%204.138%5D%29%0Aw%20%3D%20Vector%28%5B-8.802,%206.776%5D%29%0Aprint%28v.dot%28w%29%29%0A%0Av%20%3D%20Vector%28%5B-5.955,%20-4.904,%20-1.874%5D%29%0Aw%20%3D%20Vector%28%5B-4.496,%20-8.755,%207.103%5D%29%0Aprint%28v.dot%28w%29%29%0A%0Av%20%3D%20Vector%28%5B3.183,%20-7.627%5D%29%0Aw%20%3D%20Vector%28%5B-2.668,%205.319%5D%29%0Aprint%28v.angle_with%28w%29%29%0A%0Av%20%3D%20Vector%28%5B7.35,%200.221,%205.188%5D%29%0Aw%20%3D%20Vector%28%5B2.751,%208.259,%203.985%5D%29%0Aprint%28v.angle_with%28w,%20in_degrees%3DTrue%29%29&cumulative=false&curInstr=299&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false), 浏览器里会打开一个页面，如下图所示。

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

		except TypeError:
			raise TypeError('The coordinates must be an iterable')

	def magnitude(self):
		coordinates_squared = [x**2 for x in self.coordinates]
		return sqrt(sum(coordinates_squared))

	def normalized(self):
		try:
			magnitude = self.magnitude()
			return self.times_scalar(1./magnitude)
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
			angle_in_radians = acos(u1.dot(u2))

			if in_degrees:
				degrees_per_radian = 180. / pi
				return angle_in_radians * degrees_per_radian
			else: 
				return angle_in_radians

		except Exception as e:
			if str(e) == self.CANNOT_NORMALIZE_ZERO_VECTOR_MSG:
				raise Exception('Cannot compute an angle with the zero vector')
			else:
				raise e

	def __str__(self):
		return 'Vector: {}'.format(self.coordinates)


	def __eq__(self, v):
		return self.coordinates == v.coordinates

v = Vector([7.887, 4.138])
w = Vector([-8.802, 6.776])
print(v.dot(w))

v = Vector([-5.955, -4.904, -1.874])
w = Vector([-4.496, -8.755, 7.103])
print(v.dot(w))

v = Vector([3.183, -7.627])
w = Vector([-2.668, 5.319])
print(v.angle_with(w))

v = Vector([7.35, 0.221, 5.188])
w = Vector([2.751, 8.259, 3.985])
print(v.angle_with(w, in_degrees=True))
```

## 参考文献及资料

1. [**8.Coding Dot Product & Angle** of Linear Algebra Refresher Course from **Udacity.com**](https://classroom.udacity.com/courses/ud953/lessons/4374471116/concepts/45834932680923)