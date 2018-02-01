# Park-Miller-Carta PRNG [WIP]

*(documentation in progress)*
This is a multi-language repository, demonstrating C-Rust-Node.js-Web interoperability.

It utilizes Rust as a build system, in order to compile [the original C implemetations by Robin Whittle](http://www.firstpr.com.au/dsp/rand31/). A faithful Rust port is also included, cross-compilable to asm.js and WebAssembly via [Emscripten](https://github.com/kripken/emscripten), for use in Node.js and browsers.

## Using from Rust
Add `park-miller-carta-prng` to `[dependencies]` in `Cargo.toml`

main.rs:
```rust
extern crate prng;
use prng::PRNG;

fn main() {
    let mut prng = PRNG::new(1);
    let random_float = prng.next_unsigned_float();
    assert_eq!(0.000007826369, random_float);

    let random_int = prng.next_unsigned_integer();
    assert_eq!(282475249, random_int);
}
```

## Getting Started
1. Clone the repository:
`git clone https://github.com/kenOfYugen/rust_node_wasm`
2. Enter the directory:
`cd rust_node_wasm`
3. Build (add the `--release` flag for optimized builds)
  * Rust-C static/dynamic libraries: `cargo b`
  * asm.js library: `cargo b --target asmjs-unknown-emscripten`
  * wasm library: `cargo b --target wasm32-unknown-emscripter`
  * Node.js: `npm run build:all`

### Prerequisites
* Rust, get it via [rustup](https://www.rustup.rs/).
* [Node.js](https://nodejs.org/en/) for running asm.js/wasm.
* [emsdk](https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm), for compilation to asm.js/wasm.
