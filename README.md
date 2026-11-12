# clay-hex

A brick for [Clay](https://github.com/mseminatore/clay) that provides hex encoding, decoding and hexdumps for byte strings.

```clay
import("hex")

Hex encode("Hello") println        // 48656c6c6f
Hex decode("48656c6c6f") println   // Hello
Hex dump("Hello, world! 0123456789") println
// 00000000: 4865 6c6c 6f2c 2077 6f72 6c64 2120 3031  Hello, world! 01
// 00000010: 3233 3435 3637 3839                      23456789
```

## Install

```sh
clay bricks add github.com/mseminatore/clay-hex hex
```

## API

| Call | Returns |
|---|---|
| `Hex encode(data)` | the bytes of `data` as lower-case hex digits, two per byte |
| `Hex decode(text)` | the byte string for `text`: upper- or lower-case digits, with spaces, tabs and line ends skipped wherever they are (`"48 65 6c"`, or digits split over lines) |
| `Hex dump(data)` | an `xxd`-style listing: 8-digit offset, the bytes in pairs, 16 to a line, and the printable ASCII (`.` for the rest) |

A Clay String is a sequence of bytes, so everything works on any data: NUL bytes are kept, and
non-ASCII text is its UTF-8 bytes (`Hex encode("é")` is `"c3a9"`).

`dump` prints what `xxd` does (the tests were also checked against it), without the final newline.

### Errors

Mistakes raise a `RuntimeError` with a message that says what was wrong:

- `Hex decode("48F")` — `hex decode: odd-length input` (an odd number of digits, not counting whitespace)
- `Hex decode("48GG")` — `hex decode: invalid digit at position 2`; the position counts characters of the
  text you gave, whitespace included, and a bad digit is reported before an odd length
- `Hex encode(5)` — `hex encode: expects a String (got Number)` (`decode` and `dump` likewise)

## Testing

```sh
clay tests/test_hex.clay       # a brick can import itself by name
```

`.github/workflows/test.yml` runs the tests on Linux, macOS and Windows for every push and
pull request on GitHub (it builds Clay from source; pin `CLAY_REF` to a release once you
depend on one). On another Git host, delete it.
