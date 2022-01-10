# Code：在线计算两条线的交点

## 打开实验文件

- 单机右方的[onlinegdb](https://www.onlinegdb.com/online_python_compiler)，浏览器里会打开一个新的页面，把下面的这些代码段分别拷贝到main.py下面的空白栏中，然后单击空白栏最上面一栏的按键“Run”。

```python
from math import acos, sqrt, pi
from decimal import Decimal, getcontext

getcontext().prec = 30

class Vector(object):
	def __init__(self, coordinates):
		try:
			if not coordinates:
				raise ValueError
			self.coordinates = tuple([Decimal(c) for c in coordinates])
			self.dimension = len(coordinates)

		except ValueError:
			raise ValueError('The coordinates must be nonempty')

		except TypeError:
			raise TypeError('The coordinates must be an iterable')

	def __iter__(self):
		self.current = 0
		return self

	def __next__(self):
		if self.current >= len(self.coordinates):
			raise StopIteration
		else:
			current_value = self.coordinates[self.current]
			self.current += 1
			return current_value
		
	def next(self):
		return self.__next__()

	def __len__(self):
		return len(self.coordinates)

	def __getitem__(self, i):
		return self.coordinates[i]

	def __str__(self):
		return 'Vector: {}'.format([round(coord, 3)
									for coord in self.coordinates])

	def __eq__(self, v):
		return self.coordinates == v.coordinates

	def is_zero(self):
		return set(self.coordinates) == set([Decimal(0)])

	def plus(self, other):
		new_coordinates = [x + y for x, y in zip(self.coordinates, other.coordinates)]
		return Vector(new_coordinates)

	def minus(self, other):
		return Vector([coords[0] - coords[1]
					   for coords in zip(self.coordinates, other.coordinates)])

	def times_scalar(self, factor):
		return Vector([Decimal(factor) * coord for coord in self.coordinates])

	def magnitude(self):
		return Decimal(sqrt(sum([coord * coord
								 for coord in self.coordinates])))

	def normalize(self):
		try:
			return self.times_scalar(Decimal('1.0') / self.magnitude())
		except ZeroDivisionError:
			raise Exception('Cannot normalize the zero vector')

	def dot_product(self, other):
		return sum(x * y for x, y in zip(self.coordinates, other.coordinates))

	def get_angle_rad(self, other):
		dot_prod = round(self.normalize().dot_product(other.normalize()), 3)
		return acos(dot_prod)

	def get_angle_deg(self, other):
		degrees_per_rad = 180. / pi
		return degrees_per_rad * self.get_angle_rad(other)

	def is_parallel(self, other):
		return (self.is_zero() or other.is_zero() or
				self.get_angle_rad(other) in [0, pi])

	def is_orthogonal(self, other):
		return round(self.dot_product(other), 3) == 0

	def get_projected_vector(self, other):
		"""
		Gets projection of vector v in b
		"""
		b_normalized = other.normalize()
		return b_normalized.times_scalar(self.dot_product(b_normalized))

	def get_orthogonal_vector(self, other):
		return self.minus(self.get_projected_vector(other))

	def cross_product(self, other):
		[x1, y1, z1] = self.coordinates
		[x2, y2, z2] = other.coordinates
		x = (y1 * z2) - (y2 * z1)
		y = -((x1 * z2) - (x2 * z1))
		z = (x1 * y2) - (x2 * y1)
		return Vector([x, y, z])

	def area_parallelogram(self, other):
		return self.cross_product(other).magnitude()

	def area_triangle(self, other):
		return self.cross_product(other).magnitude() / 2

class MyDecimal(Decimal):
    def is_near_zero(self, eps=1e-10):
        return abs(self) < eps

class Line(object):

    NO_NONZERO_ELTS_FOUND_MSG = 'No nonzero elements found'

    def __init__(self, normal_vector=None, constant_term=None):
        self.dimension = 2

        if not normal_vector:
            all_zeros = ['0'] * self.dimension
            normal_vector = Vector(all_zeros)
        self.normal_vector = normal_vector

        if not constant_term:
            constant_term = Decimal('0')
        self.constant_term = Decimal(constant_term)

        self.set_basepoint()

    def set_basepoint(self):
        try:
            n = self.normal_vector
            c = self.constant_term
            basepoint_coords = ['0'] * self.dimension

            initial_index = Line.first_nonzero_index(n)
            initial_coefficient = n[initial_index]
            basepoint_coords[initial_index] = c / initial_coefficient
            self.basepoint = Vector(basepoint_coords)

        except Exception as e:
            if str(e) == Line.NO_NONZERO_ELTS_FOUND_MSG:
                self.basepoint = None
            else:
                raise e

    def __str__(self):

        num_decimal_places = 3

        def write_coefficient(coefficient, is_initial_term=False):
            coefficient = round(coefficient, num_decimal_places)
            if coefficient % 1 == 0:
                coefficient = int(coefficient)

            output = ''

            if coefficient < 0:
                output += '-'
            if coefficient > 0 and not is_initial_term:
                output += '+'

            if not is_initial_term:
                output += ' '

            if abs(coefficient) != 1:
                output += '{}'.format(abs(coefficient))

            return output

        n = self.normal_vector

        try:
            initial_index = Line.first_nonzero_index(n)
            terms = [write_coefficient(n[i],
                                       is_initial_term=(i == initial_index)) +
                     'x_{}'.format(i + 1)
                     for i in range(self.dimension)
                     if round(n[i], num_decimal_places) != 0]
            output = ' '.join(terms)

        except Exception as e:
            if str(e) == self.NO_NONZERO_ELTS_FOUND_MSG:
                output = '0'
            else:
                raise e

        constant = round(self.constant_term, num_decimal_places)
        if constant % 1 == 0:
            constant = int(constant)
        output += ' = {}'.format(constant)

        return output

    @staticmethod
    def first_nonzero_index(iterable):
        for k, item in enumerate(iterable):
            if not MyDecimal(item).is_near_zero():
                return k
        raise Exception(Line.NO_NONZERO_ELTS_FOUND_MSG)

    def is_parallel(self, line2):
        return self.normal_vector.is_parallel(line2.normal_vector)

    def __eq__(self, line2):
        if self.normal_vector.is_zero():
            if not line2.normal_vector.is_zero():
                return False

            diff = self.constant_term - line2.constant_term
            return MyDecimal(diff).is_near_zero()

        elif line2.normal_vector.is_zero():
            return False

        if not self.is_parallel(line2):
            return False

        basepoint_difference = self.basepoint.minus(line2.basepoint)
        return basepoint_difference.is_orthogonal(self.normal_vector)

    def intersection(self, line2):

        a, b = self.normal_vector.coordinates
        c, d = line2.normal_vector.coordinates
        k1 = self.constant_term
        k2 = line2.constant_term
        denom = ((a * d) - (b * c))

        if MyDecimal(denom).is_near_zero():
            if self == line2:
                return self
            else:
                return None

        one_over_denom = Decimal('1') / ((a * d) - (b * c))
        x_num = (d * k1 - b * k2)
        y_num = (-c * k1 + a * k2)

        return Vector([x_num, y_num]).times_scalar(one_over_denom)

# first system
# 4.046x + 2.836y = 1.21
# 10.115x + 7.09y = 3.025

line1 = Line(Vector([4.046, 2.836]), 1.21)
line2 = Line(Vector([10.115, 7.09]), 3.025)

print('first system instersects in: {}'.format(line1.intersection(line2)))

# second system
# 7.204x + 3.182y = 8.68
# 8.172x + 4.114y = 9.883

line3 = Line(Vector([7.204, 3.182]), 8.68)
line4 = Line(Vector([8.172, 4.114]), 9.883)

print('second system instersects in: {}'.format(line3.intersection(line4)))

# third system
# 1.182x + 5.562y = 6.744
# 1.773x + 8.343y = 9.525

line5 = Line(Vector([1.182, 5.562]), 6.744)
line6 = Line(Vector([1.773, 8.343]), 9.525)

print('third system instersects in: {}'.format(line5.intersection(line6)))
```

## 参考文献及资料

1. [**4.Coding Functions for Lines** of Linear Algebra Refresher Course from **Udacity.com**](https://classroom.udacity.com/courses/ud953/lessons/4624329808/concepts/48972186200923)
2. [**line.py & vector.py from Linear-Algebra-Refresher-Udacity**](https://github.com/omarrayward/Linear-Algebra-Refresher-Udacity)
2. [Line–line intersection](https://en.wikipedia.org/wiki/Line-line_intersection)
3. [Intersection](https://en.wikipedia.org/wiki/Intersection)