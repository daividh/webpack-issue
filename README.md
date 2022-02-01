## Goal

Provide a dead simple repository to reproduce a webpack issue.

```
ERROR in webpack/runtime/import chunk loading
Cannot read properties of undefined (reading 'getChunkConditionMap')
```

This issue is triggered when using together :

```
output: {
	module:  true,
	chunkFormat:  'module',
	chunkLoading:  'import',
},
```

and `url()` in a chunk generated and exported via MiniCssExtractPlugin

Error stask is the following

```
ERROR in webpack/runtime/import chunk loading
Cannot read properties of undefined (reading 'getChunkConditionMap')
TypeError: Cannot read properties of undefined (reading 'getChunkConditionMap')
    at ModuleChunkLoadingRuntimeModule.generate (/User/dav/webpack-issue/node_modules/webpack/lib/esm/ModuleChunkLoadingRuntimeModule.js:82:35)
    at ModuleChunkLoadingRuntimeModule.getGeneratedCode (/User/dav/webpack-issue/node_modules/webpack/lib/RuntimeModule.js:182:44)
    at ModuleChunkLoadingRuntimeModule.codeGeneration (/User/dav/webpack-issue/node_modules/webpack/lib/RuntimeModule.js:137:30)
    at /User/dav/webpack-issue/node_modules/webpack/lib/Compilation.js:3323:22
    at /User/dav/webpack-issue/node_modules/webpack/lib/Cache.js:93:5
    at Hook.eval [as callAsync] (eval at create (/User/dav/webpack-issue/node_modules/tapable/lib/HookCodeFactory.js:33:10), <anonymous>:6:1)
    at Cache.get (/User/dav/webpack-issue/node_modules/webpack/lib/Cache.js:75:18)
    at ItemCacheFacade.get (/User/dav/webpack-issue/node_modules/webpack/lib/CacheFacade.js:111:15)
    at Compilation._codeGenerationModule (/User/dav/webpack-issue/node_modules/webpack/lib/Compilation.js:3316:9)
    at codeGen (/User/dav/webpack-issue/node_modules/webpack/lib/Compilation.js:4826:11)
```
