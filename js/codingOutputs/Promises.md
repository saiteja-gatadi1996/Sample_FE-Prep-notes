#### Promise has three states

- pending
- fulfilled
- rejected

```js
let p = new Promise((resolve, reject) => {
  let a = 1 + 1
  if (a === 2) {
    resolve("Success")
  } else {
    reject("Failed")
  }
})

p.then((res) => {
  console.log("This is in the then block" + res)
}).catch((error) => {
  console.log("This is in the catch block" + error)
})
```

---

### Converting CallBack code into Promises

#### Callback Code:

```js
function watchTutorailCallback(callback, errorCallback) {
  let userLeft = false
  let userWatchingCatMeme = false

  if (userLeft) {
    errorCallback({
      name: "User Left",
      message: ":(",
    })
  } else if (userWatchingCatMeme) {
    errorCallback({
      name: "User Watching Cat Meme",
      message: "WebDevSimplified < Cat",
    })
  } else {
    callback("Thumbsup and subscribe")
  }
}

watchTutorailCallback(
  (message) => {
    console.log(message)
  },
  (error) => {
    console.log(error.name + "" + error.message)
  }
)
```

---

#### Promises Code:

```js
function watchTutorailPromise() {
  let userLeft = false
  let userWatchingCatMeme = false
  return new Promise((resolve, reject) => {
    if (userLeft) {
      reject({
        name: "User Left",
        message: ":(",
      })
    } else if (userWatchingCatMeme) {
      reject({
        name: "User Watching Cat Meme",
        message: "WebDevSimplified < Cat",
      })
    } else {
      resolve("Thumbsup and subscribe")
    }
  })
}

watchTutorialPromise()
  .then((message) => {
    console.log(message)
  })
  .catch((error) => {
    console.log(error.name + " " + error.message)
  })
```

---

### Example Code of Promises

```js
const promise1 = new Promise((resolve, reject) => {
  resolve("Video1")
})

const promise2 = new Promise((resolve, reject) => {
  resolve("Video2")
})

const promise3 = new Promise((resolve, reject) => {
  resolve("Video3")
})

Promise.all([promise1, promise2, promise3]).then((messages) => {
  console.log(messages) // ["Video1, Video2, Video3"]
})
```

# <--- SAMPLE CONTENT ENDS --->
