# React

Created: November 29, 2023 2:59 PM
Class: React
Reviewed: No

# React Setup and Project Structure

initializing a React project using Vite:

1. First, open your terminal and run the following commands:

```bash

npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev

```

This will:

- Create a new Vite project with React template
- Navigate into the project directory
- Install all necessary dependencies
- Start the development server

Once you've done this, you'll see a new React application running on `http://localhost:5173` (or similar port).

Look at your project structure. The key files we'll be working with are:

- `src/App.jsx`: Main application component
- `src/main.jsx`: Entry point of the application
- `index.html`: The HTML template

**Q. What is the difference between src/App.jsx and src/Main.jsx ? Why are two different jsx files required? How are they used in the project?** 

`src/main.jsx`:

- This is the entry point of your React application
- It's responsible for rendering your React app into the DOM
- It typically looks like this:

```jsx

import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)

```

Key points about `main.jsx`:

1. It imports the necessary React libraries
2. It finds the DOM element with id 'root' (which is in index.html)
3. Creates a React root and renders your app into it
4. Usually, you rarely need to modify this file

`src/App.jsx`:

- This is your main application component
- It's where you start writing your actual application code
- A simple example looks like:

```jsx

import { useState } from 'react'
import './App.css'

function App() {
  return (
    <div>
      <h1>Hello from App component!</h1>
    </div>
  )
}

export default App

```

Think of it this way:

- `main.jsx` is like the foundation of a house - it sets up the basic structure and tells React where to put your application
- `App.jsx` is like the house itself - it's where you actually build your application's features

This separation follows a common pattern in React applications:

1. Keep initialisation code (`main.jsx`) separate from application code (`App.jsx`)
2. Make the entry point (`main.jsx`) as simple as possible
3. Put all the actual application logic in components, starting with `App.jsx`

## ReactDOM

- **Virtual DOM**: React uses a **Virtual DOM** before interacting with the browser’s normal DOM. The Virtual DOM is a lightweight copy of the real DOM, where React tracks changes and updates efficiently.
- **Efficient Updates**: ReactDOM focuses on **efficient updates** to the DOM by batching changes and only updating parts of the UI that have changed. It uses a "diffing" algorithm to compare the current Virtual DOM with the previous version and only updates the changed parts.
- **Declarative API**: ReactDOM provides a declarative API via `ReactDOM.render()`, which abstracts away direct manipulation of the real DOM. Instead of manually querying and modifying elements, you define the UI using React components, and ReactDOM handles the updates.
- **Single Responsibility**: ReactDOM is specifically responsible for updating the **DOM elements** rendered by React components. It serves as a bridge between React components and the browser’s actual DOM.

**Example**:

```jsx

import React from 'react';
import ReactDOM from 'react-dom';

const element = <h1>Hello, world!</h1>;
ReactDOM.render(element, document.getElementById('root'));

```

In this example, `ReactDOM.render()` updates the content of the `#root` element with the React element.

### 2. **Normal DOM (Browser DOM)**:

- **Direct Manipulation**: The normal DOM is the **direct representation** of the HTML document in the browser. It allows developers to directly query and manipulate elements using methods like `getElementById()`, `querySelector()`, `appendChild()`, etc.
- **Synchronous Updates**: When you manipulate the DOM directly, the updates are immediate and synchronous. This can be less efficient if you have many changes, as each update can trigger a reflow or repaint of the webpage.
- **Imperative API**: The normal DOM uses an **imperative approach**, meaning you explicitly tell the browser how to change the UI. For example:
    
    ```jsx
    
    const element = document.getElementById('root');
    element.innerHTML = '<h1>Hello, world!</h1>';
    
    ```
    

### **Key Differences**:

| Feature | ReactDOM | Normal DOM (Browser DOM) |
| --- | --- | --- |
| **Update Efficiency** | Uses Virtual DOM for efficient updates | Updates directly, may be less efficient |
| **API Approach** | Declarative (e.g., `ReactDOM.render()`) | Imperative (e.g., `innerHTML`, `appendChild()`) |
| **Update Model** | Batch updates using diffing | Immediate, synchronous updates |
| **Ease of Use** | Manages updates automatically | Manual DOM manipulation |
| **Reactivity** | Reactive, based on state/props | No built-in reactivity |

### When to Use ReactDOM:

- Use **ReactDOM** when building applications with React for more efficient updates and a declarative approach.
- Use **normal DOM manipulation** for simple scripts or when you do not need the overhead of a library like React.

In summary, ReactDOM enhances the efficiency of UI updates through the use of the Virtual DOM, providing a declarative way to manage the user interface. In contrast, normal DOM manipulation is more manual and immediate, but it can become inefficient for complex, dynamic updates.

# **React: The Virtual DOM**

**How React’s virtual DOM prevents wasteful DOM manipulation.**

## **The Problem**

DOM manipulation is the heart of the modern, interactive web. Unfortunately, it is also a lot slower than most JavaScript operations.

This slowness is made worse by the fact that **most JavaScript frameworks update the DOM much more than they have to.**

As an example, let’s say that you have a list that contains ten items. You check off the first item. Most JavaScript frameworks would rebuild *the entire list*. That’s ten times more work than necessary! Only one item changed, but the remaining nine get rebuilt exactly how they were before.

Rebuilding a list is no big deal to a web browser, but modern websites can use huge amounts of DOM manipulation. Inefficient updating has become a serious problem.

To address this problem, the people at React popularized something called the *virtual DOM.*

## **The Virtual DOM**

