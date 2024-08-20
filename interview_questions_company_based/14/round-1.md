## HTML Coding

#### 1. What are semantic tags? 
  - They **give meaning to the web** content part of the markup, 
  - which **helps** both `browsers` and `developers` **understand** the structure and significance of the content, 
  - enhancing `accessibility` and search engine optimization `(SEO)`. 
  - Also make web pages **more `readable` and `maintainable`**.
  - `<header>`, `<footer>`, `<article>`, `<section>` are a few examples.

#### 2. Write down sample HTML for a blog page with sidebar and list of blogs

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Blog</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header>
      <h1>My Blog</h1>
    </header>
    <div class="container">
      <aside id="sidebar" class="sidebar">
        <nav>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </aside>
      <main>
        <article>
          <h2>Blog Post Title 1</h2>
          <p>Posted on January 1, 2024. Written by Author.</p>
          <p>This is the first paragraph of the blog post content.</p>
        </article>
        <article>
          <h2>Blog Post Title 2</h2>
          <p>Posted on January 2, 2024. Written by Author.</p>
          <p>This is the first paragraph of the second blog post content.</p>
        </article>
      </main>
    </div>
    <footer>
      <p>Copyright © 2024 My Blog. All rights reserved.</p>
      <p>Follow us on <a href="#">Social Media</a></p>
    </footer>
  </body>
</html>
```

```css
/* styles.css */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

header {
    background-color: #333;
    color: white;
    padding: 1rem;
    text-align: center;
}

.container {
    display: flex;
    flex: 1;
}

.sidebar {
    background-color: #444;
    color: white;
    width: 200px;
    padding: 20px;
    height: 100vh; /* Full height */
    overflow: auto; /* Enables scrolling if content is long */
}

.sidebar nav ul {
    list-style: none;
    padding: 0;
}

.sidebar nav ul li a {
    color: white;
    padding: 10px;
    display: block;
    text-decoration: none;
}

.sidebar nav ul li a:hover {
    background-color: #555;
}

main {
    flex: 1;
    padding: 20px;
}

footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px 0;
}
```

  ![alt text](/interview_questions_company_based/14/imagesUsed/sidebar_blog_posts.png)


----

## React Machine coding

- Take any API url and show the data on the client side
- How can we achieve the pagination, can you write down the logic
- How can we achieve infinite scrolling, can you write down the logic

**Verdict**: Selected
