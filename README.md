# reCAPTCHA-v3

![npm](https://img.shields.io/npm/v/recaptcha-v3.svg) 
![npm type definitions](https://img.shields.io/npm/types/recaptcha-v3.svg)


A simple and easy to use reCAPTCHA (v3 only) library for the browser.

## Install
With NPM:
```bash
$ npm install recaptcha-v3
```

With Yarn:
```bash
$ yarn add recaptcha-v3
```

## Prerequisites
To use this package you only need a valid site key for your domain, which you can easily get [here](https://www.google.com/recaptcha).

## Usage

With promises:
```javascript
import { load } from 'recaptcha-v3'

load('<site key>').then((recaptcha) => {
  recaptcha.execute('<action>').then((token) => {
      console.log(token) // Will print the token
    })
})
```

With async/await:
```javascript
import { load } from 'recaptcha-v3'

async function asyncFunction() {
  const recaptcha = await load('<site key>')
  const token = await recaptcha.execute('<action>')

  console.log(token) // Will also print the token
}
```

## Loader options
The loader takes care of loading the reCAPTCHA script from Google.
Therefore the loader offers optional options for additional configuration:

|Name|Description|Type|Default value
|----|-----------|----|-------------
|**useRecaptchaNet**|Due to limitations in certain countries it's required to use `recaptcha.net` instead of `google.com`.|*boolean*|`false`
|**autoHideBadge**|Will automatically hide the reCAPTCHA badge. Warning: The usage is only allowed if you follow the offical guide for hiding the badge from Google ([see here](https://developers.google.com/recaptcha/docs/faq#id-like-to-hide-the-recaptcha-v3-badge-what-is-allowed))|*boolean*|`false`

### Usage
To use the options just pass an additional object to the `load(...)` method.
For example:
```javascript
import { load } from 'recaptcha-v3'

load('<site key>', {
  useRecaptchaNet: true,
  autoHideBadge: true
}).then((recaptcha) => {
  
})
```