Here is a refresher of what happens behind the scenes in [**The Virtual DOM**](https://www.youtube.com/watch?v=jwRAdGLUarw).

In React, for every [DOM object](http://eloquentjavascript.net/13_dom.html), there is a corresponding “virtual DOM object.” A virtual DOM object is a *representation* of a DOM object, like a lightweight copy.

A virtual DOM object has the same properties as a real DOM object, but it lacks the real thing’s power to directly change what’s on the screen.

Manipulating the DOM is slow. Manipulating the virtual DOM is much faster because nothing gets drawn onscreen. Think of manipulating the virtual DOM as editing a blueprint, as opposed to moving rooms in an actual house.

## **How It Helps**

When you render a JSX element, every single virtual DOM object gets updated.

This sounds incredibly inefficient, but the cost is insignificant because the virtual DOM can update so quickly.

Once the virtual DOM has been updated, then React compares the virtual DOM with a virtual DOM *snapshot* that was taken right before the update.

By comparing the new virtual DOM with a pre-update version, React figures out *exactly which virtual DOM objects have changed.* This process is called “diffing.”

Once React knows which virtual DOM objects have changed, then React updates those objects, *and only those objects,* on the real DOM. In our example from earlier, React would be smart enough to rebuild your one checked-off list-item and leave the rest of your list alone.

This makes a big difference! React can update only the necessary parts of the DOM. React’s reputation for performance comes largely from this innovation.

In summary, here’s what happens when you try to update the DOM in React:

1. The entire virtual DOM gets updated.
2. The virtual DOM gets compared to what it looked like before you updated it. React figures out which objects have changed.
3. The changed objects, and the changed objects only, get updated on the *real* DOM.
4. Changes on the real DOM cause the screen to change.

## JSX in React.js

**JSX (JavaScript XML)** is a syntax extension for JavaScript that looks similar to HTML. It allows you to write HTML elements directly within JavaScript code, making it easier to create React components. JSX is not a separate language; it gets transpiled to regular JavaScript before being executed in the browser using tools like Babel.

### Why use JSX?

- **Easier to write**: It looks like HTML, which is familiar and easy to read.
- **Integration with JavaScript**: You can easily include JavaScript logic within JSX using `{}`.
- **Enhanced readability**: It helps to visually structure the UI code.

### Example: JSX vs. Regular JavaScript

Without JSX:

```jsx

// Using React without JSX
const element = React.createElement('h1', {}, 'Hello, world!');

```

With JSX:

```jsx

// Using React with JSX
const element = <h1>Hello, world!</h1>;

```

In the example above, the JSX code is much simpler and more intuitive compared to the React `createElement` syntax.

### How JSX Works

Behind the scenes, JSX gets converted into plain JavaScript using tools like Babel. The code:

```jsx

const element = <h1>Hello, world!</h1>;

```

gets transformed into:

```jsx

const element = React.createElement('h1', null, 'Hello, world!');

```

This is why you need to import React in older versions of React when using JSX (`import React from 'react'`). However, in React 17 and later, importing React is no longer required.

### Writing JSX: Basic Syntax

### 1. Embedding JavaScript Expressions

You can embed any JavaScript expression inside JSX using curly braces `{}`.

```jsx

const name = 'Alice';
const element = <h1>Hello, {name}!</h1>;

```

Output:

```

Hello, Alice!
```

### 2. Attributes in JSX

JSX attributes are similar to HTML attributes, but some of them have different names because they are JavaScript keywords.

```jsx

// HTML attribute
<button class="btn">Click Me</button>

// JSX attribute (uses `className` instead of `class`)
<button className="btn">Click Me</button>

```

### 3. JSX Must Have One Parent Element

In JSX, elements must be wrapped in a single parent element. You cannot have sibling elements without a parent.

```jsx

// Incorrect
// Error: Adjacent JSX elements must be wrapped in an enclosing tag
return (
  <h1>Hello</h1><p>This is a paragraph</p>
);

// Correct
return (
  <div>
    <h1>Hello</h1>
    <p>This is a paragraph</p>
  </div>
);

```

Or use **React fragments** (an empty tag) to wrap elements:

```jsx

return (
  <>
    <h1>Hello</h1>
    <p>This is a paragraph</p>
  </>
);

```

### Do's and Don'ts of JSX

### ✅ Do's

1. **Use Curly Braces for JavaScript Expressions:**

```jsx

const age = 30;
<p>Your age is {age}</p>;
```

1. **Use CamelCase for Attribute Names:**

```jsx

<button onClick={handleClick}>Click Me</button>
```

1. **Wrap Multiline JSX with Parentheses:**

```jsx

return (
  <div>
    <h1>Hello</h1>
    <p>This is a paragraph.</p>
  </div>
);
```

### ❌ Don'ts

1. **Don't use `class` as an attribute name:** Use `className` instead.

```jsx

// Incorrect
<div class="container"></div>

// Correct
<div className="container"></div>
```

1. **Don't use `for` as an attribute name:** Use `htmlFor` instead (for labels).

```jsx

// Incorrect
<label for="name">Name:</label>

// Correct
<label htmlFor="name">Name:</label>
```

1. **Avoid using JavaScript statements directly in JSX:** You can only use expressions, not statements like `if` or `for`.

```jsx

// Incorrect
return <h1>{if (isLoggedIn) 'Welcome!'}</h1>;

// Correct (use a ternary operator)
return <h1>{isLoggedIn ? 'Welcome!' : 'Please log in.'}</h1>;
```

## **React Components**

In the realm of React, the core concept revolves around components. Components are the foundational building blocks of any React application, constituting its fundamental structure. In essence, a React application is entirely constructed from these components. Every element within a React app is either a component or resides within one. This fundamental nature of components underscores their paramount importance in React development.

**Defining React Components:**

React components can be understood as the elemental units that collectively shape a user interface (UI). When we inspect any React application, the absence of components is virtually non-existent, or at the very least, everything resides within some form of a component. This leads to the assertion that components serve as the essential constituents of React user interfaces.

**Role of React in Component Rendering:**

React primarily operates by taking these components and rendering them onto a webpage, thereby forming the user interface. In more technical terms, React orchestrates the rendering of views for each component, and the aggregation of these views composes the overall user interface.

**Characteristics of Components:**

Key attributes of components include the fact that each component encapsulates its own data, JavaScript logic, and appearance. This encapsulation enables components to distinctly define how they function and their visual representation. This inherent property makes components an effective tool for constructing user interfaces.

**Component Composition in React:**

In React, the construction of complex UIs involves the creation of multiple components, subsequently combining these components akin to assembling Lego pieces. Larger components, such as a video player, a menu, or a list of questions, can be identified within the UI. Furthermore, the practice of nesting components inside one another, a key aspect of React, enhances component reusability and contributes to the overall structure of the user interface.

**Component Reusability and Props:**

A notable aspect of React development involves creating reusable components to manage UI duplication efficiently. For instance, identical questions in a list can be handled by creating a single question component and reusing it with distinct data. This is facilitated by the use of "props," a mechanism to pass data into components.

**Understanding Component Hierarchy:**

To facilitate the analysis of component relationships and structure, a component tree is employed. This tree diagram illustrates the hierarchy existing between components, elucidating how components nest within each other. It serves as a powerful tool to comprehend the relationships and interactions among components.

**Parent-Child Relationships in React:**

React frequently employs the terms "parent" and "child" components to describe relationships within a component tree. For instance, a component tree may reveal that the "refined questions" component is the parent of the "filters" component. Clear understanding of these relationships is pivotal in React development.

### **Functional Components**

### What are Functional Components?

In React, **components** are the building blocks of your application. They allow you to split your UI into isolated, reusable pieces of code. Functional components are a simpler way to create components using JavaScript functions.

### Characteristics of Functional Components:

- They are **simple JavaScript functions**.
- They **accept props** (input data) and return JSX (UI elements).
- They do not have their own internal state (unless you use hooks like `useState`).
- They are generally easier to read, write, and test compared to class components.

### Example of a Functional Component:

```jsx

// MyComponent.js
import React from 'react';

// Functional Component
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Using the component
export default Greeting;

```

Usage:

```jsx

// App.js
import React from 'react';
import Greeting from './MyComponent';

function App() {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
    </div>
  );
}

export default App;

```

Output:

```

Hello, Alice!
Hello, Bob!

```

### Explanation:

- **Props**: `props` is an object that holds the input data passed to the component. In this example, `props.name` is used to display the name.
- **JSX**: The `Greeting` function returns JSX, which is rendered as HTML.

### **The Return Keyword in Functional Components**

When we define a functional component, we essentially define a factory that can build the appropriate combination of elements every time we reference its name. It builds it by consulting a set of instructions that you must provide.

If you’re thinking, “That sounds just like what a regular Javascript function is for”, then you’re right! Functional components can be thought of in a very similar vein to regular Javascript functions, except that their job is to assemble a portion of the interface based on instructions given!

These instructions should take the form of a function declaration body. That means that they will be delimited by curly braces, like this:

```jsx
function Button() {
  // Instructions go here, between the curly braces.
}
```

Our instructions can include a combination of markup, CSS, and JavaScript to produce the desired result. The one thing we must always include is a **return** statement.

The function is expected to produce JSX code that can be used to render something onto the browser screen. Thus, when we define functional components, we must return a JSX element.

```jsx
function BackButton() {
 return <button>Back To Home</button>;
}
```

Of course, this doesn’t quite make `<button>Back To Home</button>` render onto the browser screen yet. We’ve only defined our component.

### Differences Between Functional and Class Components:

Earlier, React had two types of components: **class components** and **functional components**. Class components used to be more popular because they could handle state and lifecycle methods. However, with the introduction of **React Hooks** (like `useState` and `useEffect`), functional components can now manage state and lifecycle events as well. This is why functional components are preferred in modern React development.

### Example Using `useState` Hook:

```jsx

import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click Me</button>
    </div>
  );
}

export default Counter;

```

**Explanation:**

- **useState**: This is a React Hook that lets you add state to a functional component. In this example, `count` is a piece of state, and `setCount` is a function to update it.

Output:

```bash

You clicked 0 times
[Click Me Button]

```

### Do's and Don'ts of Functional Components:

**✅ Do:**

- Use functional components for simplicity and readability.
- Use React Hooks to manage state and side effects.
- Use destructuring to access props:

```jsx
// name and age are props which have been de-structured below
function UserProfile({ name, age }) {
  return <p>{name} is {age} years old.</p>;
}

```

**❌ Don't:**

- Avoid using old class components unless necessary for legacy codebases.
- Don't mutate props or state directly (always use functions like `setState` or `useState` for updates).

### Props in React

- **Props (short for "properties")** are arguments passed to a React component, either functional or class-based.
- These props are provided as a single **object**, where each key corresponds to the name of a prop, and its value corresponds to the value passed from the parent component.

---

### **Why are props always an object?**

- React components follow a consistent API design. When you pass props to a component, React gathers all the props and combines them into a single object that gets passed as the first parameter to functional components.

For example:

```jsx

function MyComponent(props) {
  console.log(props);
  return <div>{props.message}</div>;
}

// Usage
<MyComponent message="Hello, World!" />

```

When `MyComponent` is called, `props` is:

```jsx

{ message: "Hello, World!" }
```

Even if you pass multiple props, they will still be combined into a single `props` object:

```jsx

<MyComponent message="Hello, World!" count={42} />
```

Here, `props` would look like:

```jsx

{ message: "Hello, World!", count: 42 }
```

---

### **What if no props are passed?**

- If no props are passed to a component, the `props` object is simply an **empty object** (`{}`), ensuring a consistent type for the parameter.

For example:

```jsx

function MyComponent(props) {
  console.log(props); // Logs: {}
  return <div>No props passed</div>;
}

<MyComponent />

```

---

### **Can props be accessed directly as individual variables?**

No, not directly. But you can use **object destructuring** to extract individual prop values from the `props` object for convenience.

For example:

```jsx

function MyComponent({ message, count }) {
  return (
    <div>
      <p>{message}</p>
      <p>{count}</p>
    </div>
  );
}

<MyComponent message="Hello!" count={42} />

```

The destructuring syntax `{ message, count }` is equivalent to:

```jsx

function MyComponent(props) {
  const { message, count } = props;
  return (
    <div>
      <p>{message}</p>
      <p>{count}</p>
    </div>
  );
}
```

---

### **What about children?**

React automatically includes the `children` prop inside the `props` object. If a component is passed any child elements, they will be available in `props.children`.

For example:

```jsx

function MyComponent(props) {
  return <div>{props.children}</div>;
}

<MyComponent>
  <p>This is a child</p>
</MyComponent>

```

Here, `props` will look like:

```jsx

{
  children: <p>This is a child</p>
}

```

---

### **Key Takeaways**

1. **Props are always an object**: Even if you pass one prop or none at all, React wraps them into an object for consistency.
2. **Object destructuring** can make props easier to work with inside the component.
3. React automatically includes the `children` prop in the `props` object if the component has child elements.

### State in React

**State** is a fundamental concept in React that allows components to keep track of data that can change over time. It enables React components to respond to user interactions and updates by dynamically re-rendering the UI. 

In React, **state** is like a special kind of data storage that's used to keep track of dynamic information in a component. Think of state as the "memory" of a component—it helps the component remember certain pieces of information that might change over time.

### **Analogy: Your Component as a Warehouse**

Imagine your React component is a warehouse. Inside this warehouse, you have shelves filled with items (data). Some of these items are static (like labels or decorations that never change), but some items might change frequently (like stock levels). This frequently-changing data is what we call **state**.

For example:

- In a shopping cart component, the **state** could store the number of items in the cart.
- In a weather app component, the **state** could store the current temperature.
- In a to-do list component, the **state** could store the list of tasks.

## **How is State Different from Props?**

Before we go further, let’s distinguish **state** from **props**:

- **State** is *internal* to the component and can change over time.
- **Props** are *external* inputs to a component that are passed down from a parent component.

### **Analogy: State vs. Props**

Imagine you have a remote-controlled car:

- The **state** is like the car’s internal battery level—it’s something the car knows about itself and can change internally.
- The **props** are like the commands you send to the car via the remote control—you provide this input from the outside.

### Key Points About State:

1. **State is mutable:** It can change over time based on user interactions or other events.
2. **State is private:** It belongs to the specific component where it is declared and cannot be accessed directly by other components (unless passed down as props).
3. **State triggers re-rendering:** When the state changes, React automatically re-renders the component to reflect the new state.

### Example of State in a Functional Component

To manage state in functional components, React provides a **Hook** called `useState`.

### What is `useState`?

The `useState` hook is a function that lets you add state to your functional components. It returns two values:

1. **The current state value**
2. **A function to update the state**

## **Rules of Using State**

There are a few important rules to keep in mind when using state in React:

1. **State Should Be Immutable**: You shouldn’t modify the state directly. Instead of changing `count` directly, use the setter function (`setCount`). This ensures React knows when the state has changed.
    - ❌ **Don’t do this**: `count = count + 1;`
    - ✅ **Do this**: `setCount(count + 1);`
2. **State Updates Are Asynchronous**: State updates in React don’t happen immediately. React batches them for performance reasons. If you need to update state based on its previous value, use a callback function:
    
    ```jsx
    
    setCount(prevCount => prevCount + 1);
    ```
    
3. **State Only Exists Within the Component**: Each component has its own state. Changing the state in one component won’t affect the state in another component unless they share the state through a common parent.

### Syntax:

```jsx

const [stateVariable, setStateFunction] = useState(initialValue);
```

- `stateVariable` is the name of your state variable.
- `setStateFunction` is the function used to update the state.
- `initialValue` is the initial value of the state (e.g., `0`, `''`, `false`, or an object).

### Example: Simple Counter Using `useState`

```jsx

import React, { useState } from 'react';

function Counter() {
  // Declare a state variable 'count' with an initial value of 0
  const [count, setCount] = useState(0);

  // Function to handle button click and update the state
  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}

export default Counter;

```

### Explanation:

1. **useState(0)**: Initializes the `count` state variable with a value of `0`.
2. **setCount(count + 1)**: Updates the state by increasing `count` by 1.
3. **Re-rendering**: When `setCount` is called, React re-renders the component to show the updated count.

Output:

```mathematica

Count: 0
[Increment Button]
```

Each time you click the button, the count increases by 1.

### How `useState` Works

- When you call `useState`, it initializes the state with the given initial value.
- React remembers the state across re-renders.
- When you update the state using the setter function (e.g., `setCount`), React schedules a re-render of the component.
- The new state value is applied, and the updated UI is displayed.

### Using `useState` with Different Data Types

1. **String State:**

```jsx

import React, { useState } from 'react';

function Greeting() {
  const [name, setName] = useState('Guest');

  return (
    <div>
      <p>Hello, {name}!</p>
      <button onClick={() => setName('Alice')}>Change Name</button>
    </div>
  );
}

export default Greeting;
```

Output:

```jsx

Hello, Guest!
[Change Name Button]

```

When you click the button, the name changes to "Alice".

1. **Boolean State:**

```jsx

import React, { useState } from 'react';

function Toggle() {
  const [isOn, setIsOn] = useState(false);

  return (
    <button onClick={() => setIsOn(!isOn)}>
      {isOn ? 'ON' : 'OFF'}
    </button>
  );
}

export default Toggle;
```

Output:

```jsx

[OFF Button]
```

Each click toggles between "ON" and "OFF".

1. **Object State:**

When managing complex data, you can use objects as state variables.

```jsx

import React, { useState } from 'react';

function UserProfile() {
  const [user, setUser] = useState({ name: 'John', age: 30 });

  const updateAge = () => {
    setUser({ ...user, age: user.age + 1 });
  };

  return (
    <div>
      <h2>Name: {user.name}</h2>
      <h3>Age: {user.age}</h3>
      <button onClick={updateAge}>Increase Age</button>
    </div>
  );
}

export default UserProfile;

```

### Explanation:

- **Spread Operator (`...user`)**: It copies the existing properties of `user` and updates only the `age` property.
- **Reactivity**: When the state is updated, the UI re-renders automatically.

### Do's and Don'ts of State in React

**✅ Do:**

- Use `useState` for managing local state in functional components.
- Use separate state variables for unrelated pieces of state:

```jsx

const [name, setName] = useState('');
const [age, setAge] = useState(0);
```

- Use the previous state value if the new state depends on it:

```jsx

setCount((prevCount) => prevCount + 1);
```

**❌ Don't:**

- Don't update the state directly (this will not trigger a re-render):

```jsx

// Incorrect
count = count + 1;

// Correct
setCount(count + 1);

```

- Don't call `useState` conditionally:

```jsx

// Incorrect
if (isLoggedIn) {
  const [user, setUser] = useState(null);
}

```

State hooks must always be called at the top level of the component.

## Lifting the State

State has to be “lifted when state based data needs to be shared between two or more sibling components. This is because in React, data can be passed down from Parent to Children but data cannot be passed upwards from Child to Parent and cannot be passed sideways between two sibling components. 

### How to Lift State?

Step 1: Declare a state variable in the common parent component of the sibling. The parent component can be visualised using the React Dev tools. 

Step 2: Create all helper functions in the parent component, which should include all functions which update the state of the variable to be controlled in the parent component.

Step 3: Call the sibling components in the parent component and pass the state variable to the siblings

Step 4: The function definition of each of the sibling function must have a “prop” which can be used to receive the state managed variable as listed in the code below. 

 

**Code Structure**

In your code, you have several components: **`FriendList`**, **`Friend`**, **`FormAddFriend`**, **`FormSplitBill`**, and the main **`App`** component. Initially, **`FriendList`** and **`FormAddFriend`** need to interact with the list of friends, but they are sibling components. To enable this interaction, the state of the friends' list is "lifted" to their closest common ancestor, which is the **`App`** component.

**Explanation of Lifting the State Up**

1. **State Definition in Common Ancestor (`App`):**
    
    The **`App`** component maintains the state of the friends' list:
    
    ```jsx
    
    const [friends, setFriends] = useState(initialFriends);
    ```
    
    This state is the "source of truth" for the list of friends across the application.
    
2. **Passing State and Handlers to Children:**
    
    The **`friends`** state and the method to update it (**`setFriends`**) are passed down to **`FriendList`** and **`FormAddFriend`** as props.
    
    - To **`FriendList`** to display the list of friends.
    - To **`FormAddFriend`** to allow adding a new friend to the list.
    
    ```jsx
    
    <FriendList friends={friends} />
    <FormAddFriend onAddFriend={handleAddFriend} />
    
    ```
    
3. **Handling State Updates in Child Components:**
    
    In **`FormAddFriend`**, when a new friend is added, it calls **`onAddFriend`**, a function passed down from **`App`**. This function updates the **`friends`** state in **`App`**.
    
    ```jsx
    
    function handleAddFriend(friend){
      setFriends((prevFriends) => [...prevFriends, friend]);
    }
    
    ```
    
4. **State Changes Reflect Across Components:**
    
    Since **`FriendList`** also receives the **`friends`** state from **`App`**, any changes made in **`FormAddFriend`** (like adding a new friend) will be reflected in **`FriendList`**. Both components stay synchronized with the current list of friends.
    
5. **Benefits of Lifting the State Up:**
    - **Centralized State Management:** The state is managed in a single location (**`App`**), making it easier to handle data flow and debug.
    - **Data Consistency:** All children components that depend on this state will always render consistent data.
    - **Reusability and Separation of Concerns:** Components like **`FriendList`** and **`FormAddFriend`** don’t manage the state directly but work with it through props, making them more reusable and focused on their specific UI logic.

**Summary**

By lifting the state up to the **`App`** component, the code ensures that **`FriendList`** and **`FormAddFriend`** can interact with and reflect the same friends' list data, even though they are sibling components. This pattern is a fundamental concept in React for managing shared state across multiple components.

## Forms in React.js

Think about how forms work in a typical, non-React environment. A user types some data into a form’s input fields, and the server doesn’t know about it. The server remains clueless until the user hits a “submit” button, which sends all of the form’s data over to the server simultaneously.

In React, as in many other JavaScript environments, this is not the best way of doing things.

The problem is the period of time during which a form thinks that a user has typed one thing, but the server thinks that the user has typed a different thing. What if, during that time, a *third* part of the website needs to know what a user has typed? It could ask the form or the server and get two different answers. In a complex JavaScript app with many moving, interdependent parts, this kind of conflict can easily lead to problems.

In a React form, you want the server to know about every new character or deletion, *as soon as it happens*. That way, your screen will always be in sync with the rest of your application.

In a regular HTML form, the state of the form is typically managed by the browser. It doesn’t update the server until the user hits *submit*.

Things work a bit differently in React. In a React form, the state of the form can be managed by the component, and updates are triggered by the `onChange` event. When the user interacts with an input, such as entering or deleting any characters, the `onChange` event fires and updates the component state.

This allows the component to immediately reflect any changes made by the user and update the view accordingly.

To ensure that user input from an `<input/>` element is captured and updated in a React.js application using the `useState` hook, you need to create a controlled component. This involves managing the input's state within the component and updating it in response to user actions. The key functionalities involved are:

1. Event Handler Function
2. **`onChange` Event**
3. **`value` Attribute in `<input/>`**

Here's a step-by-step guide on how to implement this:

### **1. Initialise State with `useState` Hook**

First, import the `useState` hook from React and initialize a state variable to hold the input's value.

```jsx

import React, { useState } from 'react';

const MyComponent = () => {
  // Initialize state variable 'inputValue' with an empty string
  const [inputValue, setInputValue] = useState('');

  // ... rest of the component
};

```

- **Explanation**: The `useState` hook creates a state variable (`inputValue`) and a function to update it (`setInputValue`). The initial value is set to an empty string.

---

### **2. Create an Event Handler Function**

Define a function that will handle changes to the input field.

```jsx

const handleInputChange = (event) => {
  setInputValue(event.target.value);
};

```

- **Explanation**: The `handleInputChange` function takes an event object as an argument. It uses `event.target.value` to get the current value of the input field and updates the state using `setInputValue`.

---

### **3. Attach the `onChange` Event**

Use the `onChange` event on the `<input/>` element to trigger the event handler function whenever the input's value changes.

```jsx

<input type="text" onChange={handleInputChange} />

```

- **Explanation**: The `onChange` event listens for any changes in the input field. When the user types or deletes text, the `handleInputChange` function is called.

---

### **4. Set the `value` Attribute of the Input Element**

Assign the state variable to the `value` attribute of the `<input/>` element to make it a controlled component.

```jsx

<input type="text" value={inputValue} onChange={handleInputChange} />

```

- **Explanation**: By setting the `value` attribute to `inputValue`, you ensure that the input field always displays the current state. This keeps the UI and state in sync.

---

### **Complete Example**

Putting it all together, your component should look like this:

```jsx

import React, { useState } from 'react';

const MyComponent = () => {
  const [inputValue, setInputValue] = useState('');

  // Event handler function
  const handleInputChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      {/* Input element with 'value' and 'onChange' */}
      <input type="text" value={inputValue} onChange={handleInputChange} />

      {/* Displaying the input value */}
      <p>Current Input: {inputValue}</p>
    </div>
  );
};

export default MyComponent;

```

## Controlled vs Un-Controlled components

In React.js, form inputs can be managed in two primary ways: **controlled** and **uncontrolled** components. Understanding the differences between them is crucial for effective state management and predictable UI behavior. 

An *uncontrolled component* is a component that maintains its own internal state. A *controlled component* is a component that does not maintain any internal state. Since a controlled component has no state, it must be *controlled* by someone else.

Think of a typical `<input type='text' />` element. It appears on the screen as a text box. If you need to know what text is currently in the box, then you can ask the `<input>` element, possibly with some code like this:

```jsx
let input = document.querySelector('input[type="text"]');

let typedText = input.value; // input.value will be equal to whatever text is currently in the text box.

```

The important thing here is that the `<input>` element *keeps track of* its own text. You can access what its text is at any time.

The fact that `<input>` keeps track of information makes it an *uncontrolled component*. It maintains its own internal state by remembering data about itself.

A controlled component, on the other hand, has no memory. If you ask it for information about itself, then it will have to get that information through `props`. Most React components are *controlled*.

In React, when you give an `<input>` element a `value` attribute, then something strange happens: the `<input>` element *becomes controlled*. It stops using its internal storage. This is a more “React” way of doing things.

---

## **Controlled Components**

A **controlled component** is a form element (like `<input>`, `<textarea>`, or `<select>`) whose value is controlled by React state. In this setup, the form data is handled by the component's state, making React the single source of truth for the form's data.

### **Characteristics of Controlled Components**

1. **State Management**: The component's state (`useState` or `this.state`) holds the current value of the form input.
2. **Two-Way Data Binding**: The input's `value` is set from the state, and any changes in the input are propagated back to the state via event handlers.
3. **Event Handling**: User interactions trigger events (like `onChange`), which are handled by functions that update the state.
4. **Predictability**: Since the state controls the input value, the component's behavior is more predictable and easier to debug.

### **Example of a Controlled Component**

```jsx

import React, { useState } from 'react';

const ControlledInput = () => {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      <input type="text" value={inputValue} onChange={handleChange} />
      <p>Input Value: {inputValue}</p>
    </div>
  );
};

export default ControlledInput;

```

- **Explanation**: Here, the `inputValue` state holds the current value of the input field. The `handleChange` function updates the state whenever the user types, ensuring the UI reflects the state accurately.

---

## **Uncontrolled Components**

An **uncontrolled component** is a form element that maintains its own internal state. Instead of controlling the form data through React state, you use references to access the input's current value directly from the DOM when needed.

### **Characteristics of Uncontrolled Components**

1. **DOM-Based State**: The input's state is managed by the DOM, not by React.
2. **Refs Usage**: You use `React.createRef()` or `useRef()` to create a reference to the DOM element.
3. **Event Handling**: Less reliance on `onChange` handlers for every input; you typically retrieve the value only when needed (e.g., on form submission).
4. **Simplicity**: Can result in less boilerplate code for simple forms but may sacrifice control and predictability.

### **Example of an Uncontrolled Component**

```jsx

import React, { useRef } from 'react';

const UncontrolledInput = () => {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    alert(`Input Value: ${inputRef.current.value}`);
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </div>
  );
};

export default UncontrolledInput;

```

- **Explanation**: The `inputRef` is a reference to the DOM input element. When the button is clicked, `handleSubmit` accesses the current value directly from the DOM.

---

## **Key Differences Between Controlled and Uncontrolled Components**

### **1. Data Handling**

- **Controlled Components**: Data is stored in the component's state. React controls the input's value.
- **Uncontrolled Components**: Data is stored in the DOM. React does not control the input's value.

### **2. Accessing Input Values**

- **Controlled Components**: Access the input value through the component's state (`state` or `useState`).
- **Uncontrolled Components**: Access the input value using refs (`useRef` or `createRef`) to read the value from the DOM.

### **3. Event Handling**

- **Controlled Components**: Require event handlers (like `onChange`) to update the state with every user input.
- **Uncontrolled Components**: Do not require event handlers for every input field; values are read when needed.

### **4. Validation and Formatting**

- **Controlled Components**: Easier to validate and format input data in real-time since you have direct control over the state.
- **Uncontrolled Components**: Validation is typically done when the value is retrieved, not in real-time.

### **5. Predictability and Debugging**

- **Controlled Components**: More predictable behavior since the React state is the single source of truth.
- **Uncontrolled Components**: Less predictable because the state is managed by the DOM, which can make debugging more challenging.

### **6. Code Complexity**

- **Controlled Components**: May require more boilerplate code due to state management and event handlers.
- **Uncontrolled Components**: Can be simpler for small forms or when you don't need real-time validation.

---

## **When to Use Controlled Components**

- **Form Validation**: When you need to validate user input as it's entered.
- **Dynamic Inputs**: When the input values affect other parts of the UI or need to trigger side effects.
- **Predictable State**: When maintaining predictable and centralized state is crucial for the application.

## **When to Use Uncontrolled Components**

- **Simple Forms**: For simple forms where real-time validation and state management are unnecessary.
- **Third-Party Libraries**: When integrating with libraries that require direct access to DOM elements.
- **Performance Optimisation**: In cases where re-rendering on every input change may cause performance issues.

# **What are Uncontrolled Components?**

**Learn about uncontrolled components: what they are and when to use them.**

So, you’re building a React application and you need to get some input from your users. You reach for an `<input>` element and go with the recommended approach of making a [controlled component](https://react.dev/reference/react-dom/components#form-components). But did you know that you can also create *uncontrolled components*?

This article will cover what uncontrolled components are, how they are similar to and different from controlled components, and when to use them in your React applications.

### **Controlled Components**

Let’s begin with a quick recap on controlled components. Remember, while form elements (`<input>`, `<textarea>`, etc…) are capable of managing their own internal state, in React, we typically prefer to maintain any mutable state values within the state property of our components.

To gain control over a form element’s internal state, we can provide a `value` attribute on the `<input>` element and assign a component state variable to it.

Coding question

## **Questions**

Consider this example of a controlled component for receiving phone numbers. Take note of how the internal state of the form (`number`) is created with `useState` and is updated in the `handleChange` function.

### **Code**

```jsx
import ReactDOM from "react-dom";
import React, { useState } from "react";

function PhoneNumberForm() {
  const [number, setNumber] = useState(0);

  const handleChange = (e) => {
    const newNumber = e.target.value;

    if (!Number.isNaN(Number(newNumber)) && newNumber.length <= 10) {
      setNumber(e.target.value);
    }
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Sending confirmation code to ${number}.`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Phone Number:
        <input type="tel" value={number} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}

export default PhoneNumberForm;
```

In this example, the `PhoneNumberForm` component controls the `<input>` element by assigning its own `number` state value to the `value` attribute. Doing this essentially turns off the form element’s default behavior of controlling its own state. To keep the `number` state value up to date, an `onChange` handler is registered, which can set the state value each time a change is detected.

With this approach, we are set up to perform immediate validation on every change to the form. In this case, we can make sure that only numbers are used in the form and that the form doesn’t exceed 10 characters in length (see `handleChange()`).

Though change-by-change validation like this is common enough, in some cases, we may only care about a form’s value after it has been submitted. In these scenarios, keeping the input value up to date on every change can feel like overkill. This is where uncontrolled components come into play.

### **Uncontrolled Components**

An uncontrolled component is a form element that maintains its own state in the DOM. Rather than using a component’s own state value to maintain that element’s input value and updating it on every change, we can instead use a [ref](https://react.dev/learn/referencing-values-with-refs) to retrieve the value directly from the DOM only when we need it.

According to React:

> Refs provide a way to access DOM nodes or React elements created in the render method.
> 

To create an uncontrolled component, we begin by creating a ref using [the `useRef()` method](https://react.dev/reference/react/useRef). This method returns an object with a `.current` property that refers to the DOM node it is bound to. This ref object is bound to a form element using the `ref` attribute, and whenever the value of that form element needs to be retrieved, simply refer back to the ref object’s `.current` property.

Let’s take a look at the same `PhoneNumberForm` component, now implemented as an uncontrolled component using a ref. Notice how we are still validating the incoming phone number but only after the form has been submitted.

### **Code**

```jsx
import ReactDOM from "react-dom";
import React from "react";

function PhoneNumberForm() {
  const numberRef = React.useRef();

  const handleSubmit = (e) => {
    e.preventDefault(); 
    
    const number = numberRef.current.value;

    if (Number.isNaN(Number(number))) {
      alert('Error: Only numbers allowed.')
    }
    else if (number.length >= 10) {
      alert('Error: Number length exceeded 10 digits.')
    }
    else {
      alert(`Sending confirmation code to ${number}.`);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Phone Number:
        <input type="tel" ref={numberRef} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}

export default PhoneNumberForm;
```

In this example, the `numberRef` object is created and then bound to the `<input>` form element.

```jsx
const numberRef = React.useRef();

// ...

<input type="text" ref={numberRef} />
```

In `handleSubmit`, the value of that form element can be retrieved from the DOM node stored in `numberRef.current`.

```jsx
const number = numberRef.current.value;
```

> Note: <input> DOM nodes are instances of HTMLInputElement, so their values can be retrieved using the .value property. Other form elements may use different properties to access their input values.
> 

### **When Should You Use An Uncontrolled Component?**

In some ways, creating uncontrolled components is faster and easier than creating controlled components. However, given their departure from the React pattern of storing mutable data in a component’s state, controlled components are still recommended for most scenarios.

There is one situation in which uncontrolled components must always be used: `<input>` form elements with the `type="file"` attribute. The value for this type of `<input>` form element can only be set by a user, and not programmatically, and therefore the only way to retrieve this value is through a ref.

Consider this program that accepts a file to be uploaded via the `<input type='file'>` element and prints out the size of that file in kilobytes.

```jsx
import ReactDOM from "react-dom";
import React, { useState } from "react";

function PhoneNumberForm() {
  const fileRef = React.useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    
    const size = fileRef.current.files[0].size;
    alert(
      `This file is ${size} bytes`
    );
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        <input type="file" ref={fileRef} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}

export default PhoneNumberForm;
```

In this example, we again create a ref using the `React.createRef()` method and then bind it to the `<input>` form element. The uploaded file is stored in the array-like [`FileList`](https://developer.mozilla.org/en-US/docs/Web/API/FileList) returned by `fileRef.current.files` and the `.size` property of this file is accessed when the user submits the form.

# useEffect hook

The `useEffect` hook is one of the most powerful and commonly used hooks in React.js. It helps you manage side effects in functional components. Let’s break it down step-by-step, using intuitive analogies, technical details, and code examples.

---

### 🧠 **What is a Side Effect?**

A **side effect** is anything that affects the outside world or performs some operation that isn’t purely rendering the UI.

Imagine your React component is a **to-do list**. Just like writing tasks on the list doesn’t affect anything outside of the paper, rendering UI doesn’t produce side effects. But if you need to **send a reminder email** or **save tasks to a server**, those actions affect things outside your component—those are side effects.

Examples of side effects in React:

1. **Fetching data from an API.**
2. **Updating the document title.**
3. **Subscribing to events (like WebSocket messages or timers).**
4. **Manually interacting with the DOM.**

---

### 🚀 **Why Use `useEffect`?**

Before React hooks, side effects in React were managed in **class components** using lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`. `useEffect` lets you handle side effects in **functional components** in a clean and unified way.

---

### ⚙️ **How Does `useEffect` Work?**

The `useEffect` hook allows you to run side-effect code in response to changes in your component. The basic syntax is:

```jsx
useEffect(() => {
  // Side effect code here
});

```

The hook takes a **function** as its first argument. This function will run after every render by default.

Here’s a more complete example:

```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    // This runs after the component mounts
    const interval = setInterval(() => {
      setSeconds((prev) => prev + 1);
    }, 1000);

    // Cleanup function: runs when the component unmounts
    return () => {
      clearInterval(interval);
    };
  }, []); // The empty array means this runs only once when the component mounts

  return <div>Timer: {seconds} seconds</div>;
}

export default Timer;

```

---

### 📦 **Breaking Down the Example**

1. **State Initialization**:
    
    ```jsx
    const [seconds, setSeconds] = useState(0);
    
    ```
    
    - We use `useState` to create a piece of state (`seconds`) that starts at `0`.
2. **Effect Setup**:
    
    ```jsx
    useEffect(() => {
      const interval = setInterval(() => {
        setSeconds((prev) => prev + 1);
      }, 1000);
    
      return () => {
        clearInterval(interval);
      };
    }, []);
    
    ```
    
    - The function inside `useEffect` sets up an interval that increments `seconds` by 1 every second.
    - The **cleanup function** (`return () => clearInterval(interval);`) ensures the interval is cleared when the component unmounts, preventing memory leaks.
3. **Dependency Array**:
    
    ```jsx
    [], // Empty array means this effect only runs once when the component mounts
    
    ```
    
    - The **dependency array** controls when the effect runs. In this case, the empty array tells React to only run the effect **once** (when the component mounts).

---

### 📊 **Key Concepts of `useEffect`**

1. **Without Dependency Array**:
    
    ```jsx
    useEffect(() => {
      console.log('Effect ran');
    });
    
    ```
    
    - This runs **after every render** (initial render and updates).
2. **With Dependency Array**:
    
    ```jsx
    useEffect(() => {
      console.log('Effect ran');
    }, [count]);
    
    ```
    
    - This runs **only when `count` changes**.
3. **Cleanup Function**:
    
    ```jsx
    useEffect(() => {
      const timer = setTimeout(() => console.log('Hello'), 1000);
      return () => clearTimeout(timer);
    }, []);
    
    ```
    
    - The cleanup function is executed when the component unmounts or before the effect runs again (if dependencies change). This is useful for cleaning up subscriptions, intervals, or timers.

---

### 🛠️ **Practical Examples of `useEffect`**

1. **Fetching Data from an API**:
    
    ```jsx
    import React, { useState, useEffect } from 'react';
    
    function FetchData() {
      const [data, setData] = useState(null);
    
      useEffect(() => {
        fetch('https://jsonplaceholder.typicode.com/posts/1')
          .then((response) => response.json())
          .then((data) => setData(data));
      }, []); // Empty array means it fetches data once when the component mounts
    
      return <div>{data ? data.title : 'Loading...'}</div>;
    }
    
    export default FetchData;
    
    ```
    
2. **Updating the Document Title**:
    
    ```jsx
    import React, { useState, useEffect } from 'react';
    
    function TitleChanger() {
      const [count, setCount] = useState(0);
    
      useEffect(() => {
        document.title = `Count: ${count}`;
      }, [count]); // Update the title whenever `count` changes
    
      return <button onClick={() => setCount(count + 1)}>Increment</button>;
    }
    
    export default TitleChanger;
    
    ```
    

---

### 🧩 **Summary**

- **`useEffect`** is a hook for managing **side effects** in functional components.
- It replaces the need for lifecycle methods (`componentDidMount`, `componentDidUpdate`, `componentWillUnmount`) in class components.
- **Cleanup functions** help avoid memory leaks by cleaning up after the effect.
- The **dependency array** controls when the effect runs:
    - No array: runs after every render.
    - Empty array `[]`: runs once when the component mounts.
    - Array with values `[value1, value2]`: runs when any of the listed values change.

---

## useReducer Hook

![Screenshot 2025-01-17 at 1.42.54 PM.png](React%202088e3c5ec084e0db04fccaefddff2e8/Screenshot_2025-01-17_at_1.42.54_PM.png)

# React Router

React Router is a library for managing navigation and rendering different views in a React application. Imagine you're organising a multi-room museum where visitors need directions to specific exhibits. React Router acts like a guide, ensuring visitors (users) get to the correct room (page/component) based on where they want to go.

Let's break this down step by step with explanations and code examples.

---

### Key Concepts of React Router

### 1. **Routes (Rooms in the Museum)**

Routes define where a user can go in your app. Each route corresponds to a path in the URL and renders a specific React component.

### 2. **Router (The Museum Map)**

The `BrowserRouter` or `HashRouter` acts as the top-level container that tracks the user's location (URL) and coordinates which "room" (component) should be shown.

### 3. **Links (Signposts)**

`Link` components are like signposts in the museum, guiding users to different rooms without reloading the entire museum (page).

---

### Example 1: Basic Routing

Here’s a simple example of React Router in action.

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';

const Home = () => <h1>Welcome to the Home Page</h1>;
const About = () => <h1>About Us</h1>;
const Contact = () => <h1>Contact Us</h1>;

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/about">About</Link></li>
          <li><Link to="/contact">Contact</Link></li>
        </ul>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
};

export default App;

```

---

### How This Works:

1. **`BrowserRouter`:** Wraps the app to monitor the URL changes.
2. **`Routes` and `Route`:** Define what component to render based on the URL.
    - `path="/"` renders the `Home` component when the user visits `/`.
    - `path="/about"` renders the `About` component for `/about`.
3. **`Link`:** Provides navigation without reloading the page.

---

### Analogy:

Imagine `Router` is the museum guidebook, `Routes` are the sections of the book mapping paths to rooms, and `Link` components are arrows on the floor pointing you to the next exhibit. The guidebook ensures you always find the right exhibit without leaving the museum.

---

### Example 2: Using Parameters

What if a museum room (route) has variable content? For example, a user might want details about a specific exhibit (`/exhibit/:id`).

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link, useParams } from 'react-router-dom';

const Exhibit = () => {
  const { id } = useParams();
  return <h1>Details about Exhibit {id}</h1>;
};

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li><Link to="/exhibit/1">Exhibit 1</Link></li>
          <li><Link to="/exhibit/2">Exhibit 2</Link></li>
        </ul>
      </nav>
      <Routes>
        <Route path="/exhibit/:id" element={<Exhibit />} />
      </Routes>
    </Router>
  );
};

export default App;

```

---

### How This Works:

1. **Dynamic Path (`/exhibit/:id`):**
    - The `:id` is a route parameter that acts as a placeholder for the specific value (e.g., `1` or `2`).
2. **`useParams`:**
    - A hook provided by React Router to access route parameters like `id`.

---

### Example 3: Nested Routes

Sometimes, you need sub-rooms inside a main room (e.g., `/exhibit/:id/details`).

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link, Outlet } from 'react-router-dom';

const Exhibit = () => {
  return (
    <div>
      <h1>Exhibit</h1>
      <nav>
        <ul>
          <li><Link to="details">Details</Link></li>
        </ul>
      </nav>
      <Outlet />
    </div>
  );
};

const ExhibitDetails = () => <h1>Exhibit Details</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/exhibit/:id" element={<Exhibit />}>
          <Route path="details" element={<ExhibitDetails />} />
        </Route>
      </Routes>
    </Router>
  );
};

