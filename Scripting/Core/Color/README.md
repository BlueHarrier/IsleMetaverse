# Color

## Overview

A Color is a representation of an RGBA color value. It is used to store and manipulate colors in a way that is easy to work with. It can be used to set the color of a material, or to change the color of a sprite, among other uses. It also supports HDR colors, which can be used to create more realistic lighting effects by overloading a specific channel beyond 255 (1.0).

| Constructors |
|--------------|
| `Color()` |
| `Color(Number r, Number g, Number b)` |
| `Color(Number r, Number g, Number b, Number a)` |
| `Color(String hex)` |
| `Color(Vector3 rgb)` |
| `Color(Vector4 rgba)` |
| `Color(Color from)` |

| Constants | Type | Value |
|-----------|------|-------|
| `BLACK` | `Color` | `(0, 0, 0, 1)` |
| `BLUE` | `Color` | `(0, 0, 1, 1)` |
| `CYAN` | `Color` | `(0, 1, 1, 1)` |
| `GRAY` | `Color` | `(0.5, 0.5, 0.5, 1)` |
| `GREEN` | `Color` | `(0, 1, 0, 1)` |
| `MAGENTA` | `Color` | `(1, 0, 1, 1)` |
| `RED` | `Color` | `(1, 0, 0, 1)` |
| `TRANSPARENT` | `Color` | `(0, 0, 0, 0)` |
| `WHITE` | `Color` | `(1, 1, 1, 1)` |
| `YELLOW` | `Color` | `(1, 1, 0, 1)` |

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `r` | `Number` | Yes | Yes |
| `g` | `Number` | Yes | Yes |
| `b` | `Number` | Yes | Yes |
| `a` | `Number` | Yes | Yes |

| Method | Returns |
|--------|---------|
| `abs()` | `Color` |
| `add(Number b)` | `Color` |
| `addColor(Color b)` | `Color` |
| `blend(Color b)` | `Color` |
| `clamp(Color min, Color max)` | `Color` |
| `div(Number b)` | `Color` |
| `divColor(Color b)` | `Color` |
| `equals(Color b)` | `Boolean` |
| `greaterEquals(Color b)` | `Boolean` |
| `greaterThan(Color b)` | `Boolean` |
| `hex(Boolean includeAlpha)` | `String` |
| `intB()` | `Number` |
| `intG()` | `Number` |
| `intR()` | `Number` |
| `lerp(Color b, Number weight)` | `Color` |
| `lessEquals(Color b)` | `Boolean` |
| `lessThan(Color b)` | `Boolean` |
| `max(Color b)` | `Color` |
| `min(Color b)` | `Color` |
| `mod(Number b)` | `Color` |
| `modColor(Color b)` | `Color` |
| `mul(Number b)` | `Color` |
| `mulColor(Color b)` | `Color` |
| `negative()` | `Color` |
| `negateInPlace()` | `Undefined` |
| `set(Number r, Number g, Number b)` | `Undefined` |
| `setAlpha(Number r, Number g, Number b, Number a)` | `Undefined` |
| `sub(Number b)` | `Color` |
| `subColor(Color b)` | `Color` |

## Constructor descriptions

### `Color` Color()

Creates a new Color with the values (0, 0, 0, 1), which is black.

### `Color` Color(`Number` r, `Number` g, `Number` b)

Creates a new Color with the given red, green, and blue values, and an alpha value of 1.

### `Color` Color(`Number` r, `Number` g, `Number` b, `Number` a)

Creates a new Color with the given red, green, blue, and alpha values.

### `Color` Color(`String` hex)

Creates a new Color from the given hex string. The hex string should be in the format `#RRGGBB` or `#RRGGBBAA`.

> [!NOTE]
> This constructor does not support HDR colors, due to the limitations of the hex format.

### `Color` Color(`Vector3` rgb)

Creates a new Color from the given Vector3, with the red, green, and blue values set to the x, y, and z components, respectively. The alpha value is set to 1.

### `Color` Color(`Vector4` rgba)

Creates a new Color from the given Vector4, with the red, green, blue, and alpha values set to the x, y, z, and w components, respectively.

### `Color` Color(`Color` from)

Creates a new Color from the given Color.

## Constant descriptions

### `Color` BLACK

