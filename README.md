## Parcel bundle file size reproduction repo

A follow up on https://twitter.com/j_niewczas/status/1398620282550513667

## Setup
```
nvm use
yarn
yarn run build
```

You will see that the generated file is really huge:
```
dist/public/panel/index.html                318 B    604ms
dist/public/panel/index.eb835dd2.js     462.51 KB    3.62s
dist/public/panel/index.1152e663.css        104 B    2.62s
```

## Important note
Its possible that the file size is so huge because of `--no-scope-hoist` flag set BUT unfortunatelly without it project doesnt build at all.

Build error when not setting `--no-scope-hoist` flag:
```
Build failed.
@parcel/packager-js: The expression evaluated to a falsy value:

  (0, _assert().default)(typeof assetId === 'string')

AssertionError [ERR_ASSERTION]: The expression evaluated to a falsy value:

  (0, _assert().default)(typeof assetId === 'string')
```

### Build command I use:
```bash
NODE_ENV=production parcel build --no-source-maps \
                                 --no-scope-hoist \
                                 --cache-dir ./.tmp/build_cache \
                                 --dist-dir ./dist/public/panel \
                                 --public-url ./ \
                                 ./src/frontend/index.html
```