
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

- We define an allowlist in which javascript code and CSS resources are only allowed to load from the current origin, which is the exact hostname or domain (no sub-domains will be allowed)

```js
const helmet = require('helmet');

app.use(
  helmet.contentSecurityPolicy({
    directives: { scriptSrc: ["'self'"], styleSrc: ["'self'"] },
  })
);
```

<strong>Note:</strong> If no default policy is specified, <strong>then all other types of content policies are open and allowed,</strong> and some content policies which simply don't have a default must be specified to be overridden.

---

##### Let's construct the following content policy for our web application

- By default, allow resources to load only from our own domain origin or from our Amazon CDN.

```js
The defaultSrc refers to all script type sources, such as CSS, iframes, fonts etc;
```

- Javascript resources are <strong>restricted to our own domain and Google's hosted libraries domain </strong> so that we can load JS from Google.

- Because our web applicatiion doesn't need any kind of iframes embedding, we will disable such objects <strong>refers to objectSrc and childSrc</strong>

- Forms should <strong>only be submitted to our own domain origin</strong>

```js
cosnt helmet = require('helmet')

app.use(helmet.contentSecurityPolicy({
  directives:{
    defaultSrc: ["'self'", "https://cdn.amazon.com"],
    scriptSrc: ["'self'", "https://ajax.googleapis.com"],
    childSrc: ["'none'"],
    objectSrc: ["'none'"],
    formAction: ["'none'"],
  }
}))

```

#### Gradual CSP Implementation:

- Your Content Security Policy will grow and change as your web application grows too.

- With the many varies directives, it could be challenging to introduce a policy all at once.

- So instead of touch-n-go enforcement, strive for an incremental approach.

The CSP header has a built-in directive that helps in understanding how your web application makes use of the content policy. This directive is used to track and report any actions performed by the browser that violate the content security policy.

```js
// Do not change anything from below

Content-Security-Policy: default-src 'self'; report-uri https://mydomain.com/report
```

Once the above is added, the browser will send a POST request to the URI provided with a JSON format in the body for anything that violates the CSP.

```js
// With helmet CSP middleware

const helmet = require('helmet');

app.use(
  helmet.csp({
    directives: {
      defaultSrc: ['self'],
      reportUri: 'https://mydomain.com/report',
    },
  })
);
```

- Another important configuration for Helmet when we are still evaluating a CSP <strong>to instruct the browser to only report on content policy violation and not block them.</strong>

```js
// just add reportOnly: true

const helmet = requrie('helmet');

app.use(
  helmet.csp({
    directives: {
      defaultSrc: ['self'],
      reportUri: 'https://mydomain.com/report',
    },
    reportOnly: true,
  })
);
```