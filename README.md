
# CARVE

CARVE (Cade Andgreg's Risc-V Emulator) is a project developed under [Dr. Marz](https://www.eecs.utk.edu/people/stephen-marz/). CARVE is deployable as a web application, and is hosted at [carve.chemicaldevelopment.us](https://carve.chemicaldevelopment.us). It has been tested with many platforms, and relies only on a modern web browser with a modern JavaScript engine and [WASM](https://webassembly.org/) support.

## Building

This section is not relevant for most people -- it doesn't need to be built by end users. But, if you want to build a custom version, or you're writing the project, this is for you.

You should install the [Emscripten SDK](https://emscripten.org/docs/getting_started/downloads.html). Before you run any commands below, you'll probably have to activate it:

```shell
$ source "/path/to/emsdk/emsdk_env.sh"
```

(replacing `/path/to` with the path to your Emscripten SDK)

Now, to build `libcarve`, which is the C bindings and emulator, you can run:

```shell
$ make
```

## Running

You'll need to install NodeJS/npm to run the web app.

You'll need to install with `npm install`

Then, to serve, run `npm run serve`

## Adding an Instruction

To add an instruction, you need to do these steps:

  * Copy an existing entry in `tools/riscvdata.py`, within one of the extensions (for example, `RV32I`). This should be a tuple containing `(name, kind, opcode, f3, f7)`, modify it to match the new instruction
  * In the corresponding header for that extension (in `src/ext`, for example, `src/ext/RV32I.h`), add a macro with the name `CARVE_<name>(args...)`. You can copy an existing one to get started
  * Now, re-run `make update` (or whatever `make` command you wish). The relevant files will be updated if the data changes, or their generator scripts change

If you want to add an instruction of a new type, you will have to implement that type on your own (although )
