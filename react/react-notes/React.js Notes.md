### 1. What is React?

##### Ans:

i) React is a Javascript library for building User Interfaces.

ii) Developed by Facebook in 2011.

iii) When it comes to react, it's all about components.

- So React gives us a way to build websites and front end applications and uses in an organized way with reusable components. So components can include the output, which is the basically the HTML in react to use something called
  JSX. And you can think of components as independent chunks of user interfaces. Components can be as small as one html element.

iv) In reality, we probably will avoid the one component, since it's somewhat defeats the purpose

v) You see, the benefit of the component is that you can build a bunch of independent, isolated and most importantly reusable user interfaces. You can build independent pieces of user interfaces, meaning changing logic or layout in one command will not break your whole up.

vi) So if you ever need to make some changes, you simply locate the component, apply the changes and all the instances will be automatically updated.

vii) You say behind the scenes react is using something called virtual dom, where only the component that needs to be updated is effective. And what's really cool, it's done without rendering the whole which in turn, of course, increases the speed of your final product and as a result, the user experience as well.

viii) The only difference between React and Angular is that react at its core is only responsible for creating
user interfaces. It doesn't have things like a router or an HTTP client built in. However, we have popular packages like React Router Dom.

#### So why learn react? Why not just build all your front ends with just HTML, CSS and vanilla JavaScript?

- Well, things used to be really messy with no consistency you'd have everything would be separate (HTML, JS). React and frameworks in general have made it much easire to organize our user interfaces or our frontends.

- Another main reason to use react is - Reusable components
- Another main reason to use react is - React performs very well. It uses the virtual dom or virtual document object model. We have separate components in the UI that have something called state, and when a component state
  changes, react basically compares the existing Dom State with what the new Dom should look like. And then it finds the least expensive and most efficient way to update the Dom. So it's very fast and performant.
- Another main reason to use react is - React is Declarative

