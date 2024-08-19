# Quaternion

## Overview

Quaternions are used to represent rotations in 3D space. They are more efficient than Euler angles, and avoid the problem of gimbal lock. Quaternions are not as intuitive as Euler angles, but they are more stable and can be interpolated. They're also more efficient when concatenating multiple rotations.

| Constructors |
|--------------|
| `Quaternion()` |
| `Quaternion(Number x, Number y, Number z, Number w)` |
| `Quaternion(Vector3 euler)` |
| `Quaternion(Vector3 axis, Number angle)` |
| `Quaternion(Vector4 from)` |
| `Quaternion(Quaternion from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `IDENTITY` | `Quaternion` | `(0, 0, 0, 1)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `x` | `Number` | Yes | Yes |
| `y` | `Number` | Yes | Yes |
| `z` | `Number` | Yes | Yes |
| `w` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `angle()` | `Number` |
| `angleTo(Quaternion b)` | `Number` |
| `axis()` | `Vector3` |
| `dot(Quaternion b)` | `Number` |
| `equals(Quaternion b)` | `Boolean` |
| `euler()` | `Vector3` |
| `inverse()` | `Quaternion` |
| `length()` | `Number` |
| `lengthSquared()` | `Number` |
| `mul(Quaternion b)` | `Quaternion` |
| `normalized()` | `Quaternion` |
| `normalizeInPlace()` | `Undefined` |
| `rotate(Vector3 axis, Number angle)` | `Quaternion` |
| `set(Number x, Number y, Number z, Number w)` | `Undefined` |
| `setAxisAngle(Vector3 axis, Number angle)` | `Undefined` |
| `setEuler(Vector3 euler)` | `Undefined` |
| `slerp(Quaternion b, Number weight)` | `Quaternion` |

## Constructor descriptions

### `Quaternion` Quaternion()

Creates a new quaternion with the values `(0, 0, 0, 1)` (identity).

### `Quaternion` Quaternion(`Number` x, `Number` y, `Number` z, `Number` w)

Creates a new quaternion with the given values.

### `Quaternion` Quaternion(`Vector3` euler)

Creates a new quaternion from the given Euler angles, in order of rotation: pitch (X), yaw (Y), and roll (Z).

### `Quaternion` Quaternion(`Vector3` axis, `Number` angle)

Creates a new quaternion from the rotation through the given axis.

### `Quaternion` Quaternion(`Vector4` from)

Creates a new quaternion from the given four dimensional vector, simulating it's another quaternion.

### `Quaternion` Quaternion(`Quaternion` from)

Creates a new quaternion from the given quaternion.

## Constants descriptions

### `IDENTITY` `Quaternion`

The identity quaternion, with the values `(0, 0, 0, 1)`. Multiplying any quaternion by the identity quaternion will result in the original quaternion.

## Property descriptions

### `Number` x

The x component of the quaternion.

### `Number` y

The y component of the quaternion.

### `Number` z

The z component of the quaternion.

### `Number` w

The w component of the quaternion.

## Method descriptions

### `Number` angle()

Returns the angle of the rotation represented by the quaternion.

### `Number` angleTo(`Quaternion` b)

Returns the angle between this quaternion and the given quaternion.

### `Vector3` axis()

Returns the axis of the rotation represented by the quaternion.

### `Number` dot(`Quaternion` b)

Returns the dot product of this quaternion and the given quaternion.

### `Boolean` equals(`Quaternion` b)

Returns whether this quaternion is equal or approximately equals to the given quaternion.

### `Vector3` euler()

Returns the Euler angles represented by the quaternion, in order of rotation: pitch (X), yaw (Y), and roll (Z).

### `Quaternion` inverse()

Returns the inverse of the quaternion.

### `Number` length()

Returns the length of the quaternion.

### `Number` lengthSquared()

Returns the squared length of the quaternion, which is faster to calculate than the length.

### `Quaternion` mul(`Quaternion` b)

Returns the result of multiplying this quaternion by the given quaternion.

### `Quaternion` normalized()

Returns the normalized quaternion.

### `Undefined` normalizeInPlace()

Normalizes the quaternion in the same object.

### `Quaternion` rotate(`Vector3` axis, `Number` angle)

Rotates the quaternion through the given axis and angle.

### `Undefined` set(`Number` x, `Number` y, `Number` z, `Number` w)

Sets the values of the quaternion all at once.

### `Undefined` setAxisAngle(`Vector3` axis, `Number` angle)

Sets the quaternion from the rotation through the given axis.

### `Undefined` setEuler(`Vector3` euler)

Sets the quaternion from the given Euler angles, in order of rotation: pitch (X), yaw (Y), and roll (Z).

### `Quaternion` slerp(`Quaternion` b, `Number` weight)

Similar to `Math.lerp()`, returns the spherical linear interpolation between this quaternion and the given quaternion.
