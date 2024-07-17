# Basis

## Overview

A Basis is a 3x3 matrix that can represent a combination of rotation and scale. It is used in many places in the ecosystem, such as transforms, physics, and rendering.

| Constructors |
|--------------|
| `Basis()` |
| `Basis(Vector3 x, Vector3 y, Vector3 z)` |
| `Basis(Quaternion rotation)` |
| `Basis(Vector3 scale)` |
| `Basis(Quaternion rotation, Vector3 scale)` |
| `Basis(Basis from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Basis` | `(1, 0, 0, 0, 1, 0, 0, 0, 1)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `rotation` | `Quaternion` | Yes | Yes |
| `scale` | `Vector3` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `determinant()` | `Number` |
| `equals(Basis b)` | `Boolean` |
| `inverse()` | `Basis` |
| `matrix()` | `Number[]` |
| `mul(Basis b)` | `Basis` |
| `orthonormalized()` | `Basis` |
| `orthonormalizeInPlace()` | `Undefined` |
| `rotate(Vector3 position)` | `Vector3` |
| `rowX()` | `Vector3` |
| `rowY()` | `Vector3` |
| `rowZ()` | `Vector3` |
| `transform(Vector3 position)` | `Vector3` |
| `transposed()` | `Basis` |
| `transposeInPlace()` | `Undefined` |

## Constructor descriptions

### `Basis` Basis()

Creates a new basis with the values `(1, 0, 0, 0, 1, 0, 0, 0, 1)` (identity).

### `Basis` Basis(`Vector3` x, `Vector3` y, `Vector3` z)

Creates a new basis with the given vectors as the basis vectors.

### `Basis` Basis(`Quaternion` rotation)

Creates a new basis from the given rotation.

### `Basis` Basis(`Vector3` scale)

Creates a new basis from the given scale.

### `Basis` Basis(`Quaternion` rotation, `Vector3` scale)

Creates a new basis from the given rotation and scale.

### `Basis` Basis(`Basis` from)

Creates a new basis from the given basis.

## Constant descriptions

### `Basis` IDENTITY

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

### `Boolean` equals(`Basis` b)

Returns whether this basis is equal or approximately equals to the given basis.

### `Basis` inverse()

Returns the inverse of the basis. If the determinant is zero, the result is the identity basis.

### `Number[]` matrix()

Returns the basis as a 3x3 matrix. This matrix is represented as an array of 9 numbers.

### `Basis` mul(`Basis` b)

Returns the result of multiplying this basis by the given basis. This is equivalent to applying the transformations of both bases in sequence, and the result will be the same as multiplying the matrices of both bases, or the same as multiplying the quaternions and vectors of both bases.

### `Basis` orthonormalized()

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

### `Basis` transposed()

Returns the transposed basis. This is equivalent to swapping the rows and columns of the basis matrix.

### `Undefined` transposeInPlace()

Transposes the basis in the same object.
