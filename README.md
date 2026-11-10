# zlib-wasm

A zlib WebAssembly binary build with emscripten.

## Initialize and Build code

```
$ git clone https://github.com/PrivateBin/zlib-wasm.git
$ cd zlib-wasm
$ npm install
$ npm run build
$ npm test
```

## Example

```js
const myZlib = await require("./src/index").initialize();
const deflated = myZlib.deflate(buffer);
console.log(myZlib.inflate(deflated).equals(buffer));
```

## Benchmark

* NodeJS: v22.23.4
* OS: Ubuntu 24.04.5 LTS
* CPU: AMD Ryzen 5 3400G
* Memory: 32GB

```
$ npm run bench

> zlib-wasm@1.4 bench
> node benchmark/bench-1mbtxt.js

## lorem_1mb.txt size: 1000205
wasm x 17.71 ops/sec ±0.61% (48 runs sampled)
pako x 14.63 ops/sec ±2.68% (40 runs sampled)
native x 35.20 ops/sec ±0.59% (61 runs sampled)
Deflate: Fastest is native
## deflated lorem_1mb.txt size: 256560
wasm x 254 ops/sec ±3.26% (73 runs sampled)
pako x 202 ops/sec ±0.77% (85 runs sampled)
native x 634 ops/sec ±2.05% (88 runs sampled)
Inflate: Fastest is native
```