Represents the color black, which is `(0, 0, 0, 1)`.

### `Color` BLUE

Represents the color blue, which is `(0, 0, 1, 1)`.

### `Color` CYAN

Represents the color cyan, which is `(0, 1, 1, 1)`.

### `Color` GRAY

Represents the color gray, which is `(0.5, 0.5, 0.5, 1)`.

### `Color` GREEN

Represents the color green, which is `(0, 1, 0, 1)`.

### `Color` MAGENTA

Represents the color magenta, which is `(1, 0, 1, 1)`.

### `Color` RED

Represents the color red, which is `(1, 0, 0, 1)`.

### `Color` TRANSPARENT

Represents a transparent black color, which is `(0, 0, 0, 0)`.

### `Color` WHITE

Represents the color white, which is `(1, 1, 1, 1)`.

### `Color` YELLOW

Represents the color yellow, which is `(1, 1, 0, 1)`.

## Property descriptions

### `Number` r

The red component of the color, from 0 to 1, or over it for HDR colors.

### `Number` g

The green component of the color, from 0 to 1, or over it for HDR colors.

### `Number` b

The blue component of the color, from 0 to 1, or over it for HDR colors.

### `Number` a

The alpha component of the color, from 0 to 1.

## Method descriptions

### `Color` abs()

Similar to `Math.abs()`, returns a new color with the absolute value of each component.

### `Color` add(`Number` b)

Returns a new color with the given number added to each component.

### `Color` addColor(`Color` b)

Returns a new color by adding each component by the corresponding component of the given color.

### `Color` blend(`Color` b)

Blends the color over the given color, returning a new color.

### `Color` clamp(`Color` min, `Color` max)

Similar to `Math.clamp()`, returns a new color with each component clamped between the min and max colors.

### `Color` div(`Number` b)

Returns a new color with the given number divided by each component.

### `Color` divColor(`Color` b)

Returns a new color by dividing each component by the corresponding component of the given color.

### `Boolean` equals(`Color` b)

Returns true if the color is equal to the given color.

### `Boolean` greaterEquals(`Color` b)

Returns true if the color is greater than or equal to the given color.

### `Boolean` greaterThan(`Color` b)

Returns true if the color is greater than the given color.

### `String` hex(`Boolean` includeAlpha)

Returns the color as a hex string `#RRGGBB`, optionally including the alpha channel (`#RRGGBBAA`).

### `Number` intB()

Returns the blue component as an integer between 0 and 255, or beyond if it's an HDR color.

### `Number` intG()

Returns the green component as an integer between 0 and 255, or beyond if it's an HDR color.

### `Number` intR()

Returns the red component as an integer between 0 and 255, or beyond if it's an HDR color.

### `Color` lerp(`Color` b, `Number` weight)

Similar to `Math.lerp()`, returns a new color that is a linear interpolation between this color and the given color.

### `Boolean` lessEquals(`Color` b)

Returns true if the color is less than or equal to the given color.

### `Boolean` lessThan(`Color` b)

Returns true if the color is less than the given color.

### `Color` max(`Color` b)

Similar to `Math.max()`, returns a new color with the maximum value of each component.

### `Color` min(`Color` b)

Similar to `Math.min()`, returns a new color with the minimum value of each component.

### `Color` mod(`Number` b)

Returns a new color with the given number modulo each component.

### `Color` modColor(`Color` b)

Returns a new color by taking the modulo of each component by the corresponding component of the given color.

### `Color` mul(`Number` b)

Returns a new color with the given number multiplied by each component.

### `Color` mulColor(`Color` b)

Returns a new color by multiplying each component by the corresponding component of the given color.

### `Color` negative()

Returns the negative of the color, which is `(1 - r, 1 - g, 1 - b, a)`.

### `Undefined` negateInPlace()

Negates the color in place, setting it to its negative value.

### `Undefined` set(`Number` r, `Number` g, `Number` b)

Sets the red, green, and blue components of the color at once.

### `Undefined` setAlpha(`Number` r, `Number` g, `Number` b, `Number` a)

Sets the red, green, blue, and alpha components of the color at once.

### `Color` sub(`Number` b)

Returns a new color with the given number subtracted from each component.

### `Color` subColor(`Color` b)

Returns a new color by subtracting each component by the corresponding component of the given color.
