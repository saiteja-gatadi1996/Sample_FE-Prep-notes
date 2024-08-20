### Create your own cookie

```js
1. it should support get and set.
2. support max-age which means the cookie should be deleted after certain time(in seconds).
```

```js
//Examples:
document.myCookie = 'bfe=dev; max-age=1';
// "bfe=dev; max-age=1"

document.myCookie;
// "bfe=dev"

// after 1 second
document.myCookie;
// ""
```

```js
(function () {
  function parseCookie(cookieStr) {
    let cookies = {};
    let parts = cookieStr.split(';');
    parts.forEach((part) => {
      let [key, value] = part.split('=');
      cookies[key] = decodeURIComponent(value);
    });
    return cookies;
  }

  Object.defineProperty(document, 'myCookie', {
    get: function () {
      return parseCookie(document.cookie);
    },
    set: function (value) {
      document.cookie = value;
    },
  });
})();

// attribute used to specify the lifetime of a cookie is max-age, and this is the exact terminology you must use
document.myCookie = 'saiteja=gatadi; max-age=5'; //5 seconds
console.log(document.myCookie);

// After 8 seconds, the cookie should be expired and no longer visible
setTimeout(() => {
  console.log('After Expiration', document.myCookie);
}, 8000);
```