export default App;

```

---

### How This Works:

1. **`Outlet`:**
    - Acts as a placeholder for rendering nested routes.
2. **Nested Route:**
    - `/exhibit/:id/details` renders the `ExhibitDetails` component within the `Exhibit` component.

---

### Advanced Features:

1. **Redirects:**
If you want to automatically guide users to a specific route, use `<Navigate>`.
    
    ```jsx
    
    import { Navigate } from 'react-router-dom';
    
    const App = () => {
      return (
        <Routes>
          <Route path="/" element={<Navigate to="/home" />} />
        </Routes>
      );
    };
    
    ```
    
2. **Protected Routes:**
Control access to certain routes based on user authentication.
    
    ```jsx
    
    const ProtectedRoute = ({ isAuthenticated, children }) => {
      return isAuthenticated ? children : <Navigate to="/login" />;
    };
    
    <Route path="/dashboard" element={<ProtectedRoute isAuthenticated={true}><Dashboard /></ProtectedRoute>} />
    ```
    

---

### Recap:

- **Router:** Keeps track of URL and matches it to a route.
- **Routes and Route:** Maps paths to components.
- **Link:** Navigates between routes **without a full page reload.**
- **useParams:** Fetches dynamic parameters from the URL.
- **Outlet:** Enables nested routes.

**Q. React router provides <Routes>, <Route> and <Link> methods as part of the 'react-router-dom'. Now, I am not clear as to what is the difference between the usage of <Route> and <Link>. I see in code examples that <Link> is being used like anchor tag <a> in HTML to create hyperlinks in UI, and attributes like 'to' can be used to specify the path in the App. So, then why define a separate <Route> to specify the component to be rendered for React? Is the path specified in the app not enough to direct the app navigation and render the required component?**

### **Purpose of `<Route>` and `<Link>`**

1. **`<Route>`**
    - Used to **define the mapping** between a URL path and the component that should be rendered when the application is at that path.
    - Acts as the **router configuration** of your app.
    - Specifies "What component should be displayed for a particular path?"
    
    Example:
    
    ```jsx
    
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
    </Routes>
    ```
    
    - When the URL is `/`, the `Home` component is rendered.
    - When the URL is `/about`, the `About` component is rendered.
2. **`<Link>`**
    - Used to **navigate** between different routes defined in your application.
    - Replaces the traditional HTML `<a>` tag for client-side navigation in React apps.
    - Updates the browser's address bar **without refreshing the page**.
    - Works in tandem with the `<Route>` configuration to navigate the user to the correct component.
    
    Example:
    
    ```jsx
    
    <nav>
      <Link to="/">Home</Link><Link to="/about">About</Link>
    </nav>
    ```
    
    - Clicking the "Home" link updates the URL to `/` and renders the `Home` component.
    - Clicking the "About" link updates the URL to `/about` and renders the `About` component.

---

### **Why Define a Separate `<Route>`?**

The **path in `<Link>` alone is not enough** to make the app render a specific component. Here’s why:

1. **`<Link>` is only for navigation:**
    - It changes the URL when clicked, but it does not dictate what should be rendered for that URL.
    - The app still needs to know what component corresponds to a specific URL. That’s where `<Route>` comes in.
2. **Routing Logic with `<Route>`:**
    - `<Route>` tells React Router, "When the URL matches this path, render this component."
    - Without `<Route>`, the app wouldn’t know what to display for a given path.
3. **Separation of Concerns:**
    - `<Route>` is for defining the routing logic.
    - `<Link>` is for enabling navigation within your app.

---

### **How They Work Together**

Think of it as a combination of **declaration** (`<Route>`) and **interaction** (`<Link>`):

1. `<Route>` declares which component to render for a specific path.
2. `<Link>` triggers navigation to a specific path, which in turn causes React Router to match the path and render the associated component as per the `<Route>` configuration.

Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

function Home() {
  return <h1>Welcome to the Home Page</h1>;
}

function About() {
  return <h1>About Us</h1>;
}

export default App;
```

