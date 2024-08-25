
### Content Security Policy

- Most powerful security feature that browser has implemented in the recent years in mitigating Cross-Site Scripting vulnerabilities.
- With CSP it is possible to prevent various types of attacks, **_such as Cross-Site Scripting (XSS) and data injection attacks_**, by allowing web developers to declare which sources of content are considered trustworthy.
- The implementation of the CSP <strong>renders the use of X-Frame options header obsolete.</strong>
- It is used to <u>**_mitigate the risks associated with the execution of malicious scripts_**</u> on a web page.
- **By defining a policy**, developers can instruct the <u>**_browser to only load resources (like scripts, styles, images, etc.) from specified origins_**.</u>

**Implementation:**

- Developers <u>**_include a Content-Security-Policy header in the HTTP response from the server_**</u>, specifying the allowed sources for various types of content.

#### Some of the issues that can be prevented by setting a CSP policy are:

- Inline JS code specified with script tags and any DOM events which trigger JS execution such as onclick()
- Inline CSS code specified via style tags

### Advantages of using CSP

- With CSP, we can allow many configurations for trusted content. As such, the initial setup can grow up to set of complex directives.

- one of the CSP directive is <strong>connect-src</strong>. It is used to control (which remote servers the browser is allowed to connect to via XMLHttpRequest(XHR) or a tag elements)

- Other script interfaces that are covered by this directive are

```js
Fetch, EventSource, WebSocket, Navigator.sendBeacon();
```

- Acceptable values that we can set for this directive:
- <strong>none</strong>: not allowing remote calls such as XHR at all.
- <strong>self</strong>: Only allow remote calls to our own domain (an exact domain/hostname whereas sub domains aren't allowed)

##### Following is an example of a content security policy being set. It allows the browser to make XHR requests to the website's own domain and to Google API's domain.

```js
Content-Security-Policy: connect-src 'self' https://apis.google.com;
```

- another directive to the control the allowlist for javascript sources is called <strong>script-src.</strong>
- This directive helps to mitigate Cross-Site-Scripting(XSS) attacks by informing the browser <strong>which sources of content to trust when evaluating and executing Javascript source code</strong>
- The script-src control supports the <strong>none</strong> and <strong>self</strong> keywords as values and includes the following options

- <strong>'unsafe-inline'</strong> allow any inline Javascript source code such as script and DOM events triggering onClick() or javascript URIs. It also affects CSS for inline tags

- <strong>'unsafe-eval'</strong> allow execution of code using eval()

- Follwing is the policy for allowing javascript to be executed only from our own domain and from Google (while allowing inline javascript code as well)

```js
<meta
  http-equiv='Content-Security-Policy'
  content="default-src 'self' 'unsafe-eval'; style-src 'self' 'unsafe-inline'; script-src 'self' https://maps.googleapis.com 'unsafe-inline' 'unsafe-eval';"
/>
```

```js
Note that unsafe-inline directive refers to a website's own javascript sources.
```

<strong>default-src</strong>: where a directive doesn't have a value, it defaults to an open, non-restricting configuration.

- It is safer to set a default for all the unconfigured options, which is where the default-src comes in.

<strong>script-src</strong> a directive to set which script sources we allow to load or execute JS from.

- If it's set to a value of 'self' <strong>then it only allows sources from our own-domain. Also it will not allow inline js tags such as script </strong>
- To enable those, add <strong>unsafe-inline</strong> too.

- It should also be noted that when implementing CSP, <strong>the CSP configuration needs to meet the implementation</strong> of your web application architecture.

- If you deny inline script blocks then your R&D team should be aware of this and comes well prepared. Otherwise it might break features and functionality across code that depends on inline javascript code blocks.

## <img src="https://miro.medium.com/v2/format:webp/0*BKXMd9FkApZwM7JQ.jpg">

#### Helmet Implementation

# <--- SAMPLE CONTENT ENDS --->
