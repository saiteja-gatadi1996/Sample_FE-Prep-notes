## Observer Design Pattern

- The Observer design pattern is a software design pattern in which an <ins>***object maintains a list of its dependents, called observers***</ins>, and notifies them of any state changes, usually by calling one of their methods. 
- It's a <ins>***foundational pattern for event handling systems***</ins>, especially in user interface and web development contexts.

### Traditional JavaScript Version (pre-ES6)

```js
function Observable() {
  this.observers = [];
}

Observable.prototype = {
  subscribe: function (observer) {
    this.observers.push(observer);
  },
  unsubscribe: function (observer) {
    this.observers = this.observers.filter(
      (subscriber) => subscriber !== observer
    );
  },
  notify: function (data) {
    this.observers.forEach((observer) => observer(data));
  },
};

// Example usage:
var observable = new Observable();

function observer1(data) {
  console.log('Observer 1 received data:', data);
}

function observer2(data) {
  console.log('Observer 2 received data:', data);
}

observable.subscribe(observer1);
observable.subscribe(observer2);
observable.notify('Hello World!'); // This will log the string via both observers, if I comment this then we won't see the console.log information printed
```
----

### ES6 Version

- With the introduction of ES6 (ECMAScript 2015), JavaScript got classes 
```js
class Observable {
    constructor() {
        this.observers = [];
    }

    subscribe(observer) {
        this.observers.push(observer);
    }

    unsubscribe(observer) {
        this.observers = this.observers.filter(subscriber => subscriber !== observer);
    }

    notify(data) {
        this.observers.forEach(observer => observer(data));
    }
}

// Example usage remains the same:
const observable = new Observable();

const observer1 = data => {
    console.log('Observer 1 received data:', data);
};

const observer2 = data => {
    console.log('Observer 2 received data:', data);
};

observable.subscribe(observer1);
observable.subscribe(observer2);
observable.notify('Hello World!');  // This will log the string via both observers
```

### Real-time Example: Chat Room

- In this ES6 version, we will create a ChatRoom class as an observable that can broadcast messages to all subscribed participants. 
- Participants will subscribe to the chat room to receive messages and can unsubscribe if they leave the chat.



```js
class ChatRoom {
  constructor() {
    this.participants = [];
  }

  join(participant) {
    this.participants.push(participant);
    console.log(`${participant.name} joined the chat.`);
  }

  leave(participant) {
    this.participants = this.participants.filter((p) => p !== participant);
    console.log(`${participant.name} left the chat.`);
  }

  sendMessage(message, sender) {
    this.participants.forEach((participant) => {
      if (participant !== sender) {
        // Do not send the message to the sender
        participant.receive(message, sender);
      }
    });
  }
}

class Participant {
  constructor(name) {
    this.name = name;
  }

  receive(message, sender) {
    console.log(
      `${this.name} received a message from ${sender.name}: '${message}'`
    );
  }
}

// Example usage:
const chatRoom = new ChatRoom();

const alice = new Participant('Alice');
const bob = new Participant('Bob');
const charlie = new Participant('Charlie');

chatRoom.join(alice);
chatRoom.join(bob);
chatRoom.join(charlie);

alice.sendMessage = chatRoom.sendMessage.bind(
  chatRoom,
  'Hello everyone!',
  alice
);
bob.sendMessage = chatRoom.sendMessage.bind(chatRoom, 'Hi Alice!', bob);

alice.sendMessage();
bob.sendMessage();

chatRoom.leave(charlie);

//Output:

// Alice joined the chat.
// Bob joined the chat.
// Charlie joined the chat.
// Bob received a message from Alice: 'Hello everyone!'
// Charlie received a message from Alice: 'Hello everyone!'
// Alice received a message from Bob: 'Hi Alice!'
// Charlie received a message from Bob: 'Hi Alice!'
// Charlie left the chat
```