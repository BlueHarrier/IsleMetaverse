# AABB

## Overview

An Axis-Aligned Bounding Box (AABB) is a box that is aligned with the axes of the coordinate system. It is defined by two points, the minimum and maximum extents of the box. It is used to determine if two objects are colliding, and is a common way to represent the bounds of an object.

| Constructors |
|--------------|
| `AABB()` |
| `AABB(Vector3 position, Vector3 size)` |
| `AABB(AABB from)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `position` | `Vector3` | Yes | Yes |
| `size` | `Vector3` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `area()` | `Number` |
| `contains(Vector3 point)` | `Boolean` |
| `encloses(AABB b)` | `Boolean` |
| `end()` | `Vector3` |
| `expand(Vector3 to)` | `Undefined` |
| `grown(Vector3 by)` | `AABB` |
| `growInPlace(Vector3 by)` | `Undefined` |
| `intersects(AABB b)` | `Boolean` |
| `merge(AABB b)` | `AABB` |
| `shrinkInPlace(Vector3 by)` | `Undefined` |
| `shrunken(Vector3 by)` | `AABB` |
| `start()` | `Vector3` |
| `volume()` | `Number` |

## Constructor descriptions

### `AABB` AABB()

Creates a new AABB with the values (0, 0, 0) for the position and size.

### `AABB` AABB(`Vector3` position, `Vector3` size)

Creates a new AABB with the given position and size.

### `AABB` AABB(`AABB` from)

Creates a new AABB from the given AABB.

## Property descriptions

### `Vector3` position

The position of the center of the AABB.

### `Vector3` size

The size of the AABB.

## Method descriptions

### `Number` area()

Returns the surface area of the AABB.

### `Boolean` contains(`Vector3` point)

Returns true if the AABB contains the given point.

### `Boolean` encloses(`AABB` b)

Returns true if the AABB completely encloses the given AABB. This means that all of b's points are inside the AABB.

### `Vector3` end()

Returns the point at the maximum extent of the AABB.

### `Undefined` expand(`Vector3` to)

Expands the AABB to include the given point.

### `AABB` grown(`Vector3` by)

Returns a new AABB that is grown by the given amount on all sides.

### `Undefined` growInPlace(`Vector3` by)

Grows the AABB by the given amount on all sides.

### `Boolean` intersects(`AABB` b)

Returns true if the AABB intersects the given AABB. Unlike `encloses`, this method only requires that the two AABBs touch, not that one completely contains the other.

### `AABB` merge(`AABB` b)

Returns a new AABB that is the union of this AABB and the given AABB.

### `Undefined` shrinkInPlace(`Vector3` by)

Shrinks the AABB by the given amount on all sides.

### `AABB` shrunken(`Vector3` by)

Returns a new AABB that is shrunk by the given amount on all sides.

### `Vector3` start()

Returns the point at the minimum extent of the AABB.

### `Number` volume()

Returns the volume of the AABB.
