---
title: Using postcss-cssnext
subtitle: How to configure postcss-cssnext options
---

@[toc]

When you have correctly [setup](/setup/) cssnext, you might want to tweak it a
little bit. You will find below all the available **options**.

## `browsers`

_(default:
[browserslist default](https://github.com/ai/browserslist#readme)
`> 1%, last 2 versions, Firefox ESR, Opera 12.1`)_

Allows you to specify your browser scope.
**This option enables or disables `features` according to
[caniuse](http://caniuse.com/) database.**
This is the exact same option that you might know from Autoprefixer.
Since cssnext includes Autoprefixer, the option is propagated.

See [Browserslist](https://github.com/ai/browserslist#queries) queries syntax to
adjust this option to your needs.

_Note: if you don't specify this option, Browserslist will automatically try to
find a `browserslist` config file or use its default value._

## `features`

_(default: all features depending on your `browsers` options)_

**You should probably use `browsers` option instead of this one.**

Object containing key of features to enable/disable.
_Features are enabled by default: no key means feature is enabled_.

```js
//eg: disable custom properties support
var output = cssnext(input, {
  features: {
    customProperties: false
  }
})
```

Each feature is based on PostCSS plugins & can get its own options.
To pass options to a feature, you can just pass an object to the feature:

```js
//eg: pass variables
var output = cssnext(input, {
  features: {
    customProperties: {
      variables: {
        mainColor: "red",
        altColor: "blue",
      }
    }
  }
})
```

**To know all available options, please check corresponding postcss plugin by
browsing the
[feature mapping](https://github.com/MoOx/postcss-cssnext/blob/master/src/features.js).**

_Note: order is important to get everything working correctly._
