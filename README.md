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

## Develop

```sh
clay tests/test_hex.clay       # a brick can import itself by name
```

`.github/workflows/test.yml` runs the tests on Linux, macOS and Windows for every push and
pull request on GitHub (it builds Clay from source; pin `CLAY_REF` to a release once you
depend on one). On another Git host, delete it.

## Publish

1. Choose a license and add a `LICENSE` file.
2. Fill in `description` in `brick.json`, commit, and push to GitHub (or another Git host).
3. Tag a release: `git tag v0.1.0 && git push --tags`.
4. To let people find it, list it in the
   [clay-registry](https://github.com/mseminatore/clay-registry) with a pull request.
