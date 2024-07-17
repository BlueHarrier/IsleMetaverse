# Transform2

## Overview

A Transform2 is a 2D transformation matrix (3x3). It is used to store and manipulate 2D transformations in a way that is easy to work with. It can be used to set the position, rotation, and scale of a node, among other uses.

| Constructors |
|--------------|
| `Transform2()` |
| `Transform2(Vector2 position)` |
| `Transform2(Basis2 basis)` |
| `Transform2(Vector2 position, Basis2 basis)` |
| `Transform2(Transform2 from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Transform2` | `((1, 0, 0), (0, 1, 0), (0, 0, 1))` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `position` | `Vector2` | Yes | Yes |
| `basis` | `Basis2` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `equals(Transform2 b)` | `Boolean` |
| `inverse()` | `Transform2` |
| `lerp(Transform2 b, Number weight)` | `Transform2` |
| `matrix()` | `Number[]` |
| `mul(Transform2 b)` | `Transform2` |
| `transform(Vector2 position)` | `Vector2` |
| `transposed()` | `Transform2` |
| `transposeInPlace()` | `Undefined` |

## Constructor descriptions

### `Transform2` Transform2()

Creates a new transform with the values `((1, 0, 0), (0, 1, 0), (0, 0, 1))` (identity).

### `Transform2` Transform2(`Vector2` position)

Creates a new transform with the given position. The basis is set to the identity.

### `Transform2` Transform2(`Basis2` basis)

Creates a new transform with the given basis.

### `Transform2` Transform2(`Vector2` position, `Basis2` basis)

Creates a new transform with the given position and basis.

### `Transform2` Transform2(`Transform2` from)

Creates a new transform from the given transform.

## Constant descriptions

### `Transform2` IDENTITY

The identity transform, with the values ((1, 0, 0), (0, 1, 0), (0, 0, 1)).

## Property descriptions

### `Vector2` position

The position of the transform.

### `Basis2` basis

The basis of the transform.

## Method descriptions

### `Boolean` equals(`Transform2` b)

Returns true if this transform is equal or approximately equal to the given transform.

### `Transform2` inverse()

Returns the inverse of the transform.

### `Transform2` lerp(`Transform2` b, `Number` weight)

Returns a new transform that is the linear interpolation between this transform and the given transform.

### `Number[]` matrix()

Returns the transform as a 3x3 matrix. The matrix is represented as an array of 9 numbers.

### `Transform2` mul(`Transform2` b)

Returns a new transform that is the result of multiplying this transform by the given transform. This is equivalent to applying the transformations in order.

### `Vector2` transform(`Vector2` position)

Transforms the given position by this transform.

### `Transform2` transposed()

Returns a new transform that is the transpose of this transform.

### `Undefined` transposeInPlace()

Transposes this transform in the same object.