1. When you click on `<Link to="/">Home</Link>`, it navigates to `/` and the `<Route path="/" element={<Home />} />` ensures the `Home` component is displayed.
2. Similarly, `<Link to="/about">About</Link>` navigates to `/about`, and the `<Route path="/about" element={<About />} />` renders the `About` component.

---

### **Why Not Use Only `<a>` Tags?**

In React Router:

- `<a>` triggers a full page reload, losing the state of your React app.
- `<Link>` performs navigation without a page reload, preserving the single-page application (SPA) behavior.

---

### Summary

- `<Route>`: Defines the **routing logic** (which component to render for a path).
- `<Link>`: Provides **navigation** between the routes without reloading the page.
- They work together to create a smooth client-side routing experience in React apps.

## Using <NavLink>

The `<NavLink>` component in `react-router-dom` is a specialized version of the `<Link>` component. It allows you to create navigational links while also **styling or applying specific classes to the link** when it matches the current URL.

Think of `<NavLink>` as a signpost that not only points to a location (like `<Link>` does) but also **lights up or changes appearance** when you’re currently at that location.

---

### Key Features of `<NavLink>`:

1. **Active Link Highlighting:**
    - Automatically adds an `active` class to the link when its `to` path matches the current URL.
2. **Custom Styling/Classes:**
    - You can customize the styling or classes applied to the link based on whether it’s active.
