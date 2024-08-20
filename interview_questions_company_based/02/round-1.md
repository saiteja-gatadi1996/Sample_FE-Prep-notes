## Its a written test with the below mentioned sections

### 1) Two DSA problems

#### i) Find the repeated elements and output them as array


```javascript
function findRepeatedElements(arr) {
    let seen = new Set();
    let duplicates = new Set();

    for (let num of arr) {
        if (seen.has(num)) {
            duplicates.add(num);
        } else {
            seen.add(num);
        }
    }

    return [...duplicates];
}
```

Let's break this down:

1. We use two `Set` objects. `seen` keeps track of numbers we've come across, and `duplicates` keeps track of numbers we've seen more than once.

2. For each `num` in `arr`, we check if it's in the `seen` set. If it is, it's a duplicate, and we add it to the `duplicates` set. Otherwise, we add it to the `seen` set.

3. Finally, we return the `duplicates` set as an array.

This approach has the advantage of using just one loop, making it potentially more efficient, and the use of Sets ensures that the `duplicates` will only contain unique values.

----

#### ii) Return the largest difference of indices of given character if there is a duplicate else return -1

```javascript
function largestIndexDifference(s, char) {
    let minIndex = null;
    let maxIndex = null;

    for (let i = 0; i < s.length; i++) {
        if (s[i] === char) {
            if (minIndex === null) {
                minIndex = i;
            }
            maxIndex = i;
        }
    }

    if (minIndex !== null && maxIndex !== null && minIndex !== maxIndex) {
        return maxIndex - minIndex;
    }

    return -1;
}

// Example usage:
const str = "hello there";
const char = "e";
console.log(largestIndexDifference(str, char)); // This would return 9
```

---

#### 3) e.preventDefault to prevent event propagation

#### 4) Event-pointer: none


#### 5) Browser cache

1. **Browser Caching**: 
   - Leverage browser caching by setting appropriate HTTP headers. 
   - This allows browsers to store static assets like **`images`**, **`CSS`**, and **`JavaScript`** locally for a specified period. 
   - You can control the cache duration using the `Cache-Control` and `Expires` headers.
<br/>

2. **Content Versioning**: 
   - Append version numbers or timestamps to the filenames of your assets (e.g., `styles.css?v=1.2` or `script.js?timestamp=123456`). 
   - This ensures that when you make changes to these assets, the browser recognizes them as new files, thus avoiding caching issues.
<br/>

3. **Cache Busting**: 
   - Use cache-busting techniques like changing filenames or query parameters when deploying new versions of your website. 
   - This forces the browser to retrieve the latest version of the assets.
<br/>

4. **Conditional Requests**: 
   - Implement conditional requests using the `ETag` and `Last-Modified` headers. 
   - This allows the browser to check with the server whether the cached resource is still valid before requesting a new one.
<br/>

5. **Cache-Control Headers**: 
   - Use appropriate values for the `Cache-Control` header to define caching behavior. 
   - For example, you can set `public` or `private` cache, specify `max-age` for cache duration, and use `no-cache` or `no-store` directives when needed.
<br/>

6. **Gzip Compression**: 
   - Compress your assets before sending them to the browser. 
   - This reduces their size and speeds up loading times.
<br/>


7. **Cache Invalidation**: 
   - Plan for cache invalidation to ensure outdated or incorrect cached content is efficiently replaced. 
   - This can be managed through appropriate header settings and cache-busting techniques.
<br/>

8. **Service Workers**: 
   - Utilize service workers for modern web applications to manage caching more effectively, providing offline capabilities and background data syncing.
<br/>

9. **Monitoring and Analytics**: 
    - Use tools and analytics to monitor cache performance and user experience. 
    - This enables data-driven adjustments to your caching strategy for optimal results.
<br/>

10. **Security Considerations**: 
    - Be mindful of security implications when caching sensitive data. 
    - Use headers like **`Cache-Control`**: **`no-store`** to prevent caching of such information.
<br/>

11. **Local Storage**: 
    - Use localStorage for storing data that needs to persist across sessions. 
    - It's useful for storing user preferences or state data that doesn’t require secure handling.
<br/>

12. **Session Storage**: 
    - Use sessionStorage for storing data that should persist only for the duration of the page session. 
    - It's ideal for temporary data that should not be available after the session ends.
<br/>

13. **Cookies**: 
    - Use cookies for storing small amounts of data that need to be sent to the server with each request. 
    - Ensure to use cookies judiciously and secure them properly, especially for sensitive information.
<br/>

14. **IndexedDB**: 
    - Use IndexedDB for storing larger amounts of structured data. 
    - It's a low-level API for client-side storage, allowing you to create, read, and manage large datasets.

------------


#### 6) Caption to image in html
- To add a caption to an image in HTML, you can use the `<figure>` and `<figcaption>` elements. Here's an example:

```html
<figure>
  <img src="image.jpg" alt="Description of the image">
  <figcaption>This is a beautiful sunset over the mountains.</figcaption>
</figure>
```

Replace `"image.jpg"` with the actual path to your image and modify the caption text accordingly. The `<figcaption>` element provides a semantic way to associate a caption with an image.
