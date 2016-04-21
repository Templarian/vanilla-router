# vanilla-router

[![NPM](https://nodei.co/npm/vanilla-router.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/vanilla-router/)

[![NPM](https://nodei.co/npm-dl/vanilla-router.png?months=1&height=3)](https://nodei.co/npm/vanilla-router/)

## Description

Simplest One Page Application Router for those who want to use it on Vanilla JS


## Installation

```bashp
npm install vanilla-router --save
```

## Usage 

```js
var router = new Router({
    mode: 'history',
    page404: function (path) {
        console.log('"/' + path + '" Page not found');
    }
});

router.add('', function () {
    console.log('Home page');
});

router.add('hello/(:any)', function (name) {
    console.log('Hello, ' + name);
});

router.add('about', function () {
    console.log('About Page');
});

router.addUriListener();

router.navigateTo('hello/World');
```

## Options

#### mode `string`

`hash` - is for hashbang routes based on `window.location.hash`

`history` - is for clean url routes based on HTML5 functionality. It is also provide back-compatibility for old browser.

#### root `string`

#### page404 `function`

#### routes `Array`   

## Methods
Every public methods of Router return the instance of Router, so they can be chained.

#### add(path, handler)
`path` - string | RegExp

`handler` - callback if the URL will match the path

string path can contain:
 - parenthesis (`( )`) - value between them is sent to callback function  
 - wildcards (`:any`, `:num`, `:word`) it doesn't pass the value to callback function
 - named placeholder (`{variableName}`) it pass the value to the callback function

```js
router.add('hello/world', function(){ });
router.add('hello/(:word)', function(name){ });
router.add('hello/{name}', function(name){ });
router.add(/^hello\/(\w+)/i, function(name){ });
```

#### remove(path)

#### navigateTo(path, [state])

#### check()

#### back()

#### forward()

#### go(step)

#### addUriListener()

#### removeUriListener()

#### reset()

Reset all setting and state of Router

## Licence
Released under the MIT license
Copyright (c) 2016 Grigore Odajiu - 
