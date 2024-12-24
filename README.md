# rust-wasm-sdl2-template

A template project for Rust + WebAssembly + SDL2 (+ Dear ImGui).

The file main.rs is mostly copied from
[here](https://github.com/imgui-rs/imgui-sdl2-support/blob/main/examples/sdl2_01_basic.rs),
and the file index.html is mostly copied from
[here](https://github.com/gregbuchholz/RuSDLem/blob/main/index-wasm.html).

## Running the example
Make sure that you have Emscripten installed and that the
Emscripten environment variables are set
(`source emsdk_env.sh` on Linux).

To add the Emscripten target:

    rustup target add wasm32-unknown-emscripten

To build:

    cargo build --target=wasm32-unknown-emscripten

To run:

    emrun index.html

## Explanation of modifications for WebAssembly
The file .cargo/config.toml specifies some linker arguments.
The `MIN_WEBGL_VERSION=2` argument is necessary to prevent errors
related to the software not supporting WebGL 1.
`ASYNCIFY` and `ALLOW_MEMORY_GROWTH` are explained
[here](https://github.com/gregbuchholz/RuSDLem/tree/main?tab=readme-ov-file#further-details).
Similarly, main.rs has a line added to enable Asyncify.
Otherwise, main.rs is identical to the stock imgui-sdl2-support example.

The "debug_message_insert_support" feature of imgui-glow-renderer needs to be disabled.

Tested with Emscripten 3.1.50 and Rust 1.83.0.