3. **Exact Matching:**
    - Control whether the link is considered active for partial matches or only exact matches.

---

### Basic Example of `<NavLink>`

Here’s how to use `<NavLink>`:

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, NavLink } from 'react-router-dom';

const Home = () => <h1>Home Page</h1>;
const About = () => <h1>About Page</h1>;

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <NavLink to="/" end>
              Home
            </NavLink>
          </li>
          <li>
            <NavLink to="/about">
              About
            </NavLink>
          </li>
        </ul>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};

export default App;
```

---

### How This Works:

1. **`<NavLink>`:**
    - Creates a navigational link, similar to `<Link>`.
2. **Active Highlighting:**
    - The link corresponding to the current route automatically gets an `active` class.
    - For example, when you visit `/about`, the "About" link will have the `active` class applied.
3. **`end` Prop:**
    - Ensures that the "Home" link is only active when the URL is exactly `/`. Without `end`, the "Home" link would also match paths like `/about`.

---

### Custom Styling with `<NavLink>`

You can style the active link using CSS or by dynamically applying styles via a function.

### Example with CSS:

```css

/* styles.css */
.active {
  font-weight: bold;
  color: red;
}

```

### Code Example:

```jsx

<NavLink to="/" className={({ isActive }) => (isActive ? 'active' : '')}>
  Home
</NavLink>
```

### Explanation:

- The `className` prop accepts a function that returns a string based on the `isActive` property.
- If the link is active, the `active` class is applied.

---

### Styling Inline with the `style` Prop

You can also apply inline styles conditionally:

### Code Example:

```jsx

<NavLink
  to="/about"
  style={({ isActive }) => ({
    fontWeight: isActive ? 'bold' : 'normal',
    color: isActive ? 'green' : 'black',
  })}
>
  About
</NavLink>
```

### Explanation:

- The `style` prop accepts a function that dynamically generates styles based on whether the link is active.

---

### Customising Active Class Name

If you want a custom class instead of the default `active` class:

### Code Example:

```jsx

<NavLink to="/" className={({ isActive }) => (isActive ? 'my-active-class' : '')}>
  Home
</NavLink>
```

---

### Example with Nested Routes

Here’s an example using `<NavLink>` with nested routes:

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, NavLink } from 'react-router-dom';

const Dashboard = () => <h1>Dashboard</h1>;
const Settings = () => <h1>Settings</h1>;

const App = () => {
  return (
    <Router>
      <nav>
        <NavLink to="/dashboard">Dashboard</NavLink>
        <NavLink to="/settings">Settings</NavLink>
      </nav>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />} />
        <Route path="/settings" element={<Settings />} />
      </Routes>
    </Router>
  );
};

export default App;
```

---

### Use Case: Navigation Bars

### Code Example:

