## Compile substrate on V2.0.0 RC2

[The official getting start tutorial](https://substrate.dev/docs/en/overview/getting-started/) wrote on version v2.0.0-alpha.5, which can't compile on v2.0.0-rc2, i wrote some changes to build on the version V2.0.0-rc2  (and speed up in China). 

### Fast Installation

Mac OS, Arch, or a Debian-based OS like Ubuntu:

```shell
curl https://getsubstrate.io -sSf | bash -s -- --fast
```

### Rust Developer Environment

Substrate uses the Rust programming language. You should [install Rust](https://www.rust-lang.org/tools/install) using `rustup`:

```shell
curl https://sh.rustup.rs -sSf | sh
```

We should setup our `RUSTUP_DIST_SERVER` first in China for speed up, here is the set up command in fish (if you are using bash or zsh please use "export" instead):

```shell
set RUSTUP_DIST_SERVER "https://mirrors.tuna.tsinghua.edu.cn/rustup"
```

Then make sure that you are using the latest Rust stable by default:

```shell
rustup default stable
```

### Wasm Compilation

Substrate uses WebAssembly (Wasm), and you will need to configure your Rust compiler to use `nightly` to support this build target. Run the following:

```shell
rustup install nightly-2020-05-15
rustup override set nightly-2020-05-15
rustup target add wasm32-unknown-unknown --toolchain nightly-2020-05-15
```

### Build the Project

Build the project with:

```shell
cargo build --release
```

## References

- https://github.com/substrate-developer-hub/tutorials/issues/44
- https://github.com/paritytech/substrate/issues/6167