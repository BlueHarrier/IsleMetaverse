# Vector4

## Overview

A four dimensional vector, with x, y, z, and w components. Contains basic operations like addition, subtraction, multiplications and divisions, as well as other vector math operations, like length and normalization.

| Constructor |
|-------------|
| `Vector4()` |
| `Vector4(Number x, Number y, Number z, Number w)` |
| `Vector4(Vector2 from, Number z, Number w)` |
| `Vector4(Vector3 from, Number z)` |
| `Vector4(Vector4 from)` |

| Constant | Type | Value |
|----------|------|-------|
| `ONE` | `Vector4` | `(1, 1, 1, 1)` |
| `ZERO` | `Vector4` | `(0, 0, 0, 0)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `x` | `Number` | Yes | Yes |
| `y` | `Number` | Yes | Yes |
| `z` | `Number` | Yes | Yes |
| `w` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `abs()` | `Vector4` |
| `add(Number b)` | `Vector4` |
| `addVector(Vector4 b)` | `Vector4` |
| `ceil()` | `Vector4` |
| `clamp(Vector4 min, Vector4 max)` | `Vector4` |
| `div(Number b)` | `Vector4` |
| `divVector(Vector4 b)` | `Vector4` |
| `distance(Vector4 b)` | `Number` |
| `dot(Vector4 b)` | `Number` |
| `equals(Vector4 b)` | `Boolean` |
| `floor()` | `Vector4` |
| `greaterEquals(Vector4 b)` | `Boolean` |
| `greaterThan(Vector4 b)` | `Boolean` |
| `lerp(Vector4 b, Number weight)` | `Vector4` |
| `length()` | `Number` |
| `lengthSquared()` | `Number` |
| `lessEquals(Vector4 b)` | `Boolean` |
| `lessThan(Vector4 b)` | `Boolean` |
| `max(Number b)` | `Vector4` |
| `maxVector(Vector4 b)` | `Vector4` |
| `maxDistance(Number b)` | `Undefined` |
| `min(Number b)` | `Vector4` |
| `minVector(Vector4 b)` | `Vector4` |
| `minDistance(Number b)` | `Undefined` |
| `mod(Number b)` | `Vector4` |
| `modVector(Vector4 b)` | `Vector4` |
| `mul(Vector4 b)` | `Vector4` |
| `mulVector(Vector4 b)` | `Vector4` |
| `negate()` | `Vector4` |
| `normalized()` | `Vector4` |
| `normalizeInPlace()` | `Undefined` |
| `round()` | `Vector4` |
| `set(Number x, Number y, Number z, Number w)` | `Undefined` |
| `sub(Number b)` | `Vector4` |
| `subVector(Vector4 b)` | `Vector4` |

## Constructor descriptions

### Vector4()

Default constructor, populated with zeros on each component.

### Vector4(`Number` x, `Number` y, `Number` z, `Number` w)

Creates a vector from two numeric components.

### Vector4(`Vector2` from, `Number` z, `Number` w)

Creates a vector from a two dimensional vector and a two more components.

### Vector4(`Vector3` from, `Number` z)

Creates a vector from a three dimensional vector and a fourth component.

### Vector4(`Vector4` from)

Creates a vector from another vector of the same length, making a clone of it.

## Constant descriptions

### `Vector4` ONE

A vector composed by ones, (1, 1, 1, 1).

### `Vector4` ZERO

A vector composed by zeros, (0, 0, 0, 0).

## Property descriptions

### `Number` x

Horizontal component of the vector.

### `Number` y

Vertical component of the vector.

### `Number` z

Depth component of the vector.

### `Number` w

Fourth component of the vector.

## Method descriptions

### `Vector4` abs()

Returns the same as `Math.abs()`, but as a new vector, result of being performed for each component of the original one. The absolute value is the always positive value of a number.

### `Vector4` add(`Number` b)

Creates a new vector, result of adding the same number to each component individually.

### `Vector4` addVector(`Vector4` b)

Creates a new vector, result of adding each component individually.

### `Vector4` ceil()

Returns the same as `Math.ceil()`, but as a new vector, result of being performed for each component of the original one. The ceil value is the value of a number rounded upwards to the next integer number.

### `Vector4` clamp(`Vector4` min, `Vector4` max)

Returns the same as `Math.clamp()`, but as a new vector, result of being performed for each component of the original one. Clamping a number is essentially forcing it to stay between the minimum and the maximum values.

### `Vector4` div(`Number` b)

Creates a new vector, result of dividing the same number to each component individually.

### `Vector4` divVector(`Vector4` b)

Creates a new vector, result of dividing each component individually.

### `Number` distance(`Vector4` b)

Returns the distance between the two vectors.

### `Number` dot(`Vector4` b)

Returns the dot product with the other vector, this is the multiplication between each component, and the posterior addition of all of their results.

### `Boolean` equals(`Vector4` b)

Checks if two vectors are equivalent, or approximately equivalent, in case they have decimals.

### `Vector4` floor()

Returns the same as `Math.floor()`, but as a new vector, result of being performed for each component of the original one. The floor value is the value of a number rounded downwards to the previous integer number.

### `Boolean` greaterEqual(`Vector4` b)

Returns true if all the components of the object are greater than or equals to b's.

### `Boolean` greaterThan(`Vector4` b)

Returns true if all the components of the object are greater than b's.

### `Vector4` lerp(`Vector4` b, `Number` weight)

Linearly interpolates each component of the vector using the given weight. The mathematical function behind the linear interpolation is `f(x) = x * a + (1 - x) * b`, where a is the first number, b the second, and x the weight.

### `Number` length()

Returns the length of the vector.

### `Number` lengthSquared()

Returns the squared length of the vector. This is useful for comparing the length of two vectors without the need of calculating the square root.

### `Boolean` lessEquals(`Vector4` b)

Returns true if all the components of the object are less than or equals to b's.

### `Boolean` lessThan(`Vector4` b)

Returns true if all the components of the object are less than b's.

### `Vector4` max(`Number` b)

Returns the result of performing `Math.max()` for each component of the original vector. The max value is the highest value of a number.

### `Undefined` maxDistance(`Number` b)

Prevents the vector from being longer than the given value. If the vector is longer than the given value, it will be shortened to match it.

### `Vector4` maxVector(`Vector4` b)

Returns the same as `Math.max()`, but as a new vector, result of being performed for each component of the original one. The max value is the highest value of a number.

### `Vector4` min(`Number` b)

Returns the result of performing `Math.min()` for each component of the original vector. The min value is the lowest value of a number.

### `Undefined` minDistance(`Number` b)

Prevents the vector from being shorter than the given value. If the vector is shorter than the given value, it will be lengthened to match it.

### `Vector4` minVector(`Vector4` b)

Returns the same as `Math.min()`, but as a new vector, result of being performed for each component of the original one. The min value is the lowest value of a number.

### `Vector4` mod(`Number` b)

Creates a new vector, result of obtaining the modulo of the same number to each component individually.

### `Vector4` modVector(`Vector4` b)

Creates a new vector, result of obtaining the modulo of each component individually.

### `Vector4` mul(`Number` b)

Creates a new vector, result of multiplying the same number to each component individually.

### `Vector4` mulVector(`Vector4` b)

Creates a new vector, result of multiplying each component individually.

### `Vector4` negative()

Returns the negative of the vector, which is the same as multiplying it by -1.

### `Vector4` normalized()

Returns a normalized copy of the vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

> [!CAUTION]
> If the length of the vector is 0, the resulting vector will be populated with zeros as well.

### `Undefined` normalizeInPlace()

Normalizes the vector in the same object, preventing the creation of a new vector. A normalized vector's length is always one, and it's the result of running `vec.div(vec.length())`.

### `Vector4` round()

Returns the same as `Math.round()`, but as a new vector, result of being performed for each component of the original one. When rounding values, the number will become the closest integer.

### `Undefined` set(`Number` x, `Number` y, `Number` z, `Number` w)

Sets the x, y, z, and w components of the vector at once.

### `Vector4` sub(`Number` b)

Creates a new vector, result of subtracting the same number to each component individually.

### `Vector4` subVector(`Vector4` b)

Creates a new vector, result of subtracting each component individually.