```jsx

<nav>
  <NavLink
    to="/"
    style={({ isActive }) => ({
      textDecoration: isActive ? 'underline' : 'none',
      color: isActive ? 'blue' : 'gray',
    })}
  >
    Home
  </NavLink><NavLink
    to="/about"
    style={({ isActive }) => ({
      textDecoration: isActive ? 'underline' : 'none',
      color: isActive ? 'blue' : 'gray',
    })}
  >
    About
  </NavLink>
</nav>
```

---

### Key Props of `<NavLink>`:

1. **`to`:**
    - Specifies the route path the link navigates to.
2. **`end`:**
    - Ensures the link is active only when the URL matches exactly.
3. **`className`:**
    - Dynamically applies CSS classes based on whether the link is active.
4. **`style`:**
    - Dynamically applies inline styles based on the active state.
5. **`isActive`:**
    - A boolean provided to `className` or `style` functions to indicate whether the link is active.

---

### Recap:

- `<NavLink>` is a `<Link>` with built-in support for styling active links.
- It adds an `active` class by default, but you can customise it with the `className` or `style` props.
- Use it to highlight the currently active page in navigation menus.

## `useNavigate` in React Router

The `useNavigate` hook in `react-router-dom` allows you to programmatically navigate users to different routes in your React app. Instead of relying solely on `<Link>` or `<NavLink>` for navigation, `useNavigate` gives you the power to navigate dynamically in response to events like button clicks, API responses, or conditional logic.

---

### Key Features of `useNavigate`

1. **Programmatic Navigation:**
    - Navigate to different routes without requiring user interaction with a link.
2. **Dynamic Path Construction:**
    - Easily construct routes with parameters, query strings, or conditional logic.
3. **Navigation Control:**
    - Navigate backward or forward in the browser history stack.
4. **State Passing:**
    - Pass custom state data to the target route.

---

### Example 1: Basic Navigation

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Home = () => {
  const navigate = useNavigate();

  const goToAbout = () => {
    navigate('/about');
  };

  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={goToAbout}>Go to About</button>
    </div>
  );
};

const About = () => <h1>About Page</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};

export default App;

```

---

### How This Works:

1. **`useNavigate`:**
    - Provides the `navigate` function to control routing programmatically.
2. **`navigate('/about')`:**
    - Changes the route to `/about` and renders the `About` component.

---

### Example 2: Passing State While Navigating

The `navigate` function allows you to pass additional state data to the target route, which can be accessed using the `useLocation` hook.

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate, useLocation } from 'react-router-dom';

const Home = () => {
  const navigate = useNavigate();

  const goToAboutWithMessage = () => {
    navigate('/about', { state: { message: 'Hello from Home!' } });
  };

  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={goToAboutWithMessage}>Go to About with Message</button>
    </div>
  );
};

const About = () => {
  const location = useLocation();
  const state = location.state || {};

  return (
    <div>
      <h1>About Page</h1>
      <p><strong>Message:</strong> {state.message || 'No message passed'}</p>
    </div>
  );
};

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};

export default App;
```

---

### How This Works:

1. **`state` Property:**
    - Custom state (`{ message: 'Hello from Home!' }`) is passed when navigating to `/about`.
2. **`useLocation`:**
    - Retrieves the state data passed during navigation.
3. **Dynamic Rendering:**
    - The `About` page displays the passed message, enabling dynamic, contextual content.

---

### Example 3: Navigating Backward and Forward

The `navigate` function can also emulate the browser’s back and forward buttons by passing relative values.

### Code Example:

```jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Page1 = () => {
  const navigate = useNavigate();
  return (
    <div>
      <h1>Page 1</h1>
      <button onClick={() => navigate('/page2')}>Go to Page 2</button>
    </div>
  );
};

const Page2 = () => {
  const navigate = useNavigate();
  return (
    <div>
      <h1>Page 2</h1>
      <button onClick={() => navigate(-1)}>Go Back</button>
      <button onClick={() => navigate(1)}>Go Forward</button>
    </div>
  );
};

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/page1" element={<Page1 />} />
        <Route path="/page2" element={<Page2 />} />
      </Routes>
    </Router>
  );
};

export default App;
```

---

### How This Works:

1. **`navigate(-1)`:**
    - Moves backward one step in the browser’s history stack.
2. **`navigate(1)`:**
    - Moves forward one step in the browser’s history stack.

---

### Example 4: Conditional Navigation

You can use `useNavigate` to perform navigation based on conditions, such as user authentication or form validation.

### Code Example:

```jsx

import React, { useState } from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Login = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const navigate = useNavigate();

  const handleLogin = () => {
    setIsLoggedIn(true);
    navigate('/dashboard'); // Navigate to dashboard after login
  };

  return (
    <div>
      <h1>Login Page</h1>
      <button onClick={handleLogin}>Log In</button>
    </div>
  );
};

const Dashboard = () => <h1>Dashboard</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/dashboard" element={<Dashboard />} />
      </Routes>
    </Router>
  );
};

export default App;
```

---

### How This Works:

1. **Conditional Navigation:**
    - After clicking "Log In," the app navigates to `/dashboard` if the user is logged in.
2. **Dynamic Navigation Logic:**
    - You can control routing based on custom logic like authentication, validation, or permissions.

---

### Key Features of `useNavigate`

| Feature | Example Usage |
| --- | --- |
| Navigate to a path | `navigate('/path')` |
| Pass state with navigation | `navigate('/path', { state: {...} })` |
| Navigate backward/forward | `navigate(-1)` or `navigate(1)` |
| Replace current history | `navigate('/path', { replace: true })` |

---

### When to Use `useNavigate`?

1. **Event-Based Navigation:**
    - Trigger route changes based on events like button clicks, form submissions, or API responses.
2. **Dynamic Routing Logic:**
    - Perform conditional navigation (e.g., redirect users after login or based on permissions).
3. **Navigation with State:**
    - Pass additional data to the destination route for contextual rendering.

## useParams() hook in React Router

In React Router, the `useParams` hook is used to access dynamic segments of the URL. These dynamic segments are defined in the route path using a colon (`:`) followed by a parameter name. For example, in a route like `/users/:userId`, `userId` is a dynamic segment that can be accessed using `useParams`.

### Key Concepts

1. **Dynamic Route Parameters**:
    - Dynamic segments in the URL allow you to create flexible routes that can match different values.
    - For example, `/users/:userId` can match `/users/1`, `/users/2`, `/users/john`, etc.
2. **`useParams` Hook**:
    - The `useParams` hook returns an object containing the key-value pairs of the dynamic segments in the current URL.
    - The keys in the object correspond to the parameter names defined in the route path.

### Example Usage

Here’s an example of how to use `useParams` in a React component:

```
import React from 'react';
import { useParams } from 'react-router-dom';

function UserProfile() {
  // Use the useParams hook to access the userId parameter
  const { userId } = useParams();

  return (
    <div>
      <h1>User Profile</h1>
      <p>User ID: {userId}</p>
    </div>);
}

export default UserProfile;
```

### Explanation

1. **Defining the Route**:
    - In your route configuration, you define a route with a dynamic segment:
        
        
        ```
        <Route path="/users/:userId" element={<UserProfile />} />
        ```
        
    - Here, `:userId` is a dynamic segment that will match any value in the URL.
2. **Accessing the Parameter**:
    - In the `UserProfile` component, you use the `useParams` hook to access the `userId` parameter.
    - The `useParams` hook returns an object where the keys are the parameter names defined in the route path, and the values are the actual values from the URL.
3. **Using the Parameter**:
    - You can then use the `userId` parameter in your component to fetch data, display information, or perform other actions based on the value.

### Advanced Usage

- **Multiple Parameters**:
    
    You can define routes with multiple dynamic segments and access all of them using `useParams`.
    

```
import React from 'react';
import { useParams } from 'react-router-dom';

function PostDetails() {
  // Use the useParams hook to access multiple parameters
  const { userId, postId } = useParams();

  return (
    <div>
      <h1>Post Details</h1>
      <p>User ID: {userId}</p>
      <p>Post ID: {postId}</p>
    </div>);
}

export default PostDetails;
```

- **Route Configuration**:
    
    Define a route with multiple dynamic segments:
    
    ```
    <Route path="/users/:userId/posts/:postId" element={<PostDetails />} />
    ```
    
- **Optional Parameters**:
    
    You can also define optional parameters by using a question mark (`?`) after the parameter name in the route path. However, this is not natively supported in React Router v6. Instead, you can use nested routes or conditional logic to handle optional parameters.
    

### Example with Optional Parameters

```
import React from 'react';
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { userId, tab } = useParams();

  return (
    <div>
      <h1>User Profile</h1>
      <p>User ID: {userId}</p>
      {tab && <p>Active Tab: {tab}</p>}
    </div>);
}

export default UserProfile;
```

- **Route Configuration**:
    
    Define a route with an optional parameter:
    
    ```
    <Route path="/users/:userId/:tab?" element={<UserProfile />} />
    ```
    

### Summary

- `useParams` is a hook provided by React Router to access dynamic segments of the URL.
- It returns an object containing the key-value pairs of the dynamic segments.
- You can define routes with dynamic segments using a colon (`:`) followed by the parameter name.
- This feature is particularly useful for creating flexible and dynamic routes in your React application.

By using `useParams`, you can easily build components that respond to changes in the URL and display content based on the dynamic segments.

### useSearchParams() hook in React Router

In React Router, `searchParams` is a feature that allows you to work with the query string in a URL. The query string is the part of the URL that comes after the `?` and contains key-value pairs, such as `?name=John&age=30`. React Router provides utilities to easily access and manipulate these query parameters.

### Key Concepts

1. **`useSearchParams` Hook**:
    - React Router (v6 and above) provides the `useSearchParams` hook, which allows you to read and update the query string in the URL.
    - It returns an array with two elements:
        - `searchParams`: An instance of `URLSearchParams` that provides methods to read the query parameters.
        - `setSearchParams`: A function to update the query string.
2. **`URLSearchParams`**:
    - This is a built-in JavaScript API that provides methods to work with query strings.
    - Common methods include:
        - `get(key)`: Retrieves the value of a specific query parameter.
        - `getAll(key)`: Retrieves all values for a specific query parameter (useful for arrays).
        - `has(key)`: Checks if a query parameter exists.
        - `set(key, value)`: Sets the value of a query parameter.
        - `append(key, value)`: Adds a new value to a query parameter.
        - `delete(key)`: Removes a query parameter.

### Example Usage

Here’s an example of how to use `useSearchParams` in a React component:

```
import React from 'react';
import { useSearchParams } from 'react-router-dom';

function UserProfile() {
  // Use the useSearchParams hook
  const [searchParams, setSearchParams] = useSearchParams();

  // Get specific query parameters
  const name = searchParams.get('name');
  const age = searchParams.get('age');

  // Function to update query parameters
  const updateQueryParams = () => {
    setSearchParams({ name: 'Jane', age: 25 });
  };

  return (
    <div>
      <h1>User Profile</h1>
      <p>Name: {name || 'Not provided'}</p>
      <p>Age: {age || 'Not provided'}</p>

      <button onClick={updateQueryParams}>Update Query Params</button>
    </div>);
}

export default UserProfile;
```

### Explanation

1. **Reading Query Parameters**:
    - `searchParams.get('name')` retrieves the value of the `name` query parameter.
    - If the parameter doesn’t exist, it returns `null`.
2. **Updating Query Parameters**:
    - `setSearchParams({ name: 'Jane', age: 25 })` updates the query string in the URL to `?name=Jane&age=25`.
    - This will also trigger a re-render of the component.
3. **Handling Missing Parameters**:
    - If a query parameter is missing, you can provide a fallback value (e.g., `name || 'Not provided'`).

### Advanced Usage

