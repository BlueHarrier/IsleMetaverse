# BBox3

## Overview

A BBox3 (bounding box in three dimensions) is an Axis-Aligned Bounding Box (AABB), which is a box that is aligned with the axes of the coordinate system. It is defined by two points, the minimum and maximum extents of the box. It is used to determine if two objects are colliding, and is a common way to represent the bounds of an object.

| Constructors |
|--------------|
| `BBox3()` |
| `BBox3(Vector3 position, Vector3 size)` |
| `BBox3(BBox3 from)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `position` | `Vector3` | Yes | Yes |
| `size` | `Vector3` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `area()` | `Number` |
| `contains(Vector3 point)` | `Boolean` |
| `encloses(BBox3 b)` | `Boolean` |
| `end()` | `Vector3` |
| `expand(Vector3 to)` | `Undefined` |
| `grown(Vector3 by)` | `BBox3` |
| `growInPlace(Vector3 by)` | `Undefined` |
| `intersects(BBox3 b)` | `Boolean` |
| `merge(BBox3 b)` | `BBox3` |
| `shrinkInPlace(Vector3 by)` | `Undefined` |
| `shrunken(Vector3 by)` | `BBox3` |
| `start()` | `Vector3` |
| `volume()` | `Number` |

## Constructor descriptions

### `BBox3` BBox3()

Creates a new BBox3 with the values (0, 0, 0) for the position and size.

### `BBox3` BBox3(`Vector3` position, `Vector3` size)

Creates a new BBox3 with the given position and size.

### `BBox3` BBox3(`BBox3` from)

Creates a new BBox3 from the given BBox3.

## Property descriptions

### `Vector3` position

The position of the center of the bounding box.

### `Vector3` size

The size of the bounding box.

## Method descriptions

### `Number` area()

Returns the surface area of the bounding box.

### `Boolean` contains(`Vector3` point)

Returns true if the bounding box contains the given point.

### `Boolean` encloses(`BBox3` b)

Returns true if the bounding box completely encloses the given BBox3. This means that all of b's points are inside the box.

### `Vector3` end()

Returns the point at the maximum extent of the bounding box.

### `Undefined` expand(`Vector3` to)

Expands the bounding box to include the given point.

### `BBox3` grown(`Vector3` by)

Returns a new BBox3 that is grown by the given amount on all sides.

### `Undefined` growInPlace(`Vector3` by)

Grows the bounding box by the given amount on all sides.

### `Boolean` intersects(`BBox3` b)

Returns true if the bounding box intersects the given BBox3. Unlike `encloses`, this method only requires that the two BBox3s touch, not that one completely contains the other.

### `BBox3` merge(`BBox3` b)

Returns a new BBox3 that is the union of this bounding box and the given BBox3.

### `Undefined` shrinkInPlace(`Vector3` by)

Shrinks the bounding box by the given amount on all sides.

### `BBox3` shrunken(`Vector3` by)

Returns a new BBox3 that is shrunk by the given amount on all sides.

### `Vector3` start()

Returns the point at the minimum extent of the bounding box.

### `Number` volume()

Returns the volume of the bounding box.
