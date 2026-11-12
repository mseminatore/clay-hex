# hex

Hex encoding, decoding and hexdumps for byte strings

```clay
import("hex")

Hex encode("Hello") println        // 48656c6c6f
Hex decode("48656c6c6f") println   // Hello
Hex dump(data) println             // xxd-style listing: offset, hex bytes, ASCII column

```

## Install

```sh
clay bricks add github.com/mseminatore/clay-hex hex
```

## Testing

```sh
clay tests/test_hex.clay       # a brick can import itself by name
```

`.github/workflows/test.yml` runs the tests on Linux, macOS and Windows for every push and
pull request on GitHub (it builds Clay from source; pin `CLAY_REF` to a release once you
depend on one). On another Git host, delete it.
