# botbuilder-azure repro for issue #804

Issue: [botbuilder-azure should install runtime-dependent type files](https://github.com/Microsoft/botbuilder-js/issues/804)

Repro Steps:

1. Clone repo
1. `npm install`

After install, the package will automatically build. The failure is:

```
node_modules/botbuilder-azure/lib/cosmosDbStorage.d.ts:9:50 - error TS7016: Could not find a declaration file for module 'documentdb'. '/Users/chris/Source/temp/node_modules/documentdb/index.js' implicitly has an 'any' type.
  Try `npm install @types/documentdb` if it exists or add a new declaration (.d.ts) file containing `declare module 'documentdb';`

9 import { ConnectionPolicy, RequestOptions } from 'documentdb';
```

To fix the issue, run `npm i @types/documentdb` in this package, or ideally, in the declaring package `botbuilder-azure`.