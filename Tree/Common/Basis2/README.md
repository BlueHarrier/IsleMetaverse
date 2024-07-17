# Basis2

## Overview

A Basis2 is a 2x2 matrix, used for 2D transformations. It is used in many places in the ecosystem, such as transforms, physics, and rendering when working over canvases.

| Constructors |
|--------------|
| `Basis2()` |
| `Basis2(Vector2 x, Vector2 y)` |
| `Basis2(Number rotation)` |
| `Basis2(Vector2 scale)` |
| `Basis2(Number rotation, Vector2 scale)` |
| `Basis2(Basis2 from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Basis2` | `(1, 0, 0, 1)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `rotation` | `Number` | Yes | Yes |
| `scale` | `Vector2` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `determinant()` | `Number` |
| `equals(Basis2 b)` | `Boolean` |
| `inverse()` | `Basis2` |
| `matrix()` | `Number[]` |
| `mul(Basis2 b)` | `Basis2` |
| `rotate(Vector2 position)` | `Vector2` |
| `rowX()` | `Vector2` |
| `rowY()` | `Vector2` |
| `transform(Vector2 position)` | `Vector2` |
| `transposed()` | `Basis2` |
| `transposeInPlace()` | `Undefined` |

## Constructor descriptions

### `Basis2` Basis2()

Creates a new basis with the values `(1, 0, 0, 1)` (identity).

### `Basis2` Basis2(`Vector2` x, `Vector2` y)

Creates a new basis with the given vectors as the basis vectors.

### `Basis2` Basis2(`Number` rotation)

Creates a new basis from the given rotation in radians.

### `Basis2` Basis2(`Vector2` scale)

Creates a new basis from the given scale.

### `Basis2` Basis2(`Number` rotation, `Vector2` scale)

Creates a new basis from the given rotation and scale.

### `Basis2` Basis2(`Basis2` from)

Creates a new basis from the given basis.

## Property descriptions

### `Number` rotation

The rotation of the basis in radians.

### `Vector2` scale

The scale of the basis.

## Method descriptions

### `Number` determinant()

Returns the determinant of the basis.

> [!WARNING]
> If the determinant is zero, the basis is not invertible.

### `Boolean` equals(`Basis2` b)

Returns whether the basis is equal or approximately equal to another basis.

### `Basis2` inverse()

Returns the inverse of the basis. If the determinant is zero, the basis is not invertible, but the method will return an identity basis.

### `Number[]` matrix()

Returns the basis as a 2x2 matrix. This matrix is represented as an array of 4 numbers.

### `Basis2` mul(`Basis2` b)

Multiplies this basis by another basis, combining their transformations.

### `Vector2` rotate(`Vector2` position)

Rotates the given position by the basis, ignoring the scale.

### `Vector2` rowX()

Returns the first row of the basis.

### `Vector2` rowY()

Returns the second row of the basis.

### `Vector2` transform(`Vector2` position)

Transforms the given position by the basis, including the scale.

### `Basis2` transposed()

Returns a new basis that is transposed.

### `Undefined` transposeInPlace()

Transposes the basis in the same object.