![image](https://user-images.githubusercontent.com/42731246/165605144-427fa67d-483a-4d73-a60a-cb313182a99b.png)

### 2. Webpack

![image](https://user-images.githubusercontent.com/42731246/159537443-eb97b9ed-18d0-4dcb-81e1-85d9e99e0469.png)

Essentially, Webpack works as a module bundler, the main features of Webpack would be bundling our resources, watching for changes and running Babel transpiler.

### 3. Babel

Babel is a JavaScript transpiler that converts the newest JavaScript into the good old JavaScript so we can use all the newest features of the JavaScript language. So think things like an spread operator, destructuring and all the other goodies that come with ES6. And behind the scenes babel will turn into ES5, which in turn will make sure that our app runs smoothly in the older browsers as well.

### 4. First Component

###### This is mentioned in the index.html file in public folder

```js
<div id="root"></div>
```

```js
import React from "react"
import ReactDom from "react-dom"

function Greeting() {
  return <h4> this is SaiTeja and this is my first component </h4>
}

ReactDom.render(<Greeting />, document.getElementById("root"))
```

### 5. JSX Rules

![image](https://user-images.githubusercontent.com/42731246/159543496-b224585f-2690-48cd-b585-129012574a5a.png)

JSX expressions must have one parent element and I were to save this below code it would break.

![image](https://user-images.githubusercontent.com/42731246/166100033-728cb6ae-082b-43e5-83e9-6abd0becfc6f.png)

![image](https://user-images.githubusercontent.com/42731246/166100051-da75d2e3-87ee-442d-855a-b836e7ac5637.png)

What it means is that what we return that has to be one parent element like below:
![image](https://user-images.githubusercontent.com/42731246/166100077-a76b93c4-1dba-4b15-b672-93175cc9a392.png)

### 6. Children Prop

i) Component Book is now written in below format and we are inserting paragraph (p tag) at line 26 which is in between the Book component

```js
<Book></Book>
```

![image](https://user-images.githubusercontent.com/42731246/159547988-b3f1c590-2480-4318-b104-907bd7811e80.png)

To access the p tag, the Book Component should have a children prop like below

![image](https://user-images.githubusercontent.com/42731246/159548627-8ee13592-f041-4a5a-9dba-191b317ab21f.png)

![image](https://user-images.githubusercontent.com/42731246/159548776-af11b923-3d8e-43c7-a8c5-43c186be9044.png)

### 7. Event Basics

i) We can declare a clickHandler function (line 43) and use this function as a reference at (line 58)

ii) If we don't want to declare a function like clickHandler then we can directly write the logic by passing a callback function syntax like we did on (line 56)

Both i) and ii) works same

iii) In case if we are having any parameter in our function like ex: author is the parameter in the complexExample function (line 48) then in order to use this in onClick event we need to write this like we did on (line 61) which is passing a callback function (this runs during component loaded) and the reference function which actually works when we perform onClick.

![image](https://user-images.githubusercontent.com/42731246/159846195-a142a82e-a650-42c5-a227-f1dcc3a63ca6.png)

### 8. Import and Exports

i) Are the modules as part of ES6 (which are not react specific)
ii) Allows us to split up our app in small chunks which makes easier to manage our app in general

#### Default Exports:

```js
export default Greeting
```

To import default export component, the syntax is like below (We can write any name apart from Greeting)

```js
import Greeting from "./Greeting"
```

Ex:

```js
import Wishing from "./Greeting"
```

#### Named Exports:

```js
export const Greeting
```

#### Named Exports must match the function naming which is Greeting:

```js
import { Greeting } from "./Greeting"
```

#### Another Few examples of Default and Named Exports

##### Here we declared as Named Export on line 1

![image](https://user-images.githubusercontent.com/42731246/159847866-99fe703b-b957-40e9-802f-37461512ad32.png)

##### While importing this Named Export we should match the name with books

In our case we wrote as data in (line 7) and that is why browser failed to compile

![image](https://user-images.githubusercontent.com/42731246/159847926-f996626c-f74b-4654-abab-b30074c6171d.png)

##### For default export in this case, we need to write as export default books

##### import this as import books or any name from './books'

i) We only need to have one default export in a file which there can be any number of Named Exports in a single file

### 9. Advanced React

![image](https://user-images.githubusercontent.com/42731246/159848930-582c1a0e-6add-4f94-9ee6-d5cdd41c3c8c.png)

i) Basic Example of state change

If in our handleClick function we change the value of title, we observed that the Random Title naming is not changed to Hello People.

Now, the problem is that we are not rendering the component. So we change the value and we're not rendering the component. That's the reason why we cannot see any changes.

Now, the second thing is that we have no way to preserve this value in between the renders as well. So essentially, we would want two things.

We would want to keep the value between the renders, but also we would want to trigger that and this is where the useState comes into play, where it will allow us to do just that.

![image](https://user-images.githubusercontent.com/42731246/159856053-1230418f-4b79-4611-bf4d-2b5f3fcaa7a0.png)

### 10. Advanced React- useState

useState is a function

![image](https://user-images.githubusercontent.com/42731246/160236968-2f541e12-ad65-479d-981c-3a7ca8dc3f66.png)

on line 5, if we invoke this function, we would see that returns an array, and the first argument is actually a state value (at the moment it is undefined because we haven't passed a default value like a empty string or boolean or an empty array or empty object for example), and the second arg is the function which actually controls the value
![image](https://user-images.githubusercontent.com/42731246/160237205-c16aea74-4576-458d-9491-5de33516aa2f.png)

### Good example of useState

```js
import React, { useState } from "react"

const UseStateBasics = () => {
  const [text, setText] = useState("random title")
  const handleClick = () => {
    if (text === "random title") {
      setText("hello world")
    } else {
      setText("random title")
    }
  }

  return (
    <React.Fragment>
      <h1>{text}</h1>
      <button type="button" className="btn" onClick={handleClick}>
        change title
      </button>
    </React.Fragment>
  )
}

export default UseStateBasics
```

### General use of Hooks

i) a Hook should start with use

ii) a Component that use Hooks should start with Uppercase, otherwise it throws an error saying like

##### your component is neither a react function component or a custom React Hook function

iii) the hooks you are defining should be written inside the function body,

##### below is the wrong way of defining hooks

![image](https://user-images.githubusercontent.com/42731246/160237786-c83647dd-f269-4cbe-8589-5128052bef41.png)

![image](https://user-images.githubusercontent.com/42731246/160237612-1b785852-3c7a-4a2d-aa2a-d2edbd890905.png)

### useState Array Example

##### Data is an array and having objects and this is a named export.

![image](https://user-images.githubusercontent.com/42731246/160237991-01c234a5-ca50-4901-8aff-497a19588a43.png)

##### utilizing the data and holding the data value in people useState hook, now the people value holds the entire data (which was defined inside data.js),

##### we are iterating the people array using map (Higher Order Function) and destructuring the id,name from the person and returning the name

![image](https://user-images.githubusercontent.com/42731246/160237963-e1a4a9d0-c1e8-41a2-8b7a-2958bc7587e0.png)

##### a single button was created to clear items, as we are not referencing to a function and directly using the function (we need to pass a callback/arrow function to avoid running in a infinite loop, in our case data is an array, so to clear the data we need to pass the empty array)

![image](https://user-images.githubusercontent.com/42731246/160238220-7c0f7f89-d5ef-4d81-9871-575fb13036e2.png)

##### To only remove a singe person, we need to follow two approaches

i) Filter and show out (all the users) whose id doesn't match with the remove user id. (Read it twice).

This happens because we are using setPeople(newPeople) which holds latest value (that is filtered users).

In shorter terms: Our list will be filtered and shown without that removed user

ii) As we are passing a parameter inside the removeItem function, to use this in onClick we need to write like a (callback/arrow function) syntactical.

![image](https://user-images.githubusercontent.com/42731246/160238310-ca71ea3d-e070-4710-ad3b-320102db8286.png)

#### Another good way of re-writing function (functional approach)

![image](https://user-images.githubusercontent.com/42731246/160239773-f6f0951b-6929-4cc7-8918-5df48273055d.png)

### useState Object Example

Clearly observe that our person value is now object, so to change this we also need to pass an array inside setPerson function,

###### the reason we use spread operator was, we only want to disturb the message property and want to keep out the remaining properties as it is.

![image](https://user-images.githubusercontent.com/42731246/160238826-25960005-182f-4c9e-b0a5-a126f2df9e36.png)

###### we can also define in a separate hooks for name, age, message like we did below, and the good thing is now we can directy write setMessage and change the text message to whatever we need

![image](https://user-images.githubusercontent.com/42731246/160238930-6097f159-f85d-4c27-98fa-468f426c50bc.png)

#### Simple Counter Example using useState

![image](https://user-images.githubusercontent.com/42731246/160239237-2a4b4f48-fd38-4505-a290-3a5a5516cb55.png)

Added a new button which should increase the counter value after 2 seconds

##### IF we write like below (as we are holding the prevState value) this exactly holds our correct value (for Ex: If we clicked 10 times, it should update the value to 10). This is happening due to asynchronous way of handling the value due to setTimeout

##### If we click the button 10 times, it will only update once (if we use commented way of setValue(value+1) code)

![image](https://user-images.githubusercontent.com/42731246/160239864-03b39355-e7cf-4854-a952-432e9e71ac7d.png)

### 11. Advanced React- useEffect

###### by default useEffect will runs after every re-render (Each and everytime we re-run the component, useEffect will run)

Every time we click notice we're updating the value , we're calling the useEffect after every render.
And of course, the functionality that is within the useEffect also runs because now I have document.title (This happens because useState helps us to re-render the component and preserves the value between the re-renders, In a similar way by default useEffect will run after every re-render (so inside useEffect we are writing the document.title to change as per the value change))

![image](https://user-images.githubusercontent.com/42731246/160252796-b8546be5-9900-4002-a530-c57489aa6851.png)

#### Incase if I want my title to showcase only when I receive messages (ex: 1 )

#### Do's (Conditional rendering of hooks)

![image](https://user-images.githubusercontent.com/42731246/160252828-4d4ff777-aa68-44b3-b792-b8120b9b569a.png)

#### Don't

![image](https://user-images.githubusercontent.com/42731246/160252906-8f96e800-4d2e-4411-9c0d-3f2dc1d19f29.png)

#### useEffect with dependency array

![image](https://user-images.githubusercontent.com/42731246/160253228-b995af9a-cfee-443d-8647-c49756ed0786.png)

#### useEffect with cleanup Function

![image](https://user-images.githubusercontent.com/42731246/160253693-ec309809-b027-4fef-a098-c41360aa151a.png)

#### useEffect- Fetch Data

### make sure to add dependency array as we only want to fetch the json data during initial render. (Also we want to avoid re-rendering)

![image](https://user-images.githubusercontent.com/42731246/160253778-53a3bd04-3507-43e6-8ab6-91c9f0f8ce11.png)

### Multiple returns basics

![image](https://user-images.githubusercontent.com/42731246/160253871-8b329504-40b7-46f5-8efc-061304d9da57.png)

### Fetching Example (Good Example)

```js
import React, { useState, useEffect } from "react"
const url = "https://api.github.com/users/QuincyLarson"
const MultipleReturns = () => {
  const [isLoading, setIsLoading] = useState(true)
  const [isError, setIsError] = useState(false)
  const [user, setUser] = useState("default user")

  useEffect(() => {
    fetch(url)
      .then((resp) => {
        if (resp.status >= 200 && resp.status <= 299) {
          return resp.json()
        } else {
          setIsLoading(false)
          setIsError(true)
          throw new Error(resp.statusText)
        }
      })
      .then((user) => {
        const { login } = user
        setUser(login)
        setIsLoading(false)
      })
      .catch((error) => console.log(error))
  }, [])

  if (isLoading) {
    return (
      <div>
        <h1>Loading...</h1>
      </div>
    )
  }
  if (isError) {
    return (
      <div>
        <h1>Error....</h1>
      </div>
    )
  }
  return (
    <div>
      <h1>{user}</h1>
    </div>
  )
}

export default MultipleReturns
```

### Short circuit Evaluation

On line 6 (text is empty, that means false)
On line 15 (as text value returns false, it looks for john value)
On line 16 (as text value returns false, it doesn't print hello world)
On line 17 (as text value returns true (reversed), it does print hello world)
![image](https://user-images.githubusercontent.com/42731246/160254203-c708adbe-455f-430a-a033-03504ccd8997.png)

### Ternary Operator Evaluation

isError is defined as useState hook (which declared as boolean value)
If isError is true we would see there is an error would print up else there is no error would printup

![image](https://user-images.githubusercontent.com/42731246/160254343-6edc872d-6f30-4169-8565-1f5dc31a86ff.png)

### Show/Hide logic using useState, useEffect

Every time show is true, we are running Item component.

```js
import React, { useState, useEffect } from "react"

const ShowHide = () => {
  const [show, setShow] = useState(false)
  return (
    <>
      <button className="btn" onClick={() => setShow(!show)}>
        show/hide
      </button>
      {show && <Item />}
    </>
  )
}

const Item = () => {
  const [size, setSize] = useState(window.innerWidth)
  const checkSize = () => {
    setSize(window.innerWidth)
  }
  useEffect(() => {
    window.addEventListener("resize", checkSize)
    return () => {
      window.removeEventListener("resize", checkSize)
    }
  }, [])

  return (
    <div style={{ marginTop: "2rem" }}>
      <h1>Window</h1>
      <h2>size : {size}</h2>
    </div>
  )
}

export default ShowHide
```

### Form Basics

On line 25, we don't need to use onClick (as we already used onSubmit on line 16)
![image](https://user-images.githubusercontent.com/42731246/160255132-69120b62-788f-4344-bb5b-1ba3cba51b30.png)

### Controlled Inputs

```js
// JS
// const input = document.getElementById('myText');
// const inputValue = input.value

// React
// value, onChange

import React, { useState } from "react"
const ControlledInputs = () => {
  const [firstName, setFirstName] = useState("")
  const [email, setEmail] = useState("")
  const [people, setPeople] = useState([])

  const handleSubmit = (e) => {
    e.preventDefault()
    if (firstName && email) {
      const person = { id: new Date().getTime().toString(), firstName, email }
      console.log(person)
      setPeople((people) => {
        return [...people, person]
      })
      setFirstName("")
      setEmail("")
    } else {
      console.log("empty values")
    }
  }
  return (
    <>
      <article>
        <form className="form" onSubmit={handleSubmit}>
          <div className="form-control">
            <label htmlFor="firstName">Name : </label>
            <input
              type="text"
              id="firstName"
              name="firstName"
              value={firstName}
              onChange={(e) => setFirstName(e.target.value)}
            />
          </div>
          <div className="form-control">
            <label htmlFor="email">Email : </label>
            <input
              type="email"
              id="email"
              name="email"
              value={email}
              onChange={(e) => setEmail(e.target.value)}
            />
          </div>
          <button type="submit">add person</button>
        </form>
        {people.map((person, index) => {
          const { id, firstName, email } = person
          return (
            <div className="item" key={id}>
              <h4>{firstName}</h4>
              <p>{email}</p>
            </div>
          )
        })}
      </article>
    </>
  )
}

export default ControlledInputs
```

### Multiple Inputs (Dynamically store the input value)

```js
import React, { useState } from "react"
// JS
// const input = document.getElementById('myText');
// const inputValue = input.value
// React
// value, onChange

const ControlledInputs = () => {
  const [person, setPerson] = useState({ firstName: "", email: "", age: "" })
  const [people, setPeople] = useState([])
  const handleChange = (e) => {
    const name = e.target.name
    const value = e.target.value
    setPerson({ ...person, [name]: value })
  }
  const handleSubmit = (e) => {
    e.preventDefault()
    if (person.firstName && person.email && person.age) {
      const newPerson = { ...person, id: new Date().getTime().toString() }
      setPeople([...people, newPerson])
      setPerson({ firstName: "", email: "", age: "" })
    }
  }
  return (
    <>
      <article className="form">
        <form>
          <div className="form-control">
            <label htmlFor="firstName">Name : </label>
            <input
              type="text"
              id="firstName"
              name="firstName"
              value={person.firstName}
              onChange={handleChange}
            />
          </div>
          <div className="form-control">
            <label htmlFor="email">Email : </label>
            <input
              type="email"
              id="email"
              name="email"
              value={person.email}
              onChange={handleChange}
            />
          </div>
          <div className="form-control">
            <label htmlFor="age">Age : </label>
            <input
              type="number"
              id="age"
              name="age"
              value={person.age}
              onChange={handleChange}
            />
          </div>
          <button type="submit" className="btn" onClick={handleSubmit}>
            add person
          </button>
        </form>
      </article>
      <article>
        {people.map((person) => {
          const { id, firstName, email, age } = person
          return (
            <div key={id} className="item">
              <h4>{firstName}</h4>
              <p>{email}</p>
              <p>{age}</p>
            </div>
          )
        })}
      </article>
    </>
  )
}

export default ControlledInputs
```

### 12. Advanced React- useRef

#####useState does trigger the re-renders and preseve the value whereas useRef doesn't trigger re-render but preserve the value

![image](https://user-images.githubusercontent.com/42731246/160294468-1792f1e3-6240-46cb-b3f0-76485e5d1a41.png)

![image](https://user-images.githubusercontent.com/42731246/160294812-ea04344f-a06a-4de1-9786-1cf68f10ebbd.png)

we don't need to useEffect with dependency array (as this logic will anyhow doesn't trigger re-render)

focus is to focus the input field upon initial render(component loaded for the first time)

![image](https://user-images.githubusercontent.com/42731246/160294837-a58e9826-41d9-43b6-ae19-cba8bd647375.png)

### 13. Advanced React- useReducer

#### Code differences between Todo app (useState vs useReducer)

##### i) Todo with useState

```js
import React, { useState } from "react"
import Modal from "./Modal"
import { data } from "../../../data"

const Index = () => {
  const [name, setName] = useState("")
  const [people, setPeople] = useState(data)
  const [showModal, setShowModal] = useState(false)

  const handleSubmit = (e) => {
    e.preventDefault()
    if (name) {
      setShowModal(true)
      setPeople([...people, { id: new Date().getTime().toString(), name }])
      setName("")
    } else {
      setShowModal(true)
    }
  }

  return (
    <>
      {showModal && <Modal />}
      <form onSubmit={handleSubmit}>
        <div>
          <input
            type="text"
            value={name}
            onChange={(e) => setName(e.target.value)}
          />
        </div>

        <button type="submit">add</button>
      </form>

      {people.map((person) => {
        return (
          <div key={person.id}>
            <h4>{person.name}</h4>
          </div>
        )
      })}
    </>
  )
}
```

#### useReducer-Basics

When we are invoking useReducer we are getting two things back

i) state, which is a value( we can call anything),
ii) dispatch, which is a function (we can call anything)

In the useReducer, the first thing we pass is the reducer function, the second thing is initialState

//reducer function manipulates the state
i) This reducer function looks for the two things (state that is right before the update, action (of what are we trying to do ))

##### Note: Always return the state in the reducer function

###### In short terms: useReducer looks for a reducer function which actually manipulates the state and it will happen once we dispatch the action

//initialState
ii) we use this as an object that have various properties (ex: people: [], loading:false, error:false)

##### To access these defaultState values (we need to write jsx like state.isModalOpen (this is due to line 13))

![image](https://user-images.githubusercontent.com/42731246/160296502-2a0cea76-ae46-47d7-adc8-84b5015456dd.png)

##### ii) Todo with useReducer

##### index.js

```js
import React, { useState, useReducer } from "react"
import Modal from "./Modal"
import { data } from "../../../data"
// reducer function
import { reducer } from "./reducer"
const defaultState = {
  people: [],
  isModalOpen: false,
  modalContent: "",
}
const Index = () => {
  const [name, setName] = useState("")
  const [state, dispatch] = useReducer(reducer, defaultState)
  const handleSubmit = (e) => {
    e.preventDefault()
    if (name) {
      const newItem = { id: new Date().getTime().toString(), name }
      dispatch({ type: "ADD_ITEM", payload: newItem })
      setName("")
    } else {
      dispatch({ type: "NO_VALUE" })
    }
  }
  const closeModal = () => {
    dispatch({ type: "CLOSE_MODAL" })
  }
  return (
    <>
      {state.isModalOpen && (
        <Modal closeModal={closeModal} modalContent={state.modalContent} />
      )}
      <form onSubmit={handleSubmit} className="form">
        <div>
          <input
            type="text"
            value={name}
            onChange={(e) => setName(e.target.value)}
          />
        </div>
        <button type="submit">add </button>
      </form>
      {state.people.map((person) => {
        return (
          <div key={person.id} className="item">
            <h4>{person.name}</h4>
            <button
              onClick={() =>
                dispatch({ type: "REMOVE_ITEM", payload: person.id })
              }
            >
              remove
            </button>
          </div>
        )
      })}
    </>
  )
}

export default Index
```

##### Modal.js

```js
import React, { useEffect } from "react"

const Modal = ({ modalContent, closeModal }) => {
  useEffect(() => {
    setTimeout(() => {
      closeModal()
    }, 3000)
  })
  return (
    <div className="modal">
      <p>{modalContent}</p>
    </div>
  )
}

export default Modal
```

##### reducer.js

```js
export const reducer = (state, action) => {
  if (action.type === "ADD_ITEM") {
    const newPeople = [...state.people, action.payload]
    return {
      ...state,
      people: newPeople,
      isModalOpen: true,
      modalContent: "item added",
    }
  }
  if (action.type === "NO_VALUE") {
    return { ...state, isModalOpen: true, modalContent: "please enter value" }
  }
  if (action.type === "CLOSE_MODAL") {
    return { ...state, isModalOpen: false }
  }
  if (action.type === "REMOVE_ITEM") {
    const newPeople = state.people.filter(
      (person) => person.id !== action.payload
    )
    return { ...state, people: newPeople }
  }
  throw new Error("no matching action type")
}
```

### Prop-Drilling Example

i) We have passed people data, removePerson function as props to List component

ii) Now in the List component we accepted them as props by destructuring.

iii) Inside the list component, we are using people data to map each and every person in the list and then passing them as props again to SinglePerson Component

iv) Inside the SinglePerson component, we accepted props (id means key prop, name is one of the property from person prop which is passed as spread operator, and removePerson logic is what was prop drilled from PropDrilling component to SinglePersonComponent)

v) This is what Prop-Drilling is, as we can see that List doesn't even require removePerson logic but we don't had another chance as we have to declare it just to use this removePerson logic in the successive child component.

vi) We can use useContext in this case to get rid of Prop-Drilling

vii) We can also use Redux but as the application grows bigger it is suggested to use Redux.

```js
import React, { useState } from "react"
import { data } from "../../../data"
// more components
// fix - context api, redux (for more complex cases)

const PropDrilling = () => {
  const [people, setPeople] = useState(data)
  const removePerson = (id) => {
    setPeople((people) => {
      return people.filter((person) => person.id !== id)
    })
  }
  return (
    <section>
      <h3>prop drilling</h3>
      <List people={people} removePerson={removePerson} />
    </section>
  )
}

const List = ({ people, removePerson }) => {
  return (
    <>
      {people.map((person) => {
        return (
          <SinglePerson
            key={person.id}
            {...person}
            removePerson={removePerson}
          />
        )
      })}
    </>
  )
}

const SinglePerson = ({ id, name, removePerson }) => {
  return (
    <div className="item">
      <h4>{name}</h4>
      <button onClick={() => removePerson(id)}>remove</button>
    </div>
  )
}

export default PropDrilling
```

### Context API/useContext

i) Well, first, we would need to create the context.

```js
const PersonContext = React.createContext()
```

ii) Now, the moment we do that now, we have access to two components, the provider and the consumer.

```js
// two components - Provider, Consumer
```

iii) So with the arrival of use context, we won't use the consumer.
iv) Previously, before the useContext hook was introduced, we were using the consumer. However, now we don't have to.
v) We get essentially two components back once you set up that create context and the way you access those components, you're going to go with PersonContext and then PersonContext.Provider or PersonContext.Consumer
vi) So the thing is, provider works as a distributor. So, look for your root component and then in the return of the root Component you would want to wrap in PersonContext and then the provider.

Ex: Refer Code below (ContextAPI is our root component and in that return we are now wrapping in PersonContext and then the Provider)

```js
const ContextAPI = () => {
  const [people, setPeople] = useState(data)
  const removePerson = (id) => {
    setPeople((people) => {
      return people.filter((person) => person.id !== id)
    })
  }

  return (
    <PersonContext.Provider value={{ removePerson, people }}>
      <h3>Context API / useContext</h3>
      <List />
    </PersonContext.Provider>
  )
}
```

vi) As observed for Provider we are having value prop, we can access this value using useContext.

vii) Now to access whatever we passed in the value prop (removePerson) in another Component (Ex: SinglePerson), make sure to use useContext hook and inside this useContext hook we need to pass in the Context that we have created (PersonContext)

```js
const SinglePerson = ({ id, name }) => {
  const { removePerson } = useContext(PersonContext)

  return (
    <div className="item">
      <h4>{name}</h4>
      <button onClick={() => removePerson(id)}>remove</button>
    </div>
  )
}
```

If else you want value prop in List Component, refer to the example code

Note: When we log mainData---> we get this as object which has all the properties like people, removePerson.

If we want we can directly destructure which is something like below

```js
const { people } = useContext(PersonContext)
```

```js
const List = () => {
  const mainData = useContext(PersonContext)
  console.log(mainData)
  return (
    <>
      {mainData.people.map((person) => {
        return <SinglePerson key={person.id} {...person} />
      })}
    </>
  )
}
```

###### Quick Summary till point 7:

###### We have a PersonContext.Provider that needs to wrap your whole component tree or whole application.

###### When we talk about PersonContext, we need to pass this PersonContext into the useContext hook

### Custom Hooks

i) Custom Hooks helps us in reusing the functionality(fetching data, saving to local storage)
ii) return an object with values such as loading, products (by the way, naming convention can be anything)
iii) CustomHook requires an url and the component should update everytime the url changes
iv) Custom Hooks works when we use (use keyword --->Ex: useFetch)

##### We are using below custom Hook (useFetch ) and importing in the another component (Example Component)

##### Code of custom hook, (with this code, console would be showing a warning as a missing dependency inside the useEffect )

```js
import { useState, useEffect, useCallback } from 'react';

export const useFetch = (url) => {
  const [loading, setLoading] = useState(true);
  const [products, setProducts] = useState([]);

  const getProducts =async () => {
    const response = await fetch(url);
    const products = await response.json();
    setProducts(products);
    setLoading(false);
  }, [url];

  useEffect(() => {
    getProducts();
  }, [url]);
  return { loading, products };
};
```

##### Code of custom hook, to resolve missing dependency inside the useEffect

```js
import { useState, useEffect, useCallback } from "react"

export const useFetch = (url) => {
  const [loading, setLoading] = useState(true)
  const [products, setProducts] = useState([])

  const getProducts = useCallback(async () => {
    const response = await fetch(url)
    const products = await response.json()
    setProducts(products)
    setLoading(false)
  }, [url])

  useEffect(() => {
    getProducts()
  }, [url, getProducts])
  return { loading, products }
}
```

###### In our above case getProducts is added to the dependency array inside useEffect. This works correctly only when the getProducts function is wrapped with useCallback as now it checks for the url dependency array and it only create the function or trigger the re-render when url gets updated.

###### In case if we directly add getProducts in useEffect dependency array and if we haven't wrapped our function inside useCallback then it would lead to an infinite loop.

###### If it sounds confusing, refer to the further examples on useCallback

##### As we were returning object in our Custom Hook and we used useState in our Custom Hook which usually returns an array and we do array destructuring.

```js
import React, { useState, useEffect } from "react"
import { useFetch } from "./2-useFetch"

const url = "https://course-api.com/javascript-store-products"

const Example = () => {
  const { loading, products } = useFetch(url)
  console.log(products)
  return (
    <div>
      <h2>{loading ? "loading..." : "data"}</h2>
    </div>
  )
}

export default Example
```

### PropTypes

i) We'll have to set up a prop types property on the component. So we go with the name of the component.

In this case it is a product and then we go with prop types. So that is the name of the property.

Note: Instead of breaking your application (blank page or unexpected behaviour), PropTypes help you by throwing those logs in the console saying you need to do something because the props that you are expecting well, in one of the items, they are missing.

ii) To handle these situations, we can use short circuit operators or default props

```js
import PropTypes from "prop-types"
import defaultImage from "../../../assets/default-image.jpeg"
const Product = ({ image, name, price }) => {
  const url = image && image.url
  return (
    <article className="product">
      <img src={url || defaultImage} alt={name || "default name"} />
      <h4>{name}</h4>
      <p>${price || 3.99}</p>
    </article>
  )
}

Product.propTypes = {
  image: PropTypes.object.isRequired,
  name: PropTypes.string.isRequired,
  price: PropTypes.number.isRequired,
}
// Product.defaultProps = {
//   name: 'default name',
//   price: 3.99,
//   image: defaultImage,
// };

export default Product
```

### Performance Optimization

![image](https://user-images.githubusercontent.com/42731246/161441383-75ef39cb-0a2a-400e-a158-2b3529a8c1ea.png)

### i) React.memo

As useState triggers the re-render for everytime the value changes, our entire components gets re-renders everytime we click on count button (which should not be the case)

With React.memo (we should actually need to wrap it to the whole component) as it will check if the value of props or state is changed, in our case it was products which was passed as props which was not changing and in this case React.memo works good

```js
import React, { useState, useEffect, useCallback, useMemo } from "react"
import { useFetch } from "../../9-custom-hooks/final/2-useFetch"

const url = "https://course-api.com/javascript-store-products"

// every time props or state changes, component re-renders

const Index = () => {
  const { products } = useFetch(url)
  const [count, setCount] = useState(0)

  return (
    <>
      <h1>Count : {count}</h1>
      <button className="btn" onClick={() => setCount(count + 1)}>
        click me
      </button>
      <BigList products={products} />
    </>
  )
}

const BigList = React.memo(({ products }) => {
  return (
    <section className="products">
      {products.map((product) => {
        return <SingleProduct key={product.id} {...product}></SingleProduct>
      })}
    </section>
  )
})

const SingleProduct = ({ fields }) => {
  let { name, price } = fields
  price = price / 100
  const image = fields.image[0].url

  return (
    <article className="product">
      <img src={image} alt={name} />
      <h4>{name}</h4>
      <p>${price}</p>
    </article>
  )
}
export default Index
```

###### React.memo has its own disadvantages (when something like a function AddToCart is passed as props to the SingleProduct)

###### In addToCart function, the value is changing everytime and whenver this is passed as props, the SingleProduct component is getting re-rendered everytime the value changes.

```js
const addToCart = () => setCart(cart + 1)
```

```js
const SingleProduct = ({ fields, addToCart }) => {
  let { name, price } = fields
  price = price / 100
  const image = fields.image[0].url

  // useEffect(() => {
  //   console.count('hello from product');
  // });
  return (
    <article className="product">
      <img src={image} alt={name} />
      <h4>{name}</h4>
      <p>${price}</p>
      <button onClick={addToCart}>add to cart</button>
    </article>
  )
}
```

So that's why React thinks that, this value changed and that's why, again, we're triggering the re-rendering.

Now, what is the solution? The solution is using useCallback, which essentially is somewhat similar like we were doing with a memo but now it is going to do with the function.

Which is similarly like (look up for the value of the function is changed or not (If changes --> Need to re-create the function))

### useCallback

We wrap our function in the parentheses, But also what I would want is the dependancy (So now we create this function only when we update the cart value)

If we don't add the cart as the dependency, cart value will be always zero only

This is because even though my value got updated in the state, since I didn't create this below function due to empty dependency when the cart state value changed, we will be always sitting on the zero.

That is why adding cart as dependency array is very important

```js
const addToCart = useCallback(() => {
  setCart(cart + 1)
}, [cart])
```

### useMemo

Instead of memoizing the function(which we have seen the useCallback was dealing), here useMemo deals with memoizing the value

In our below example, calculateMostExpension function will return some value and in this case this would perform some operations and takes some time to calculate this value.

```js
const calculateMostExpensive = (data) => {
  return (
    data.reduce((total, item) => {
      const price = item.fields.price
      if (price >= total) {
        total = price
      }
      return total
    }, 0) / 100
  )
}
```

It would be nice to remember the value which gets returned from the above function and only run the function when the data changes (So in my case, of course, that is the products value which is given as a parameter inside the calculateMostExpension)

And to solve the above issue, useMemo can be used. (we need to pass is a callback function and the first thing we need to setup is the function that returns a value which in our case is calculateMostExpension and the second thing is the dependency array.
And again, in this case, I'm passing in the products.)

```js
const mostExpensive = useMemo(
  () => calculateMostExpensive(products),
  [products]
)
```

### Complete code(React.memo, useCallback, useMemo) for Reference

```js
import React, { useState, useCallback, useMemo } from "react"
import { useFetch } from "../../9-custom-hooks/final/2-useFetch"

const url = "https://course-api.com/javascript-store-products"

// every time props or state changes, component re-renders
const calculateMostExpensive = (data) => {
  return (
    data.reduce((total, item) => {
      const price = item.fields.price
      if (price >= total) {
        total = price
      }
      return total
    }, 0) / 100
  )
}
const Index = () => {
  const { products } = useFetch(url)
  const [count, setCount] = useState(0)
  const [cart, setCart] = useState(0)

  const addToCart = useCallback(() => {
    setCart(cart + 1)
  }, [cart])

  const mostExpensive = useMemo(
    () => calculateMostExpensive(products),
    [products]
  )
  return (
    <>
      <h1>Count : {count}</h1>
      <button className="btn" onClick={() => setCount(count + 1)}>
        click me
      </button>
      <h1 style={{ marginTop: "3rem" }}>cart : {cart}</h1>
      <h1>Most Expensive : ${mostExpensive}</h1>
      <BigList products={products} addToCart={addToCart} />
    </>
  )
}

const BigList = React.memo(({ products, addToCart }) => {
  return (
    <section className="products">
      {products.map((product) => {
        return (
          <SingleProduct
            key={product.id}
            {...product}
            addToCart={addToCart}
          ></SingleProduct>
        )
      })}
    </section>
  )
})

const SingleProduct = ({ fields, addToCart }) => {
  let { name, price } = fields
  price = price / 100
  const image = fields.image[0].url

  return (
    <article className="product">
      <img src={image} alt={name} />
      <h4>{name}</h4>
      <p>${price}</p>
      <button onClick={addToCart}>add to cart</button>
    </article>
  )
}
export default Index
```

### React Router 6 - Updated Version

i) You see, unlike traditional multipage applications, where each time user requests a page, they are stretched from the server and as a result there is a page refresh.

ii) When it comes to react we will build single page applications where all of the HTML JavaScript is loaded at once and the rest of the functionality is handled by JavaScript. And as a result our project gets that snappy app like Feel.

iii) Now React does not have built in support for routing. In other words, we will need to use an extra library for that. And the most popular choice out there is React Router.

iv) We want to get the browser router which is going to connect to the actual browser,

