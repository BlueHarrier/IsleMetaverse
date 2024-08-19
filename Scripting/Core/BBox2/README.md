# BBox2

## Overview

A BBox2 (bounding box in two dimensions) is a rectangle shape defined by two points, the minimum and maximum extents. It is used to determine if two objects are colliding, and is a common way to represent the bounds of a two dimensional object.

| Constructors |
|--------------|
| `BBox2()` |
| `BBox2(Vector2 position, Vector2 size)` |
| `BBox2(BBox2 from)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `position` | `Vector2` | Yes | Yes |
| `size` | `Vector2` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `area()` | `Number` |
| `contains(Vector2 point)` | `Boolean` |
| `encloses(BBox2 b)` | `Boolean` |
| `end()` | `Vector2` |
| `expand(Vector2 to)` | `Undefined` |
| `grown(Vector2 by)` | `BBox2` |
| `growInPlace(Vector2 by)` | `Undefined` |
| `intersects(BBox2 b)` | `Boolean` |
| `merge(BBox2 b)` | `BBox2` |
| `shrinkInPlace(Vector2 by)` | `Undefined` |
| `shrunken(Vector2 by)` | `BBox2` |
| `start()` | `Vector2` |

## Constructor descriptions

### `BBox2` BBox2()

Creates a new BBox2 with the values (0, 0) for the position and size.

### `BBox2` BBox2(`Vector2` position, `Vector2` size)

Creates a new BBox2 with the given position and size.

### `BBox2` BBox2(`BBox2` from)

Creates a new BBox2 from the given BBox2.

## Property descriptions

### `Vector2` position

The position of the center of the bounding box.

### `Vector2` size

The size of the bounding box.

### `Number` area()

Returns the area of the bounding box.

### `Boolean` contains(`Vector2` point)

Returns true if the bounding box contains the given point.

### `Boolean` encloses(`BBox2` b)

Returns true if the bounding box encloses the given BBox2.

### `Vector2` end()

Returns the position of the bottom right corner of the bounding box.

### `Undefined` expand(`Vector2` to)

Expands the bounding box to include the given point.

### `BBox2` grown(`Vector2` by)

Returns a new BBox2 that is grown by the given amount.

### `Undefined` growInPlace(`Vector2` by)

Grows the bounding box by the given amount.

### `Boolean` intersects(`BBox2` b)

Returns true if the bounding box intersects the given BBox2.

### `BBox2` merge(`BBox2` b)

Returns a new BBox2 that is the union of the two bounding boxes.

### `Undefined` shrinkInPlace(`Vector2` by)

Shrinks the bounding box by the given amount.

### `BBox2` shrunken(`Vector2` by)

Returns a new BBox2 that is shrunk by the given amount.

### `Vector2` start()

Returns the position of the top left corner of the bounding box.
