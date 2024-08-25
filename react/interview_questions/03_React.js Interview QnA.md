### 1. What is JSX?

JSX stands for JavaScript XML. JSX allows us to write HTML in React. JSX makes it easier to write and add HTML in React.

### 2.

![image](https://user-images.githubusercontent.com/42731246/151151328-2a575f80-1e86-4f4a-b9ab-a6f9197e7344.png)

### 3. What is SPA?

An SPA (Single-page application) is a web app implementation that loads only a single web document, and then updates the body content of that single document via JavaScript APIs such as XMLHttpRequest and Fetch when different content is to be shown.

This therefore allows users to use websites without loading whole new pages from the server, which can result in performance gains and a more dynamic experience, with some tradeoff disadvantages such as SEO, more effort required to maintain state, implement navigation, and do meaningful performance monitoring.

### 4. Render prop

The term “render prop” refers to a technique for sharing code between React components using a prop whose value is a function.

```js
class Cat extends React.Component {
  render() {
    const mouse = this.props.mouse;
    return (
      <img
        src='/cat.jpg'
        style={{ position: 'absolute', left: mouse.x, top: mouse.y }}
      />
    );
  }
}

class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY,
    });
  }

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
        {/*
          Instead of providing a static representation of what <Mouse> renders,
          use the `render` prop to dynamically determine what to render.
        */}
        {this.props.render(this.state)}
      </div>
    );
  }
}

class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>Move the mouse around!</h1>
        <Mouse render={(mouse) => <Cat mouse={mouse} />} />
      </div>
    );
  }
}
```

### 5. ServiceWorker vs Web Worker?

#### ServiceWorker:

Rich offline experiences, periodic background syncs, push notifications. A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction.The reason this is such an exciting API is that it allows you to support offline experiences, giving developers complete control over the experience.

It's a JavaScript Worker, so it can't access the DOM directly. Instead, a service worker can communicate with the pages it controls by responding to messages sent via the postMessage interface, and those pages can manipulate the DOM if needed.

#### Web Worker:

Web Workers are a simple means for web content to run scripts in background threads. The worker thread can perform tasks without interfering with the user interface. In addition, they can perform I/O using XMLHttpRequest (although the responseXML and channel attributes are always null) or fetch (with no such restrictions). Once created, a worker can send messages to the JavaScript code that created it by posting messages to an event handler specified by that code (and vice versa).

# <--- SAMPLE CONTENT ENDS --->