v) The routes component, which is going to be a parent for all our routes and then route component, which we'll use to set up a single page.

```js
import { BrowserRouter, Routes, Route } from "react-router-dom"

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<div>home page</div>} />
        <Route
          path="testing"
          element={
            <div>
              <h2>testing </h2>
            </div>
          }
        />
      </Routes>
    </BrowserRouter>
  )
}

export default App
```

vi) Passing compnents in a route

```js
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="about" element={<About />} />
    <Route path="products" element={<Products />} />
  </Routes>
</BrowserRouter>
```

vi) Linking to the other pages inside our React app, make sure to match up /about from Link to the Route path ='about' (there is no slash here but still it works)

```js

import { Link } from 'react-router-dom';

const Home = () => {
  return (
    <div>
      <h2>Home Page</h2>
      <Link to='/about' className='btn'>
        About
      </Link>
      <a href="">
    </div>
  );
};
export default Home;
```

vii) Error Page (route logic not found)

```js
<Route path="*" element={<Error />} />
```

#### viii) Nested pages

Actually the parent route is nested into the other 3 child routes.
The behaviour looks something like /about (as only / is given in parent)

And this is how we are calling the below based on parent. Ex: /about or /products

In Case if we have dashboard instead of / then it should look like /dashboard/about or /dashboard/products

```js
function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />}>
          <Route path="about" element={<About />} />
          <Route path="products" element={<Products />} />
          <Route path="*" element={<Error />} />
        </Route>
      </Routes>
    </BrowserRouter>
  )
}
```

### Shared Layout

###### How we can set up a shared layout?

i) Well, we need to go to the parent, in our case Home Component and import Outlet from react-router-dom.

And then we just need to display this Outlet component and whatever we'll set up around this outlet component is going to be the shared layout across the pages that are nested inside of the parent and then the actual page content will be displayed here in the output one.

Ex: If Navbar component is nested inside of the parent then the Navbar will be shared layout

```js
import { Link } from "react-router-dom"
const Navbar = () => {
  return (
    <nav className="navbar">
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
      <Link to="/products">Products</Link>
    </nav>
  )
}
export default Navbar
```

![image](https://user-images.githubusercontent.com/42731246/161842297-db023920-ad45-4bc8-810e-f6e5e6ff8fa0.png)

So whatever we have in the about, product. Essentially all the pages that we have nested.

And as a result, notice not only I display the contents of the about page or the product page, but also we have a navbar.
