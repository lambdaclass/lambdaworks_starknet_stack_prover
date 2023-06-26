# Lambdaworks Cairo Prover

We're still moving all the code from [LambdaWorks](https://github.com/lambdaclass/lambdaworks) related to the STARK Cairo prover.
The CI, the documentation and the GPU code hasn't yet been yet migrated.

Disclaimer: This prover is still in development and may contain bugs. It is not intended to be used in production yet.

## Main building blocks

- [STARKS](https://github.com/lambdaclass/lambdaworks_cairo_prover/tree/main/src/starks): Everything related to STARKs building blocks such as the prover, verifier and FRI.
- [Cairo](https://github.com/lambdaclass/lambdaworks_cairo_prover/tree/main/src/cairo): Implementation of the Cairo AIR.

To be added:

- Grinding
- Skipping FRI layers
- Optimizing verifier operations
- Range-check and Pedersen built-ins
- Different layouts

## Requirements

- Cargo 1.69+
  
## How to try it

For the moment, only programs in Cairo 0 with no arguments and contracts in Cairo 1 with no arguments are supported.

### Using Docker compiler for Cairo 0 programs

Build the compiler image with:

`make docker_build_cairo_compiler`

Then for example, if you have a Cairo program in the project folder, you can use:

`make docker_compile_and_run PROGRAM=program_name.cairo`

### Using cairo-compile for Cairo 0 programs

If you have `cairo-lang`installed, you can use it instead of the Dockerfile

Then for example, if you have some Cairo program in the project folder, you can use:

`make compile_and_run PROGRAM=program_name.cairo`

### Compiling Cairo 1 contracts

To run, prove and verify Cairo 1 contracts, use the following command:

``` bash
cargo run -- <PATH-TO-casm-FILE>
```

for example:

``` bash
cargo run -- cairo_programs/fibonacci.casm
```
