itoa
====

[![Build Status](https://api.travis-ci.org/dtolnay/itoa.svg?branch=master)](https://travis-ci.org/dtolnay/itoa)
[![Latest Version](https://img.shields.io/crates/v/itoa.svg)](https://crates.io/crates/itoa)

This crate provides fast functions for printing integer primitives to an
[`io::Write`](https://doc.rust-lang.org/std/io/trait.Write.html). The
implementation comes straight from
[libcore](https://github.com/rust-lang/rust/blob/b8214dc6c6fc20d0a660fb5700dca9ebf51ebe89/src/libcore/fmt/num.rs#L201-L254)
but avoids the performance penalty of going through
[`fmt::Formatter`](https://doc.rust-lang.org/std/fmt/struct.Formatter.html).

See also [`dtoa`](https://github.com/dtolnay/dtoa) for printing floating point
primitives.

## Performance

![performance](https://raw.githubusercontent.com/dtolnay/itoa/master/performance.png)

## Functions

```rust
extern crate itoa;

let mut buf = Vec::new();
itoa::write(&mut buf, 128u64).unwrap();
```

The function signature is:

```rust
fn write<W: io::Write + ?Sized, V: itoa::Integer>(writer: &mut W, value: V) -> io::Result<()>
```

where `itoa::Integer` is implemented for `i8`, `u8`, `i16`, `u16`, `i32`, `u32`,
`i64`, `u64`, `isize` and `usize`.

## Dependency

Itoa is available on [crates.io](https://crates.io/crates/itoa). Use the
following in `Cargo.toml`:

```toml
[dependencies]
itoa = "0.2"
```

## License

Licensed under either of

 * Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in itoa by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
