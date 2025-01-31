#Cache Breaking Tasks

This is a fork of [Shaky Shane's cache-breaker](https://github.com/shakyShane/cache-breaker) to fix dependency issues.

**Note: This modules does nothing with the file system, that means you'll have to read/write files yourself, or wait for
the Grunt & Gulp Plugins**


##Install

```
npm install AkuraDavis/cache-breaker
```

##Use in project

```
var cacheBreaker = require("cache-breaker");
```

###Usage Examples

**Append a timestamp as query string**

```js
var string   = '<link href="/style.css" /><link href="/style2.css" />';

cacheBreaker.breakCache(string, ['style.css', 'style2.css']);

// output
// <link href="/style.css?rel=23452341" /><link href="/style2.css?rel=23452341" />

```

**Append a timestamp in the filename**

```js
var string   = '<link href="/style.css" />';

cacheBreaker.breakCache(string, 'style.css', {position: 'filename'});

// output
// <link href="/style.56432352.css" />

```


**Overwrite an exiting timestamp**

Use this when you have rewrite rules in place.

```js
var string   = '<link href="/style.2452345.css" />';

cacheBreaker.breakCache(string, 'style.*.css', {position: 'overwrite'});

// output
// <link href="/style.56432352.css" />

```

##TODO

- [x] [Grunt Plugin](https://github.com/AkuraDavis/grunt-cache-breaker)
- [ ] Gulp Plugin
- [x] Accept file src for creating MD5 hash
- [x] Allow user-specified string in place of timestamp