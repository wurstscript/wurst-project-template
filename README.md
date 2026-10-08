# Wurst project template

A small Warcraft III map and a runnable Wurst example. Start with
`wurst/Hello.wurst`: it generates a custom unit at compile time, uses stock icon
and model constants with VS Code previews, and demonstrates vectors, method
chaining, and a timer closure.

## Getting started

Install the [Wurst VS Code extension](https://marketplace.visualstudio.com/items?itemName=peterzeller.wurst),
then run **Wurst: New Wurst Project**. The extension installs the compiler,
runtime, and Grill. Grill generates `wurst.build`, installs the standard library,
and configures the selected script mode and Warcraft III patch.

This repository supplies template files; `wurst.build` is generated per project,
and dependencies are installed under `_build/dependencies/`. For a direct clone,
add a `wurst.build` such as:

```yaml
projectName: HelloWurst
dependencies:
  - https://github.com/wurstscript/WurstStdlib2
```

Then run `grill install`. Open `wurst/Hello.wurst` and use the play button to run
the example, or build a distributable map with `grill build ExampleMap-folder.w3x`.
Build output goes in `_build/`.

## Map and imports

`ExampleMap-folder.w3x/` is an unpacked map directory. Keep the `.w3x` suffix: Wurst
recognizes it as a map, and builds a packed `.w3x` for distribution. Commit the
directory's contents, and edit its map data using the World Editor or the Wurst
extension. See the [map folder guide](https://wurstlang.org/news/map-folders-mpq-lua-guardrails.html).

Place additional assets in `imports/`; the build imports them into the map.
The included `dummy.mdx` is available for standard-library dummy units.
Use stock paths from `Icons` and `Units` without importing Warcraft III's assets.

## Compiler options

`wurst_run.args` accepts `-` for options used by both run and build, and `+` for
build-only options. Compile-time object generation and stack traces are enabled
for both. Inlining and optimizations are enabled only for builds, keeping test
runs quick and easier to debug. See the [Wurst manual](https://wurstlang.org/manual.html).

## Template distribution

`grill generate` supports `--map-format folder|archive` and defaults to folder
mode for Reforged. It selects the `map-folder` branch for folder projects and
`master` for archive projects.
