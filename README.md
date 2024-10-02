

To build for wasm (Web)

Install a nightly build of rustc, the wasm32-unknown-emscripten target for rustc, and rust-src. The reason why nightly rustc is required is the unstable flag to build std (-Zbuild-std). Assuming that Rust was installed with rustup, this is quite simple.

```zsh
rustup toolchain install nightly
rustup component add rust-src --toolchain nightly
rustup target add wasm32-unknown-emscripten --toolchain nightly
```

Next, install Emscripten. The simplest way to achieve this is to install emsdk from the git repo. We recommended version 3.1.39 for now.1


```zsh
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install 3.1.39
./emsdk activate 3.1.39
source ./emsdk.sh     (or ./emsdk.bat on windows)
```

```zsh
cargo +nightly build -Zbuild-std --target wasm32-unknown-emscripten
```