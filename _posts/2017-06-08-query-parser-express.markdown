---
layout: post
title:  "Express extended query parser"
date:   2017-06-08 20:06:59 +0000
author: anupvarghese
comments: true
---

Express has simple and extended query parsers. `simple` is based on Node's [queryparser](https://www.npmjs.com/package/querystring) and `extended` is based on [qs](https://www.npmjs.com/package/qs)

However, if we need to override the default options of `qs`, we could do as below,

```javascript
const express = require('express');
const qs = require('qs');

const app = express();
app.set('query parser', (str) => qs.parse(str, { arrayLimit: 100 }));
...
```

This will use `qs` as the default query parser & override its default `arrayLimit` size from 20 to 100.
