# TypeScript Build Tools and Tricks

- build TypeScript for different platforms

```json
{
  "scripts": {
    "build": "npm run build:es2015 && npm run build:esm && npm run build:cjs && npm run build:umd && npm run build:umd:min",
    "build:es2015": "tsc --module es2015 --target es2015 --outDir dist/es2015",
    "build:esm": "tsc --module es2015 --target es5 --outDir dist/esm",
    "build:cjs": "tsc --module commonjs --target es5 --outDir dist/cjs",
    "build:umd": "rollup dist/esm/index.js --format umd --name YourLibrary --sourceMap --output dist/umd/yourlibrary.js",
    "build:umd:min": "cd dist/umd && uglifyjs --compress --mangle --source-map --screw-ie8 --comments --o yourlibrary.min.js -- yourlibrary.js && gzip yourlibrary.min.js -c > yourlibrary.min.js.gz",
  }
}
```