- **Multiple Values for a Key**:
    
    If your query string has multiple values for the same key (e.g., `?color=red&color=blue`), you can use `searchParams.getAll('color')` to retrieve them as an array.
    
- **Appending Query Parameters**:
    
    If you want to add a new query parameter without removing existing ones, you can use `searchParams.append('key', 'value')` before calling `setSearchParams`.
    

### Example with Multiple Values

```
import React from 'react';
import { useSearchParams } from 'react-router-dom';

function ColorFilters() {
  const [searchParams, setSearchParams] = useSearchParams();

  // Get all values for the 'color' parameter
  const colors = searchParams.getAll('color');

  // Function to add a new color
  const addColor = () => {
    searchParams.append('color', 'green');
    setSearchParams(searchParams);
  };

  return (
    <div>
      <h1>Selected Colors</h1>
      <ul>
        {colors.map((color, index) => (
          <li key={index}>{color}</li>))}
      </ul>

      <button onClick={addColor}>Add Green</button>
    </div>);
}

export default ColorFilters;
```

### Summary

- `useSearchParams` is a powerful hook for working with query strings in React Router.
- It provides an easy way to read and update query parameters in your application.
- Use `URLSearchParams` methods like `get`, `set`, `append`, and `delete` to manipulate the query string.

This feature is particularly useful for filtering, sorting, or passing state through the URL in a React application.

### Lazy Loading a Page

Lazy loading and React Suspense are techniques used to optimize the performance of React applications by loading components only when they are needed. This can significantly reduce the initial load time and improve the user experience, especially for large applications with many components.

### Key Concepts

1. **Lazy Loading**:
    - Lazy loading is a technique where you defer the loading of certain parts of your application until they are actually needed.
    - In React, this is achieved using the `React.lazy` function, which allows you to dynamically import a component.
2. **React Suspense**:
    - React Suspense is a mechanism that allows you to "suspend" the rendering of a component while it is waiting for some asynchronous operation (like loading a lazy component) to complete.
    - It provides a fallback UI (like a loading spinner) to show while the component is being loaded.

### How to Use Lazy Loading and React Suspense

### 1. **Lazy Loading with `React.lazy`**

The `React.lazy` function lets you render a dynamic import as a regular component. It takes a function that returns a `Promise` which resolves to a module with a React component.

```jsx
import React, { lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));
```

### 2. **Suspense for Fallback UI**

When you use `React.lazy`, you need to wrap the lazy component in a `Suspense` component. The `Suspense` component takes a `fallback` prop, which is a React element that will be displayed while the lazy component is being loaded.

```jsx
import React, { Suspense } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>);
}

export default App;
```

### Example Usage

Here’s a more complete example that demonstrates lazy loading and React Suspense in action:

```jsx
import React, { Suspense, lazy } from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

// Lazy load the components
const Home = lazy(() => import('./Home'));
const About = lazy(() => import('./About'));
const Contact = lazy(() => import('./Contact'));

function App() {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </Suspense>
    </Router>);
}

export default App;
```

### Explanation

1. **Lazy Loading**:
    - The `Home`, `About`, and `Contact` components are imported using `React.lazy`. This means they will only be loaded when the user navigates to the corresponding route.
2. **Suspense**:
    - The `Suspense` component wraps the `Routes` component and provides a fallback UI (`<div>Loading...</div>`) that will be displayed while the lazy components are being loaded.
3. **Routing**:
    - The `Routes` component from `react-router-dom` is used to define the routes. Each route corresponds to a lazy-loaded component.

### Benefits of Lazy Loading and React Suspense

- **Improved Performance**:
    - By splitting your code into smaller chunks and loading them on demand, you can reduce the initial load time of your application.
- **Better User Experience**:
    - Users only download the code they need, which can lead to faster interactions and a smoother experience.
- **Simplified Code Splitting**:
    - `React.lazy` and `Suspense` make it easy to implement code splitting without needing to manually handle promises or loading states.

### Advanced Usage

- **Error Boundaries**:
    - To handle errors that might occur while loading the lazy component, you can use an Error Boundary. This is a React component that catches JavaScript errors anywhere in its child component tree.

```jsx
import React, { Suspense, lazy } from 'react';
import ErrorBoundary from './ErrorBoundary';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <ErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </ErrorBoundary>);
}

export default App;
```

- **Preloading Components**:
    - You can preload lazy components in the background to improve the user experience further. This can be done by triggering the import before the component is actually needed.

```jsx
const LazyComponent = lazy(() => import('./LazyComponent'));

// Preload the component
const preloadLazyComponent = () => {
  import('./LazyComponent');
};

// Trigger preload on some user action
<button onClick={preloadLazyComponent}>Preload Component</button>
```

### Summary

- **Lazy Loading**: Use `React.lazy` to dynamically import components, reducing the initial load time.
- **React Suspense**: Use `Suspense` to provide a fallback UI while the lazy component is being loaded.
- **Error Boundaries**: Wrap `Suspense` with an Error Boundary to handle errors during loading.
- **Preloading**: Preload components in the background to improve user experience.

By combining lazy loading and React Suspense, you can create more efficient and responsive React applications, ensuring that users only download the code they need when they need it.

### useContext hook

Context API : In some React applications, the component tree structure is such that there could be some components which call in other child components. For e.g consider a React application in which the component tree appears like below: 

![ContextAPI_REACT.png](React%202088e3c5ec084e0db04fccaefddff2e8/ContextAPI_REACT.png)

Now, consider a scenario, in which ‘username’ needs to be displayed by components A,D and F. While component A can directly receive the ‘username’ like a prop, but in case of component D and F, the username prop will have to be passed down through all higher level components which have no use of the ‘username’ prop. This is where **Context**  comes into the picture. 

**Context provides a way to pass data through the component tree without having to pass down props manually at every level**. 

### Key Concepts

1. **Context**:
    - Context provides a way to pass data through the component tree without having to pass props down manually at every level.
    - It is designed to share data that can be considered "global" for a tree of React components, such as the current authenticated user, theme, or preferred language.
2. **`useContext` Hook**:
    - The `useContext` hook allows you to subscribe to a context and read its value within a functional component.
    - It takes a context object (created by `React.createContext`) and returns the current context value for that context.

### How to Use `useContext`

### 1. **Creating a Context**

First, you need to create a context using `React.createContext`. This function returns an object with `Provider` and `Consumer` components.

```jsx
import React from 'react';

const MyContext = React.createContext(defaultValue);
```

- `defaultValue`: The default value for the context. This is used when a component does not have a matching `Provider` above it in the component tree.

### 2. **Providing Context Value**

To provide a value to the context, you use the `Provider` component. This component accepts a `value` prop, which is the value you want to pass down to the components that consume the context.

```jsx
<MyContext.Provider value={/* some value */}>
  {/* child components */}
</MyContext.Provider>
```

### 3. **Consuming Context Value**

To consume the context value within a functional component, you use the `useContext` hook.

```jsx
import React, { useContext } from 'react';

function MyComponent() {
  const contextValue = useContext(MyContext);
  return <div>{contextValue}</div>;
}
```

### Example Usage

Here’s a complete example that demonstrates how to use `useContext` to manage a theme in a React application:

### 1. **Create a Context**

```jsx
import React from 'react';

const ThemeContext = React.createContext('light'); // Default theme is 'light'
```

### 2. **Provide Context Value**

Wrap your component tree with the `Provider` component and pass the current theme as the `value` prop.

```jsx
function App() {
  const [theme, setTheme] = React.useState('light');

  const toggleTheme = () => {
    setTheme(prevTheme => (prevTheme === 'light' ? 'dark' : 'light'));
  };

  return (
    <ThemeContext.Provider value={theme}>
      <Toolbar toggleTheme={toggleTheme} />
    </ThemeContext.Provider>);
}
```

### 3. **Consume Context Value**

Use the `useContext` hook to access the theme value within any component.

```jsx
import React, { useContext } from 'react';

function Toolbar({ toggleTheme }) {
  return (
    <div>
      <ThemedButton toggleTheme={toggleTheme} />
    </div>);
}

function ThemedButton({ toggleTheme }) {
  const theme = useContext(ThemeContext);

  return (
    <button
      onClick={toggleTheme}style={{
        backgroundColor: theme === 'light' ? '#fff' : '#333',
        color: theme === 'light' ? '#000' : '#fff',
      }}>
      Toggle Theme
    </button>);
}
```

### Explanation

1. **Creating Context**:
    - `ThemeContext` is created with a default value of `'light'`.
2. **Providing Context**:
    - The `App` component maintains the current theme state and provides it to the `ThemeContext.Provider`.
    - The `toggleTheme` function allows switching between `'light'` and `'dark'` themes.
3. **Consuming Context**:
    - The `ThemedButton` component uses the `useContext` hook to access the current theme value from `ThemeContext`.
    - The button's style is dynamically updated based on the current theme.

### Benefits of Using `useContext`

- **Simplifies Prop Drilling**:
    - `useContext` eliminates the need to pass props through multiple levels of components, making your code cleaner and easier to maintain.
- **Centralized State Management**:
    - Context allows you to manage state in a centralized manner, making it easier to share data across different parts of your application.
- **Improved Performance**:
    - By avoiding prop drilling, you can reduce the number of re-renders and improve the performance of your application.

### Advanced Usage

- **Combining with `useReducer`**:
    - You can combine `useContext` with `useReducer` to manage more complex state logic.

```jsx
import React, { useReducer, useContext } from 'react';

const initialState = { theme: 'light' };

function reducer(state, action) {
  switch (action.type) {
    case 'toggleTheme':
      return { theme: state.theme === 'light' ? 'dark' : 'light' };
    default:
      throw new Error();
  }
}

const ThemeContext = React.createContext();

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <ThemeContext.Provider value={{ state, dispatch }}>
      <Toolbar />
    </ThemeContext.Provider>);
}

function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>);
}

function ThemedButton() {
  const { state, dispatch } = useContext(ThemeContext);

  return (
    <button
      onClick={() => dispatch({ type: 'toggleTheme' })}style={{
        backgroundColor: state.theme === 'light' ? '#fff' : '#333',
        color: state.theme === 'light' ? '#000' : '#fff',
      }}>
      Toggle Theme
    </button>);
}
```

### Summary

- **`useContext` Hook**: Allows you to access the value of a context directly within a functional component.
- **Context**: Provides a way to pass data through the component tree without manually passing props at every level.
- **Benefits**: Simplifies prop drilling, centralizes state management, and improves performance.

By using `useContext`, you can create more maintainable and efficient React applications, especially when dealing with global state or shared data.

**Q. Explain what is the meaning of this statement: "This is used when a component does not have a matching Provider above it in the component tree.”**

The statement **"This is used when a component does not have a matching Provider above it in the component tree"** refers to how React handles the **default value** of a context when no `Provider` is present in the component tree. Let’s break this down step by step:

---

### 1. **What is a `Provider`?**

- A `Provider` is a component that wraps part of your component tree and supplies a value to the context. It is created when you use `React.createContext`.
- Any component within the `Provider`'s subtree can access the context value using `useContext` or `Context.Consumer`.

Example:

```jsx
<MyContext.Provider value={someValue}>
  <ChildComponent />
</MyContext.Provider>
```

Here, `ChildComponent` (and any of its descendants) can access the `someValue` provided by the `Provider`.

---

### 2. **What Happens if There is No `Provider`?**

- If a component tries to access a context using `useContext` or `Context.Consumer`, but there is no `Provider` wrapping it (or any of its ancestors), React will fall back to the **default value** specified when the context was created.

Example:

