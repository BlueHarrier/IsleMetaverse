# Vector2

## Overview

A two dimensional vector, with x and y components. Contains basic operations like addition, subtraction, multiplications and divisions, as well as other vector math operations, like length and normalization.

| Constructor |
|-------------|
| `Vector2()` |
| `Vector2(Number x, Number y)` |
| `Vector2(Vector2 from)` |

| Constant | Type | Value |
|----------|------|-------|
| `DOWN` | `Vector2` | `(0, 1)` |
| `LEFT` | `Vector2` | `(-1, 0)` |
| `ONE` | `Vector2` | `(1, 1)` |
| `RIGHT` | `Vector2` | `(1, 0)` |
| `UP` | `Vector2` | `(0, -1)` |
| `ZERO` | `Vector2` | `(0, 0)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `x` | `Number` | Yes | Yes |
| `y` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `abs()` | `Vector2` |
| `add(Number b)` | `Vector2` |
| `addVector(Vector2 b)` | `Vector2` |
| `angle()` | `Number` |
| `angleTo(Vector2 position)` | `Number` |
| `angleWith(Vector2 b)` | `Number` |
| `ceil()` | `Vector2` |
| `clamp(Vector2 min, Vector2 max)` | `Vector2` |
| `cross(Vector2 b)` | `Number` |
| `div(Number b)` | `Vector2` |
| `divVector(Vector2 b)` | `Vector2` |
| `distance(Vector2 b)` | `Number` |
| `dot(Vector2 b)` | `Number` |
| `equals(Vector2 b)` | `Boolean` |
| `floor()` | `Vector2` |
| `greaterEquals(Vector2 b)` | `Boolean` |
| `greaterThan(Vector2 b)` | `Boolean` |
| `lerp(Vector2 b, Number weight)` | `Vector2` |
| `length()` | `Number` |
| `lengthSquared()` | `Number` |
| `lessEquals(Vector2 b)` | `Boolean` |
| `lessThan(Vector2 b)` | `Boolean` |
| `max(Number b)` | `Vector2` |
| `maxVector(Vector2 b)` | `Vector2` |
| `maxDistance(Number b)` | `Undefined` |
| `min(Number b)` | `Vector2` |
| `minVector(Vector2 b)` | `Vector2` |
| `minDistance(Number b)` | `Undefined` |
| `mod(Number b)` | `Vector2` |
| `modVector(Vector2 b)` | `Vector2` |
| `mul(Vector2 b)` | `Vector2` |
| `mulVector(Vector2 b)` | `Vector2` |
| `negate()` | `Vector2` |
| `normalized()` | `Vector2` |
| `normalizeInPlace()` | `Undefined` |
| `reflect(Vector2 b)` | `Vector2` |
| `rotate(Number angle)` | `Vector2` |
| `round()` | `Vector2` |
| `set(Number x, Number y)` | `Undefined` |
| `sub(Number b)` | `Vector2` |
| `subVector(Vector2 b)` | `Vector2` |

## Constructor descriptions

### Vector2()

Default constructor, populated with zeros on each component.

### Vector2(`Number` x, `Number` y)

Creates a vector from two numeric components.

### Vector2(`Vector2` from)

Creates a vector from another vector of the same length, making a clone of it.

## Constant descriptions

### `Vector2` DOWN

Represents the default two dimensional down, which is (0, 1).

### `Vector2` LEFT

Represents the default two dimensional left, which is (1, 0).

### `Vector2` ONE

A vector composed by ones, (1, 1).

### `Vector2` RIGHT

Represents the default two dimensional right, which is (-1, 0).

### `Vector2` UP

Represents the default two dimensional up, which is (0, -1).

### `Vector2` ZERO

A vector composed by zeros, (0, 0).

## Property descriptions

### `Number` x

Horizontal component of the vector.

### `Number` y

Vertical component of the vector.

## Method descriptions

### `Vector2` abs()

Returns the same as `Math.abs()`, but as a new vector, result of being performed for each component of the original one. The absolute value is the always positive value of a number.

### `Vector2` add(`Number` b)

Creates a new vector, result of adding the same number to each component individually.

### `Vector2` addVector(`Vector2` b)

Creates a new vector, result of adding each component individually.

### `Number` angle()

Returns the angle of the vector relative to `Vector2.RIGHT`, in radians.

### `Number` angleTo(`Vector2` position)

Checks the angle of the original vector to another vector, considering they're positions, and not directions. The angle is returned in radians.

### `Number` angleWith(`Vector2` b)

Returns the angle between the two vectors, in radians.

### `Vector2` ceil()

Returns the same as `Math.ceil()`, but as a new vector, result of being performed for each component of the original one. The ceil value is the value of a number rounded upwards to the next integer number.

### `Vector2` clamp(`Vector2` min, `Vector2` max)

Returns the same as `Math.clamp()`, but as a new vector, result of being performed for each component of the original one. Clamping a number is essentially forcing it to stay between the minimum and the maximum values.

### `Number` cross(`Vector2` b)

Returns the cross product with the other vector. This is usually not possible to do in two dimensions, but it's possible to calculate the cross product of two vectors in 3D space, by adding a third dimension to the vectors, and then calculating the cross product. The returning value would be the z component of the resulting vector.

### `Vector2` div(`Number` b)

Creates a new vector, result of dividing the same number to each component individually.

### `Vector2` divVector(`Vector2` b)

Creates a new vector, result of dividing each component individually.

### `Number` distance(`Vector2` b)

Returns the distance between the two vectors.

### `Number` dot(`Vector2` b)

Returns the dot product with the other vector, this is the multiplication between each component, and the posterior addition of all of their results.

### `Boolean` equals(`Vector2` b)

Checks if two vectors are equivalent, or approximately equivalent, in case they have decimals.

### `Vector2` floor()

Returns the same as `Math.floor()`, but as a new vector, result of being performed for each component of the original one. The floor value is the value of a number rounded downwards to the previous integer number.

### `Boolean` greaterEqual(`Vector2` b)

Returns true if all the components of the object are greater than or equals to b's.

### `Boolean` greaterThan(`Vector2` b)

Returns true if all the components of the object are greater than b's.

### `Vector2` lerp(`Vector2` b, `Number` weight)

Linearly interpolates each component of the vector using the given weight. The mathematical function behind the linear interpolation is `f(x) = x * a + (1 - x) * b`, where a is the first number, b the second, and x the weight.

### `Number` length()

Returns the length of the vector.

### `Number` lengthSquared()

Returns the squared length of the vector. This is useful for comparing the length of two vectors without the need of calculating the square root.

### `Boolean` lessEquals(`Vector2` b)

Returns true if all the components of the object are less than or equals to b's.

### `Boolean` lessThan(`Vector2` b)

Returns true if all the components of the object are less than b's.

### `Vector2` max(`Number` b)

Returns the result of performing `Math.max()` for each component of the original vector. The max value is the highest value of a number.

### `Undefined` maxDistance(`Number` b)

Prevents the vector from being longer than the given value. If the vector is longer than the given value, it will be shortened to match it.

### `Vector2` maxVector(`Vector2` b)

Returns the same as `Math.max()`, but as a new vector, result of being performed for each component of the original one. The max value is the highest value of a number.

### `Vector2` min(`Number` b)

Returns the result of performing `Math.min()` for each component of the original vector. The min value is the lowest value of a number.

### `Undefined` minDistance(`Number` b)

Prevents the vector from being shorter than the given value. If the vector is shorter than the given value, it will be lengthened to match it.

### `Vector2` minVector(`Vector2` b)

Returns the same as `Math.min()`, but as a new vector, result of being performed for each component of the original one. The min value is the lowest value of a number.

### `Vector2` mod(`Number` b)

Creates a new vector, result of obtaining the modulo of the same number to each component individually.

### `Vector2` modVector(`Vector2` b)

Creates a new vector, result of obtaining the modulo of each component individually.

### `Vector2` mul(`Number` b)

Creates a new vector, result of multiplying the same number to each component individually.

### `Vector2` mulVector(`Vector2` b)

Creates a new vector, result of multiplying each component individually.

### `Vector2` negative()

Returns the negative of the vector, which is the same as multiplying it by -1.

### `Vector2` normalized()

Returns a normalized copy of the vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

> [!CAUTION]
> If the length of the vector is 0, the resulting vector will be populated with zeros as well.

### `Undefined` normalizeInPlace()

Normalizes the vector in the same object, preventing the creation of a new vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

### `Vector2` reflect(`Vector2` b)

Creates a new vector, result of reflecting this one over b.

### `Vector2` round()

Returns the same as `Math.round()`, but as a new vector, result of being performed for each component of the original one. When rounding values, the number will become the closest integer.

### `Undefined` set(`Number` x, `Number` y)

Sets the x and y components of the vector at once.

### `Vector2` sub(`Number` b)

Creates a new vector, result of subtracting the same number to each component individually.

### `Vector2` subVector(`Vector2` b)

Creates a new vector, result of subtracting each component individually.

