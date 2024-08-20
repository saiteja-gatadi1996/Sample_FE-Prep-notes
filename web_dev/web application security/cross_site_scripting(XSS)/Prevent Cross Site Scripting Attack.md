
#### 1) Since XSS works by injecting malicious code into a website, 
  - the website owners should make sure that **all user inputs are validated** <ins>before they are **`stored`** into the database.</ins> 

#### 2) Sanitizing user input is another mitigation method 
- that essentially requires **all user data to be cleaned of potentially dangerous symbols** that are usually used in HTML markup and JavaScript code.
- **blacklist** HTML tags in user input.

----

- <strong>innerHTML</strong> is not a safe because if the user inputs valid HTML or script tag or an image tag, It'll render as actual HTML instead of as text.
- In order to get rid of this we can replace .innerHTML to <strong>.innerText</strong>
- If you really want to use innerHTML you need to make sure that nothing that goes to the innerHTML is sent you by the user unless you first escape that user input so essentially makes us that user input will render a <strong>string</strong> no matter what you do because you <strong>escape out all of the different HTML specific symbols</strong> so that it can no longer be rendered as HTML and must be rendered as text.