```jsx
const MyContext = React.createContext('defaultValue');

function ChildComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

function App() {
  return <ChildComponent />;
}
```

In this example:

- There is no `Provider` wrapping `ChildComponent` or any of its ancestors.
- When `ChildComponent` accesses `MyContext` using `useContext`, it will receive the **default value** (`'defaultValue'`) because no `Provider` is present.

---

### 3. **Why is the Default Value Useful?**

- The default value acts as a **fallback** to ensure that your application doesn’t break when a `Provider` is missing.
- It’s particularly useful during development or when you want to provide a sensible default for components that might be used outside of a `Provider`.

---

### 4. **When Does This Happen?**

This situation occurs in the following scenarios:

1. **No `Provider` in the Tree**:
    - If you forget to wrap your component tree with a `Provider`, the default value will be used.
2. **Using a Component Outside the `Provider`**:
    - If you use a component that relies on a context outside the subtree of the `Provider`, it will fall back to the default value.
3. **Testing Components in Isolation**:
    - When testing a component that uses a context, you might not always wrap it in a `Provider`. In such cases, the default value ensures the component still works.

---

### 5. **Example to Illustrate**

### Without a `Provider`:

```jsx
import React, { useContext } from 'react';

// Create a context with a default value
const ThemeContext = React.createContext('light');

function ThemedButton() {
  // Access the context value
  const theme = useContext(ThemeContext);

  return (
    <button style={{ backgroundColor: theme === 'light' ? '#fff' : '#333' }}>
      Current Theme: {theme}
    </button>);
}

function App() {
  return <ThemedButton />;
}
```

- In this case, `ThemedButton` will use the **default value** (`'light'`) because there is no `Provider` in the component tree.

### With a `Provider`:

```jsx
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedButton />
    </ThemeContext.Provider>);
}
```

- Here, `ThemedButton` will use the value provided by the `Provider` (`'dark'`).

---

### 6. **Key Takeaways**

- The **default value** is a safety net for when no `Provider` is present.
- It ensures that your components don’t break or throw errors when they try to access a context without a `Provider`.
- Always define a meaningful default value when creating a context, especially if the context is optional or might not always be provided.

---

### 7. **When to Avoid Relying on Default Values**

- If your application **requires** a context to function properly, you should always wrap the relevant parts of your component tree with a `Provider`.
- Relying on default values can lead to unexpected behavior if the context is essential for your component’s logic.

Example:

```jsx
const UserContext = React.createContext(null);

function UserProfile() {
  const user = useContext(UserContext);

  if (!user) {
    throw new Error('UserContext.Provider is missing!');
  }

  return <div>Welcome, {user.name}!</div>;
}
```

In this case, the component explicitly throws an error if the `Provider` is missing, ensuring that the context is always provided.

# **React + TypeScript**

### React props are always objects

In React, components receive their inputs via a special object called **props**. Props are used to pass data from a parent component to a child component.

When you define a React functional component, it receives **one single argument**, which is the **props object**. This object contains all the props (properties) passed to the component by the parent. 

### **Incorrect Way: Direct Parameter**

When you define your `DisplayExpenses` component like this:

```tsx

function DisplayExpenses(expenses: ExpenseProp[]) {
  return expenses;
}
```

### **Explanation**:

- Here, `expenses` is being treated as if it were passed **directly** as the only parameter to the component.
- This implies that when calling `<DisplayExpenses />`, React would need to pass `expenses` directly as an argument, which is **not how React works**.

### **What React Actually Passes**:

- React **always passes a single object** to the component. This object contains all the props as key-value pairs.

---

### **Correct Way: Props Object**

In React, the correct way to define the component is to accept a **props object** and then access `expenses` from that object:

```tsx

function DisplayExpenses({ expenses }: { expenses: ExpenseProp[] }) {
  return (
    <ul>
      {expenses.map((expense, index) => (
        <li key={index}>{expense.title}</li>
      ))}
    </ul>
  );
}
```

### **Explanation**:

- `{ expenses }` is a **de-structuring assignment**. It means you're extracting the `expenses` key from the props object.
- The full function signature could also be written without de-structuring like this:
    
    ```tsx
    
    function DisplayExpenses(props: { expenses: ExpenseProp[] }) {
      return (
        <ul>
          {props.expenses.map((expense, index) => (
            <li key={index}>{expense.title}</li>
          ))}
        </ul>
      );
    }
    ```
    

### **Why This Works**:

- When you call the component in `App.tsx` like this:
    
    ```tsx
    
    <DisplayExpenses expenses={expenses} />
    ```
    
    React passes an object that looks like this:
    
    ```jsx
    
    { expenses: [ { title: 'Dinner', amount: '100', date: '16-Nov-2024', selectedCategory: 'food' } ] }
    ```
    
- Your component receives this object and can access the `expenses` array using `props.expenses` or `{ expenses }` through de-structuring.

---

### **React’s Props Mechanism**

When React calls a component, it always passes a **single props object**. This object groups all the props you pass to the component in the JSX.

### **Example of Multiple Props**

If your component needed more than one prop, you might have:

```tsx

<DisplayExpenses expenses={expenses} title="My Expenses" />
```

React will pass:

```jsx

{ expenses: [...], title: "My Expenses" }
```

Therefore, your component should be defined to accept a **props object** that contains these keys:

```tsx

function DisplayExpenses({ expenses, title }: { expenses: ExpenseProp[]; title: string }) {
  return (
    <div>
      <h2>{title}</h2>
      <ul>
        {expenses.map((expense, index) => (
          <li key={index}>{expense.title}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

### **Summary**

1. **React Passes One Props Object**:
    - When you render a component with props, React bundles all the props into a **single object**.
2. **Treat Props as an Object**:
    - Your component should accept this props object and access individual props from it, either through:
        - De-structuring: `function Component({ prop1, prop2 })`
        - Accessing via the `props` object: `function Component(props)`
3. **Why Direct Parameters Don’t Work**:
    - React doesn’t call components with individual arguments for each prop. It only passes one argument—the props object.

### **Analogy**

Imagine props as a **package** containing multiple items:

- **Incorrect Way** (Direct Parameter):
    
    You're expecting React to hand you each item directly.
    
    ```tsx
    
    function DisplayExpenses(expenses, title) {
      // This is not how React passes props.
    }
    ```
    
- **Correct Way** (Props Object):
    
    React hands you the **package** (an object), and you unpack the items from it.
    
    ```tsx
    
    function DisplayExpenses({ expenses, title }) {
      // Unpack 'expenses' and 'title' from the props object.
    }
    ```
    

This approach aligns with how React handles data flow, making your components flexible and consistent.

1. **Navigation with State:**
    - Pass additional data to the destination route for contextual rendering.
2. **Dynamic Routing Logic:**
    - Perform conditional navigation (e.g., redirect users after login or based on permissions).
3. **Event-Based Navigation:**
    - Trigger route changes based on events like button clicks, form submissions, or API responses.

### When to Use `useNavigate`?

---

| Feature | Example Usage |
| --- | --- |
| Navigate to a path | `navigate('/path')` |
| Pass state with navigation | `navigate('/path', { state: {...} })` |
| Navigate backward/forward | `navigate(-1)` or `navigate(1)` |
| Replace current history | `navigate('/path', { replace: true })` |

### Key Features of `useNavigate`

---

1. **Dynamic Navigation Logic:**
    - You can control routing based on custom logic like authentication, validation, or permissions.
2. **Conditional Navigation:**
    - After clicking "Log In," the app navigates to `/dashboard` if the user is logged in.

### How This Works:

---

```jsx
jsx
Copy code
import React, { useState } from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Login = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const navigate = useNavigate();

  const handleLogin = () => {
    setIsLoggedIn(true);
    navigate('/dashboard'); // Navigate to dashboard after login
  };

  return (
    <div>
      <h1>Login Page</h1>
      <button onClick={handleLogin}>Log In</button>
    </div>
  );
};

const Dashboard = () => <h1>Dashboard</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/dashboard" element={<Dashboard />} />
      </Routes>
    </Router>
  );
};

export default App;

```

### Code Example:

You can use `useNavigate` to perform navigation based on conditions, such as user authentication or form validation.

### Example 4: Conditional Navigation

---

1. **`navigate(1)`:**
    - Moves forward one step in the browser’s history stack.
2. **`navigate(-1)`:**
    - Moves backward one step in the browser’s history stack.

### How This Works:

---

```jsx
jsx
Copy code
import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Page1 = () => {
  const navigate = useNavigate();
  return (
    <div>
      <h1>Page 1</h1>
      <button onClick={() => navigate('/page2')}>Go to Page 2</button>
    </div>
  );
};

const Page2 = () => {
  const navigate = useNavigate();
  return (
    <div>
      <h1>Page 2</h1>
      <button onClick={() => navigate(-1)}>Go Back</button>
      <button onClick={() => navigate(1)}>Go Forward</button>
    </div>
  );
};

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/page1" element={<Page1 />} />
        <Route path="/page2" element={<Page2 />} />
      </Routes>
    </Router>
  );
};

export default App;

```

### Code Example:

The `navigate` function can also emulate the browser’s back and forward buttons by passing relative values.

### Example 3: Navigating Backward and Forward

---

1. **Dynamic Rendering:**
    - The `About` page displays the passed message, enabling dynamic, contextual content.
2. **`useLocation`:**
    - Retrieves the state data passed during navigation.
3. **`state` Property:**
    - Custom state (`{ message: 'Hello from Home!' }`) is passed when navigating to `/about`.

### How This Works:

---

```jsx
jsx
Copy code
import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate, useLocation } from 'react-router-dom';

const Home = () => {
  const navigate = useNavigate();

  const goToAboutWithMessage = () => {
    navigate('/about', { state: { message: 'Hello from Home!' } });
  };

  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={goToAboutWithMessage}>Go to About with Message</button>
    </div>
  );
};

const About = () => {
  const location = useLocation();
  const state = location.state || {};

  return (
    <div>
      <h1>About Page</h1>
      <p><strong>Message:</strong> {state.message || 'No message passed'}</p>
    </div>
  );
};

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};

export default App;

```

### Code Example:

The `navigate` function allows you to pass additional state data to the target route, which can be accessed using the `useLocation` hook.

### Example 2: Passing State While Navigating

---

1. **`navigate('/about')`:**
    - Changes the route to `/about` and renders the `About` component.
2. **`useNavigate`:**
    - Provides the `navigate` function to control routing programmatically.

### How This Works:

---

```jsx
jsx
Copy code
import React from 'react';
import { BrowserRouter as Router, Routes, Route, useNavigate } from 'react-router-dom';

const Home = () => {
  const navigate = useNavigate();

  const goToAbout = () => {
    navigate('/about');
  };

  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={goToAbout}>Go to About</button>
    </div>
  );
};

const About = () => <h1>About Page</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};

export default App;

```

### Code Example:

### Example 1: Basic Navigation

---

1. **State Passing:**
    - Pass custom state data to the target route.
2. **Navigation Control:**
    - Navigate backward or forward in the browser history stack.
3. **Dynamic Path Construction:**
    - Easily construct routes with parameters, query strings, or conditional logic.
4. **Programmatic Navigation:**
    - Navigate to different routes without requiring user interaction with a link.

### Key Features of `useNavigate`

---

The `useNavigate` hook in `react-router-dom` allows you to programmatically navigate users to different routes in your React app. Instead of relying solely on `<Link>` or `<NavLink>` for navigation, `useNavigate` gives you the power to navigate dynamically in response to events like button clicks, API responses, or conditional logic.

### `useNavigate` in React Router