# Transform3

## Overview

A Transform3 is a 3D transformation matrix (4x4). It is used to store and manipulate 3D transformations in a way that is easy to work with. It can be used to set the position, rotation, and scale of a node, among other uses.

| Constructors |
|--------------|
| `Transform3()` |
| `Transform3(Vector3 position)` |
| `Transform3(Basis3 basis)` |
| `Transform3(Vector3 position, Basis3 basis)` |
| `Transform3(Transform3 from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Transform3` | `((1, 0, 0, 0), (0, 1, 0, 0), (0, 0, 1, 0), (0, 0, 0, 1))` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `basis` | `Basis3` | Yes | Yes |
| `position` | `Vector3` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `equals(Transform3 b)` | `Boolean` |
| `inverse()` | `Transform3` |
| `lerp(Transform3 b, Number weight)` | `Transform3` |
| `matrix()` | `Number[]` |
| `mul(Transform3 b)` | `Transform3` |
| `transform(Vector3 position)` | `Vector3` |
| `transposed()` | `Transform3` |
| `transposeInPlace()` | `Undefined` |

## Constructor descriptions

### `Transform3` Transform3()

Creates a new transform with the values ((1, 0, 0, 0), (0, 1, 0, 0), (0, 0, 1, 0), (0, 0, 0, 1)) (identity).

### `Transform3` Transform3(`Vector3` position)

Creates a new transform with the given position. The basis is set to the identity.

### `Transform3` Transform3(`Basis3` basis)

Creates a new transform with the given basis.

### `Transform3` Transform3(`Vector3` position, `Basis3` basis)

Creates a new transform with the given position and basis.

### `Transform3` Transform3(`Transform3` from)

Creates a new transform from the given transform.

## Constant descriptions

### `Transform3` IDENTITY

Creates a new transform with the values ((1, 0, 0, 0), (0, 1, 0, 0), (0, 0, 1, 0), (0, 0, 0, 1)) (identity).

## Property descriptions

### `Basis3` basis

The basis of the transform.

### `Vector3` position

The position of the transform.

## Method descriptions

### `Boolean` equals(`Transform3` b)

Compares this transform to another transform and returns true if they are equal or approximately equal.

### `Transform3` inverse()

Returns the inverse of the transform.

### `Transform3` lerp(`Transform3` b, `Number` weight)

Linearly interpolates between this transform and another transform by the given weight.

### `Number[]` matrix()

Returns the transform as a 4x4 matrix. The matrix is represented by an array of 16 numbers.

### `Transform3` mul(`Transform3` b)

Multiplies this transform by another transform. This combines their transformations.

### `Vector3` transform(`Vector3` position)

Transforms the given position by this transform.

### `Transform3` transposed()

Returns a new transform that is the transpose of this transform.

### `Undefined` transposeInPlace()

Transposes this transform in the same object.
