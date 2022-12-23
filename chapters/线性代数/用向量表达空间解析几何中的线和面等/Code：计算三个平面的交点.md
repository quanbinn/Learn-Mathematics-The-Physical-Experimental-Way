# Code：计算三个平面的交点

## 打开实验文件

- 单击右方的[onlinegdb](https://www.onlinegdb.com/online_python_compiler)，浏览器里会打开一个新的页面，把下面的这些代码段分别拷贝到main.py下面的空白栏中，然后单击空白栏最上面一栏的按键“Run”。

```python
from decimal import Decimal, getcontext
from copy import deepcopy

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

class Plane(object):

    NO_NONZERO_ELTS_FOUND_MSG = 'No nonzero elements found'

    def __init__(self, normal_vector=None, constant_term=None):
        self.dimension = 3

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

            initial_index = Plane.first_nonzero_index(n)
            initial_coefficient = n[initial_index]

            basepoint_coords[initial_index] = c / initial_coefficient
            self.basepoint = Vector(basepoint_coords)

        except Exception as e:
            if str(e) == Plane.NO_NONZERO_ELTS_FOUND_MSG:
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
            initial_index = Plane.first_nonzero_index(n)
            terms = [write_coefficient(
                     n[i], is_initial_term=(i == initial_index)) +
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

    def is_parallel(self, plane2):
        return self.normal_vector.is_parallel(plane2.normal_vector)

    def __eq__(self, plane2):
        if self.normal_vector.is_zero():
            if not plane2.normal_vector.is_zero():
                return False

            diff = self.constant_term - plane2.constant_term
            return MyDecimal(diff).is_near_zero()

        elif plane2.normal_vector.is_zero():
            return False

        if not self.is_parallel(plane2):
            return False

        basepoint_difference = self.basepoint.minus(plane2.basepoint)
        return basepoint_difference.is_orthogonal(self.normal_vector)

    def __iter__(self):
        self.current = 0
        return self

    def next(self):
        if self.current >= len(self.normal_vector):
            raise StopIteration
        else:
            current_value = self.normal_vector[self.current]
            self.current += 1
            return current_value

    def __len__(self):
        return len(self.normal_vector)

    def __getitem__(self, i):
        return self.normal_vector[i]

    @staticmethod
    def first_nonzero_index(iterable):
        for k, item in enumerate(iterable):
            if not MyDecimal(item).is_near_zero():
                return k
        raise Exception(Plane.NO_NONZERO_ELTS_FOUND_MSG)

class LinearSystem(object):

    ALL_PLANES_MUST_BE_IN_SAME_DIM_MSG = ('All planes in the system should '
                                          'live in the same dimension')
    NO_SOLUTIONS_MSG = 'No solutions'
    INF_SOLUTIONS_MSG = 'Infinitely many solutions'

    def __init__(self, planes):
        try:
            d = planes[0].dimension
            for p in planes:
                assert p.dimension == d

            self.planes = planes
            self.dimension = d

        except AssertionError:
            raise Exception(self.ALL_PLANES_MUST_BE_IN_SAME_DIM_MSG)

    def __len__(self):
        return len(self.planes)

    def __getitem__(self, i):
        return self.planes[i]

    def __setitem__(self, i, x):
        try:
            assert x.dimension == self.dimension
            self.planes[i] = x

        except AssertionError:
            raise Exception(self.ALL_PLANES_MUST_BE_IN_SAME_DIM_MSG)

    def __str__(self):
        ret = 'Linear System:\n'
        temp = ['Equation {}: {}'.format(i + 1, p)
                for i, p in enumerate(self.planes)]
        ret += '\n'.join(temp)
        return ret

    def swap_rows(self, row1, row2):
        self[row1], self[row2] = self[row2], self[row1]

    def multiply_coefficient_and_row(self, coefficient, row):
        self[row] = _get_new_plane(coefficient, self[row])

    def add_multiple_times_row_to_row(self, coefficient, row_to_add,
                                      row_to_be_added_to):
        recipient_plane = self[row_to_be_added_to]
        new_plane = _get_new_plane(coefficient, self[row_to_add])
        new_normal_vector = \
            recipient_plane.normal_vector.plus(new_plane.normal_vector)
        constant_term = new_plane.constant_term + recipient_plane.constant_term
        self[row_to_be_added_to] = Hyperplane(normal_vector=new_normal_vector,
                                              constant_term=constant_term)

    def indices_of_first_nonzero_terms_in_each_row(self):
        num_equations = len(self)

        indices = [-1] * num_equations

        for i, p in enumerate(self.planes):
            try:
                p.first_nonzero_index(p.normal_vector)
                indices[i] = p.first_nonzero_index(p.normal_vector)
            except Exception as e:
                if str(e) == Plane.NO_NONZERO_ELTS_FOUND_MSG:
                    continue
                else:
                    raise e

        return indices

    def compute_triangular_form(self):
        system = deepcopy(self)

        num_equations = len(system)
        num_variables = system.dimension

        col = 0
        for row in range(num_equations):
            while col < num_variables:
                c = MyDecimal(system[row].normal_vector[col])
                if c.is_near_zero():
                    swap_succeeded = system.did_swap_with_row_below(row, col)
                    if not swap_succeeded:
                        col += 1
                        continue

                system.clear_coefficients_bellow(row, col)
                col += 1
                break

        return system

    def did_swap_with_row_below(self, row, col):
        num_equations = len(self)

        for k in range(row + 1, num_equations):
            coefficient = MyDecimal(self[k].normal_vector[col])
            if not coefficient.is_near_zero():
                self.swap_rows(row, k)
                return True

        return False

    def clear_coefficients_bellow(self, row, col):
        num_equations = len(self)
        beta = MyDecimal(self[row].normal_vector[col])

        for row_to_be_added_to in range(row + 1, num_equations):
            n = self[row_to_be_added_to].normal_vector
            gamma = n[col]
            alpha = -gamma / beta
            self.add_multiple_times_row_to_row(alpha, row, row_to_be_added_to)

    def clear_coefficients_above(self, row, col):
        for row_to_be_added_to in range(row)[::-1]:
            n = self[row_to_be_added_to].normal_vector
            alpha = -(n[col])
            self.add_multiple_times_row_to_row(alpha, row, row_to_be_added_to)

    def compute_rref(self):
        tf = self.compute_triangular_form()

        num_equations = len(tf)
        pivot_indices = tf.indices_of_first_nonzero_terms_in_each_row()

        for row in range(num_equations)[::-1]:
            pivot_var = pivot_indices[row]
            if pivot_var < 0:
                continue
            tf.scale_row_to_make_coefficient_equal_one(row, pivot_var)
            tf.clear_coefficients_above(row, pivot_var)

        return tf

    def scale_row_to_make_coefficient_equal_one(self, row, col):
        n = self[row].normal_vector
        beta = Decimal('1.0') / n[col]
        self.multiply_coefficient_and_row(beta, row)

    def do_gaussian_elimination(self):
        rref = self.compute_rref()

        try:
            rref.raise_excepion_if_contradictory_equation()
            rref.raise_excepion_if_too_few_pivots()
        except Exception as e:
            return e.message

        num_variables = rref.dimension
        solution_coordinates = [rref.planes[i].constant_term
                                for i in range(num_variables)]

        return Vector(solution_coordinates)

    def raise_excepion_if_contradictory_equation(self):
        for plane in self.planes:
            try:
                plane.first_nonzero_index(plane.normal_vector)

            except Exception as e:
                if str(e) == 'No nonzero elements found':
                    constant_term = MyDecimal(plane.constant_term)
                    if not constant_term.is_near_zero():
                        raise Exception(self.NO_SOLUTIONS_MSG)

                else:
                    raise e

    def raise_excepion_if_too_few_pivots(self):
        pivot_indices = self.indices_of_first_nonzero_terms_in_each_row()
        num_pivots = sum([1 if index >= 0 else 0 for index in pivot_indices])
        num_variables = self.dimension

        if num_pivots < num_variables:
            raise Exception(self.INF_SOLUTIONS_MSG)

    def compute_solution(self):
        try:
            return self.do_gaussian_elimination_and_parametrization()

        except Exception as e:
            if str(e) == self.NO_SOLUTIONS_MSG:
                return str(e)
            else:
                raise e

    def do_gaussian_elimination_and_parametrization(self):
        rref = self.compute_rref()
        rref.raise_excepion_if_contradictory_equation()

        direction_vectors = rref.extract_direction_vectors_for_parametrization()  # NOQA
        basepoint = rref.extract_basepoint_for_parametrization()

        return Parametrization(basepoint, direction_vectors)

    def extract_direction_vectors_for_parametrization(self):
        num_variables = self.dimension
        pivot_indices = self.indices_of_first_nonzero_terms_in_each_row()
        free_variable_indices = set(range(num_variables)) - set(pivot_indices)

        direction_vectors = []

        for free_var in free_variable_indices:
            vector_coords = [0] * num_variables
            vector_coords[free_var] = 1
            for index, plane in enumerate(self.planes):
                pivot_var = pivot_indices[index]
                if pivot_var < 0:
                    break
                vector_coords[pivot_var] = -plane.normal_vector[free_var]

            direction_vectors.append(Vector(vector_coords))

        return direction_vectors

    def extract_basepoint_for_parametrization(self):
        num_variables = self.dimension
        pivot_indices = self.indices_of_first_nonzero_terms_in_each_row()

        basepoint_coords = [0] * num_variables

        for index, plane in enumerate(self.planes):
            pivot_var = pivot_indices[index]
            if pivot_var < 0:
                break
            basepoint_coords[pivot_var] = plane.constant_term

        return Vector(basepoint_coords)

class MyDecimal(Decimal):
    def is_near_zero(self, eps=1e-10):
        return abs(self) < eps

p0 = Plane(normal_vector=Vector(['1','1','1']), constant_term='1')
p1 = Plane(normal_vector=Vector(['0','1','0']), constant_term='2')
p2 = Plane(normal_vector=Vector(['1','1','-1']), constant_term='3')
p3 = Plane(normal_vector=Vector(['1','0','-2']), constant_term='2')

s = LinearSystem([p0,p1,p2,p3])

print(s.indices_of_first_nonzero_terms_in_each_row())
print('{},{},{},{}'.format(s[0],s[1],s[2],s[3]))
print(len(s))
print(s)

s[0] = p1
print(s)

print(MyDecimal('1e-9').is_near_zero())
print(MyDecimal('1e-11').is_near_zero())
```

## 参考文献及资料

1. [**22.Coding GE Solution** of Linear Algebra Refresher Course from **Udacity.com**](https://classroom.udacity.com/courses/ud953/lessons/4624329808/concepts/48972186200923)
2. [**linear_system.py, plane.py & vector.py from Linear-Algebra-Refresher-Udacity**](https://github.com/omarrayward/Linear-Algebra-Refresher-Udacity)