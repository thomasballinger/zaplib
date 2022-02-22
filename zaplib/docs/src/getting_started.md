# Getting Started

## Installation

1. [Install Rust](https://www.rust-lang.org/tools/install)
2. Clone Zaplib:

```
git clone https://github.com/Zaplib/zaplib.git
```

3. Navigate to the repo, install the Cargo extension for Zaplib, and the dependencies:

```
cd zaplib
cargo install cargo-zaplib
cargo zaplib install-deps
```

If you're going to do local development of Zaplib, be sure to add the `--devel` flag which installs some more dependencies, like [CEF](https://github.com/chromiumembedded) binaries.

```
cd zaplib
cargo install cargo-zaplib
cargo zaplib install-deps --devel
```

## Examples

Now you're ready to run a simple example natively. Here are some fun ones to play with:
* `cargo run -p example_single_button`
* `cargo run -p example_charts`
* `cargo run -p example_text`
* `cargo run -p example_lightning --release` (best to do a release build; see below)
* `cargo run -p example_bigedit --release` (best to do a release build; see below)

Feel free to check out the `examples` directory for more examples to play with!

**Warning:** On Mac we currently have a memory leak bug, so some examples might crash after a while. Windows doens't work at all currently. Linux hasn't been tested very well recently. WebAssembly (below) should generally work well though. Early alpha software.. stay tuned!

##  WebAssembly Build

Of course, Zaplib is a WebAssembly framework, so let's run these in **Chrome** (more browser support coming soon):

1. Build all the examples:
   
```
cargo zaplib build --workspace
```

Or just a single example:

```
cargo zaplib build -p example_single_button
```

2. Run a basic server:

```
cargo zaplib serve
```

3. Navigate your browser to: 

[`http://localhost:3000/zaplib/examples/example_single_button`](http://localhost:3000/zaplib/examples/example_single_button)

## Release Build

For a more performant build, add the `--release` flag, e.g.:


### Native

```
cargo run -p example_single_button --release
```

### WebAssembly

```
cargo zaplib build -p example_single_button --release
```

You'll also need to add the `?release` query param:

[`http://localhost:3000/zaplib/examples/example_single_button/?release`](http://localhost:3000/zaplib/examples/example_single_button/?release)


## Generate Docs

To view automatically generated API documentation, run:

```
zaplib/scripts/build_rustdoc.sh
```

## Next Steps

* Set up your [tooling](./basic_tooling.md).
* Dive into some tutorials.
* Look at the code for one of the examples ([`example_single_button`](https://github.com/Zaplib/zaplib/blob/main/zaplib/examples/example_single_button/src/single_button.rs) is a great simple one to start with) and try to modify it.
