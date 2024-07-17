# Basis3

## Overview

A Basis3 is a 3x3 matrix that can represent a combination of rotation and scale. It is used in many places in the ecosystem, such as transforms, physics, and rendering.

| Constructors |
|--------------|
| `Basis3()` |
| `Basis3(Vector3 x, Vector3 y, Vector3 z)` |
| `Basis3(Quaternion rotation)` |
| `Basis3(Vector3 scale)` |
| `Basis3(Quaternion rotation, Vector3 scale)` |
| `Basis3(Basis3 from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Basis3` | `(1, 0, 0, 0, 1, 0, 0, 0, 1)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `rotation` | `Quaternion` | Yes | Yes |
| `scale` | `Vector3` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `determinant()` | `Number` |
| `equals(Basis3 b)` | `Boolean` |
| `inverse()` | `Basis3` |
| `lerp(Basis3 b, Number weight)` | `Basis3` |
| `matrix()` | `Number[]` |
| `mul(Basis3 b)` | `Basis3` |
| `orthonormalized()` | `Basis3` |
| `orthonormalizeInPlace()` | `Undefined` |
| `rotate(Vector3 position)` | `Vector3` |
| `rowX()` | `Vector3` |
| `rowY()` | `Vector3` |
| `rowZ()` | `Vector3` |
| `transform(Vector3 position)` | `Vector3` |
| `transposed()` | `Basis3` |
| `transposeInPlace()` | `Undefined` |

## Constructor descriptions

### `Basis3` Basis3()

Creates a new basis with the values `(1, 0, 0, 0, 1, 0, 0, 0, 1)` (identity).

### `Basis3` Basis3(`Vector3` x, `Vector3` y, `Vector3` z)

Creates a new basis with the given vectors as the basis vectors.

### `Basis3` Basis3(`Quaternion` rotation)

Creates a new basis from the given rotation.

### `Basis3` Basis3(`Vector3` scale)

Creates a new basis from the given scale.

### `Basis3` Basis3(`Quaternion` rotation, `Vector3` scale)

Creates a new basis from the given rotation and scale.

### `Basis3` Basis3(`Basis3` from)

Creates a new basis from the given basis.

## Constant descriptions

### `Basis3` IDENTITY

The identity basis, with the values `(1, 0, 0, 0, 1, 0, 0, 0, 1)`. This basis has no rotation or scale, and any vector transformed by it will remain the same.

## Property descriptions

### `Quaternion` rotation

Quaternion representing the rotation of the basis.

### `Vector3` scale

Vector representing the scale of the basis.

## Method descriptions

### `Number` determinant()

Returns the determinant of the basis.

> [!WARNING]
> If the determinant is zero, the basis is not invertible.

### `Boolean` equals(`Basis3` b)

Returns whether this basis is equal or approximately equals to the given basis.

### `Basis3` inverse()

Returns the inverse of the basis. If the determinant is zero, the result is the identity basis.

### `Basis3` lerp(`Basis3` b, `Number` weight)

Returns a new basis that is the linear interpolation between this basis and the given basis.

### `Number[]` matrix()

Returns the basis as a 3x3 matrix. This matrix is represented as an array of 9 numbers.

### `Basis3` mul(`Basis3` b)

Returns the result of multiplying this basis by the given basis. This is equivalent to applying the transformations of both bases in sequence, and the result will be the same as multiplying the matrices of both bases, or the same as multiplying the quaternions and vectors of both bases.

### `Basis3` orthonormalized()

Returns a new basis that is orthonormalized. This means that the basis vectors are normalized and orthogonal to each other.

### `Undefined` orthonormalizeInPlace()

Orthonormalizes the basis in the same object.

### `Vector3` rotate(`Vector3` position)

Rotates the given position by the basis, ignoring the scale.

### `Vector3` rowX()

Returns the x basis vector.

### `Vector3` rowY()

Returns the y basis vector.

### `Vector3` rowZ()

Returns the z basis vector.

### `Vector3` transform(`Vector3` position)

Transforms the given position by the basis, including the scale.

### `Basis3` transposed()

Returns the transposed basis. This is equivalent to swapping the rows and columns of the basis matrix.

### `Undefined` transposeInPlace()

Transposes the basis in the same object.
