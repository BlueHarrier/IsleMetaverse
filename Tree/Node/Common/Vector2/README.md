# Vector2

## Overview

A two dimensional vector, with x and y components. Contains basic operations like addition, subtraction, multiplications and divisions, as well as other vector math operations, like length and normalization.

| Constructor |
|-------------|
| `Vector2()` |
| `Vector2(Number x, Number y)` |
| `Vector2(Vector2 from)` |

| Constant | Type | Value |
|----------|------|-------|
| `DOWN` | `Vector2` | `(0, 1)` |
| `LEFT` | `Vector2` | `(-1, 0)` |
| `ONE` | `Vector2` | `(1, 1)` |
| `RIGHT` | `Vector2` | `(1, 0)` |
| `UP` | `Vector2` | `(0, -1)` |
| `ZERO` | `Vector2` | `(0, 0)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `x` | `Number` | Yes | Yes |
| `y` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `abs()` | `Vector2` |
| `add(Vector2 b)` | `Vector2` |
| `angleTo(Vector b)` | `Number` |
| `angleWith(Vector2 b)` | `Number` |
| `ceil()` | `Vector2` |
| `clamp(Vector2 min, Vector2 max)` | `Vector2` |
| `div(Vector2 b)` | `Vector2` |
| `distance(Vector2 b)` | `Number` |
| `dot(Vector2 b)` | `Number` |
| `equals(Vector2 b)` | `Boolean` |
| `flip()` | `Vector2` |
| `floor()` | `Vector2` |
| `greaterEquals(Vector2 b)` | `Boolean` |
| `greaterThan(Vector2 b)` | `Boolean` |
| `lerp(Vector2 b, Number weight)` | `Vector2` |
| `length()` | `Number` |
| `lessEquals(Vector2 b)` | `Boolean` |
| `lessThan(Vector2 b)` | `Boolean` |
| `mul(Vector2 b)` | `Vector2` |
| `normalized()` | `Vector2` |
| `reflect(Vector2 b)` | `Vector2` |
| `round()` | `Vector2` |
| `sub(Vector2 b)` | `Vector2` |
