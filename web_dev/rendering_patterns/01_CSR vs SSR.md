## Client Side Rendering (CSR)

### Fetching Data:
- **_<ins>Data is fetched asynchronously</ins>_** from the client (browser) **_<ins>after the initial page load</ins>_**. 
- The fetch call to the API is made from the browser. 

### Rendering:
- <ins>Initially, the page loads **`without`** the data</ins>. 
- Once the data is fetched and the state is updated, 
- **React `re-renders`** the component to display the fetched data.

### Interactivity and Performance: 
- The initial load is quick because the **_<ins>browser first loads the minimal HTML structure without the data</ins>_**. 
- However, the data appears on the screen only after the API call completes, which **_<u>can introduce a noticeable delay before users see the complete content</u>_**.

### SEO Implications: 
- Since the content is loaded asynchronously after the initial page load, search engines that do not execute JavaScript may not index the dynamically loaded content properly. 
- This **_can negatively affect the page's SEO_**.

```js
//api fetch example
// React component that fetches data from an API
import { useEffect, useState } from 'react';
export default function MyPosts() {
  const [posts, setPosts] = useState;
  useEffect(() => {
    fetch('https://api.jsonbin.io/v3/b/6342b4f62b3499323bd881c1')
      .then((res) => res.json())
      .then((data) => {
        setPosts(data.record.posts);
      });
  }, []);
  return (
    <>
      My posts
      <ul>
        {posts.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </>
  );
}
```
## Server Side Rendering (SSR)**

**Fetching Data:** The `getServerSideProps` **_<u>function runs on the server during the request-response cycle</u>_**. It **<u>fetches data before the page is rendered**</u>. <br/>
**Rendering**: The **_<u>server renders the page with the fetched data</u>_**, and the **<u>complete HTML is sent to the browser</u>**. The user sees the fully rendered page as soon as it loads.<br/>
**Performance and SEO:** The initial load might be slightly slower compared to CSR because the server has to fetch the data and render the page before sending it to the client. However, the user perceives it as faster since the data is visible immediately without additional loading times.<br/>

##### Additionally, <u>SSR is beneficial for SEO as search engines index the fully rendered page content</u>.

**Interactivity:** JavaScript can still be used to enhance the page and add client-side interactivity after the initial server-rendered page load.

```js
// the data is fetched `on the server`, and the page is rendered with the data before being sent to the client
export default function MyPosts(props) {
  return (
    <>
      My posts
      <ul>
        {props.posts.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </>
  );
}

export async function getServerSideProps(context) {
  const promise = await fetch(
    'https://api.jsonbin.io/v3/b/6342b4f62b3499323bd881c1'
  );
  const data = await promise.json();

  return {
    props: { posts: data.record.posts },
  };
}
```

### Comparison Summary:

**CSR**: **_<u>Good for dynamic applications where content changes frequently and user interactivity is high</u>_**. Initial page loads are fast, but complete content visibility depends on the API call's latency. It **might pose challenges for SEO.** <br/>
**SSR**: **_<u>Ideal for content-heavy applications where SEO is crucial</u>_**. The initial load delivers fully rendered content, improving perceived performance and ensuring content is SEO-friendly. However, it can put more load on the server, especially for high-traffic sites.
