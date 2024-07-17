# Vector3

## Overview

A three dimensional vector, with x, y, and z components. Contains basic operations like addition, subtraction, multiplications and divisions, as well as other vector math operations, like length and normalization.

| Constructor |
|-------------|
| `Vector3()` |
| `Vector3(Number x, Number y, Number z)` |
| `Vector3(Vector2 from, Number z)` |
| `Vector3(Vector3 from)` |

| Constant | Type | Value |
|----------|------|-------|
| `BACK` | `Vector3` | `(0, 0, -1)` |
| `DOWN` | `Vector3` | `(0, -1, 0)` |
| `FORWARD` | `Vector3` | `(0, 0, 1)` |
| `LEFT` | `Vector3` | `(-1, 0, 0)` |
| `ONE` | `Vector3` | `(1, 1, 1)` |
| `RIGHT` | `Vector3` | `(1, 0, 0)` |
| `UP` | `Vector3` | `(0, 1, 0)` |
| `ZERO` | `Vector3` | `(0, 0, 0)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `x` | `Number` | Yes | Yes |
| `y` | `Number` | Yes | Yes |
| `z` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `abs()` | `Vector3` |
| `add(Number b)` | `Vector3` |
| `addVector(Vector3 b)` | `Vector3` |
| `angleWith(Vector3 b)` | `Number` |
| `ceil()` | `Vector3` |
| `clamp(Vector3 min, Vector3 max)` | `Vector3` |
| `cross(Vector3 b)` | `Number` |
| `div(Number b)` | `Vector3` |
| `divVector(Vector3 b)` | `Vector3` |
| `distance(Vector3 b)` | `Number` |
| `dot(Vector3 b)` | `Number` |
| `equals(Vector3 b)` | `Boolean` |
| `floor()` | `Vector3` |
| `greaterEquals(Vector3 b)` | `Boolean` |
| `greaterThan(Vector3 b)` | `Boolean` |
| `lerp(Vector3 b, Number weight)` | `Vector3` |
| `length()` | `Number` |
| `lengthSquared()` | `Number` |
| `lessEquals(Vector3 b)` | `Boolean` |
| `lessThan(Vector3 b)` | `Boolean` |
| `max(Number b)` | `Vector3` |
| `maxVector(Vector3 b)` | `Vector3` |
| `maxDistance(Number b)` | `Undefined` |
| `min(Number b)` | `Vector3` |
| `minVector(Vector3 b)` | `Vector3` |
| `minDistance(Number b)` | `Undefined` |
| `mod(Number b)` | `Vector3` |
| `modVector(Vector3 b)` | `Vector3` |
| `mul(Vector3 b)` | `Vector3` |
| `mulVector(Vector3 b)` | `Vector3` |
| `negate()` | `Vector3` |
| `normalized()` | `Vector3` |
| `normalizeInPlace()` | `Undefined` |
| `reflect(Vector3 b)` | `Vector3` |
| `round()` | `Vector3` |
| `set(Number x, Number y, Number z)` | `Undefined` |
| `sub(Number b)` | `Vector3` |
| `subVector(Vector3 b)` | `Vector3` |

## Constructor descriptions

### Vector3()

Default constructor, populated with zeros on each component.

### Vector3(`Number` x, `Number` y, `Number` z)

Creates a vector from two numeric components.

### Vector3(`Vector2` from, `Number` z)

Creates a vector from a two dimensional vector and a third component.

### Vector3(`Vector3` from)

Creates a vector from another vector of the same length, making a clone of it.

## Constant descriptions

### `Vector3` BACK

Represents the default three dimensional back, which is (0, 0, -1).

### `Vector3` DOWN

Represents the default three dimensional down, which is (0, -1, 0).

### `Vector3` FORWARD

Represents the default three dimensional forward, which is (0, 0, 1).

### `Vector3` LEFT

Represents the default three dimensional left, which is (-1, 0, 0).

### `Vector3` ONE

A vector composed by ones, (1, 1, 1).

### `Vector3` RIGHT

Represents the default three dimensional right, which is (1, 0, 0).

### `Vector3` UP

Represents the default three dimensional up, which is (0, 1, 0).

### `Vector3` ZERO

A vector composed by zeros, (0, 0, 0).

## Property descriptions

### `Number` x

Horizontal component of the vector.

### `Number` y

Vertical component of the vector.

### `Number` z

Depth component of the vector.

## Method descriptions

### `Vector3` abs()

Returns the same as `Math.abs()`, but as a new vector, result of being performed for each component of the original one. The absolute value is the always positive value of a number.

### `Vector3` add(`Number` b)

Creates a new vector, result of adding the same number to each component individually.

### `Vector3` addVector(`Vector3` b)

Creates a new vector, result of adding each component individually.

### `Number` angleWith(`Vector3` b)

Returns the shortest angle between the two vectors, in radians.

### `Vector3` ceil()

Returns the same as `Math.ceil()`, but as a new vector, result of being performed for each component of the original one. The ceil value is the value of a number rounded upwards to the next integer number.

### `Vector3` clamp(`Vector3` min, `Vector3` max)

Returns the same as `Math.clamp()`, but as a new vector, result of being performed for each component of the original one. Clamping a number is essentially forcing it to stay between the minimum and the maximum values.

### `Number` cross(`Vector3` b)

Returns the cross product with the other vector. The cross product is a vector that is perpendicular to the two vectors being multiplied.

### `Vector3` div(`Number` b)

Creates a new vector, result of dividing the same number to each component individually.

### `Vector3` divVector(`Vector3` b)

Creates a new vector, result of dividing each component individually.

### `Number` distance(`Vector3` b)

Returns the distance between the two vectors.

### `Number` dot(`Vector3` b)

Returns the dot product with the other vector, this is the multiplication between each component, and the posterior addition of all of their results.

### `Boolean` equals(`Vector3` b)

Checks if two vectors are equivalent, or approximately equivalent, in case they have decimals.

### `Vector3` floor()

Returns the same as `Math.floor()`, but as a new vector, result of being performed for each component of the original one. The floor value is the value of a number rounded downwards to the previous integer number.

### `Boolean` greaterEqual(`Vector3` b)

Returns true if all the components of the object are greater than or equals to b's.

### `Boolean` greaterThan(`Vector3` b)

Returns true if all the components of the object are greater than b's.

### `Vector3` lerp(`Vector3` b, `Number` weight)

Linearly interpolates each component of the vector using the given weight. The mathematical function behind the linear interpolation is `f(x) = x * a + (1 - x) * b`, where a is the first number, b the second, and x the weight.

### `Number` length()

Returns the length of the vector.

### `Number` lengthSquared()

Returns the squared length of the vector. This is useful for comparing the length of two vectors without the need of calculating the square root.

### `Boolean` lessEquals(`Vector3` b)

Returns true if all the components of the object are less than or equals to b's.

### `Boolean` lessThan(`Vector3` b)

Returns true if all the components of the object are less than b's.

### `Vector3` max(`Number` b)

Returns the result of performing `Math.max()` for each component of the original vector. The max value is the highest value of a number.

### `Undefined` maxDistance(`Number` b)

Prevents the vector from being longer than the given value. If the vector is longer than the given value, it will be shortened to match it.

### `Vector3` maxVector(`Vector3` b)

Returns the same as `Math.max()`, but as a new vector, result of being performed for each component of the original one. The max value is the highest value of a number.

### `Vector3` min(`Number` b)

Returns the result of performing `Math.min()` for each component of the original vector. The min value is the lowest value of a number.

### `Undefined` minDistance(`Number` b)

Prevents the vector from being shorter than the given value. If the vector is shorter than the given value, it will be lengthened to match it.

### `Vector3` minVector(`Vector3` b)

Returns the same as `Math.min()`, but as a new vector, result of being performed for each component of the original one. The min value is the lowest value of a number.

### `Vector3` mod(`Number` b)

Creates a new vector, result of obtaining the modulo of the same number to each component individually.

### `Vector3` modVector(`Vector3` b)

Creates a new vector, result of obtaining the modulo of each component individually.

### `Vector3` mul(`Number` b)

Creates a new vector, result of multiplying the same number to each component individually.

### `Vector3` mulVector(`Vector3` b)

Creates a new vector, result of multiplying each component individually.

### `Vector3` negative()

Returns the negative of the vector, which is the same as multiplying it by -1.

### `Vector3` normalized()

Returns a normalized copy of the vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

> [!CAUTION]
> If the length of the vector is 0, the resulting vector will be populated with zeros as well.

### `Undefined` normalizeInPlace()

Normalizes the vector in the same object, preventing the creation of a new vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

### `Vector3` reflect(`Vector3` b)

Creates a new vector, result of reflecting this one over b.

### `Vector3` round()

Returns the same as `Math.round()`, but as a new vector, result of being performed for each component of the original one. When rounding values, the number will become the closest integer.

### `Undefined` set(`Number` x, `Number` y, `Number` z)

Sets the x, y, and z components of the vector at once.

### `Vector3` sub(`Number` b)

Creates a new vector, result of subtracting the same number to each component individually.

### `Vector3` subVector(`Vector3` b)

Creates a new vector, result of subtracting each component individually.

