# htmlparser2

[![NPM version](http://img.shields.io/npm/v/htmlparser2.svg?style=flat)](https://npmjs.org/package/htmlparser2)
[![Downloads](https://img.shields.io/npm/dm/htmlparser2.svg?style=flat)](https://npmjs.org/package/htmlparser2)
[![Build Status](http://img.shields.io/travis/fb55/htmlparser2/master.svg?style=flat)](http://travis-ci.org/fb55/htmlparser2)
[![Coverage](http://img.shields.io/coveralls/fb55/htmlparser2.svg?style=flat)](https://coveralls.io/r/fb55/htmlparser2)

A forgiving HTML/XML/RSS parser. The parser can handle streams and provides a callback interface.

Forked from https://github.com/fb55/htmlparser2

Add an option for Parser to distinguish an empty attribute and an attribute that have empty string value

```javascript
var htmlparser = require("./lib/index");
var htmlString = '<input name="empty" value="" hidden/>'

var json1 = htmlparser.parseDOM(htmlString, {})
console.log('json1 = ', json1)
/*
 *  json1 =  [{ 
 *      type: 'tag',
 *      name: 'input',
 *      attribs: { name: 'empty', value: '', hidden: '' },
 *      children: [],
 *      next: null,
 *      prev: null,
 *      parent: null
 *  }]
 */
var json2 = htmlparser.parseDOM(htmlString, {
	distinguishEmptyAttribute: true
})
console.log('json1 = ', json2)
/*
*  json2 =  [{ 
*      type: 'tag',
*      name: 'input',
*      attribs: { name: 'empty', value: '', hidden: null },
*      children: [],
*      next: null,
*      prev: null,
*      parent: null
*  }]
*/
```
