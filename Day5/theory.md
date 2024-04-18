## EPSD -7

## Q: What are various ways to `add images` into our App? Explain with `code examples`.

A: Using the `full URL of the image` for the web (CDN) or any public images.
Example :

```
<img src="https://reactjs.org/logo-og.png" alt="React Image" />
```

Adding the image into the project
`Drag your image into your project` and `import it` into the desired component

```
import reactLogo from "./reactLogo.png";
export default function App() {
  return <img src={reactLogo} alt="react logo" />
}
```

The correct way to structure images in your project is to add them in an `images` folder. If you are using other `assets` than just images, you might want to add all in the `assets` folders.

```
import reactLogo from "../../assets/images/reactLogo.png";
export default function App() {
  return <img src={reactLogo} alt="react logo" />
}
```

## Q: What would happen if we do `console.log(useState())`?

A: If we do `console.log(useState())`, we get an array `[undefined, function]` where first item in an array is `state` is `undefined` and the second item in an array is `setState` `function` is bound dispatchSetState.

## Q: How will `useEffect` behave if we `don't add` a `dependency array`?

A: Syntax of `useEffect` is:

```
useEffect(() => {}, []);
```

Case 1 : When the `dependency array is not included` in the arguments of `useEffect() hook`, the callback function will be executed `every time` the component is rendered and re-rendered.

```
useEffect(() => {
	console.log("I run everytime this component rerenders")
});
```

Case 2 : When the `dependency array is empty` in the arguments of `useEffect() hook`, the callback function will be executed `only one time` during the initial render of the component.

```
useEffect(() => {
	console.log("I Only run once (When the component gets mounted)")
}, []);
```

Case 3 : When the `dependency array contains a condition`, the callback function will be executed `one time` during the initial render of the component and also rerender if there is a `change in the condition`.

```
useEffect(() => {
	console.log("I run every-time when my condition changed")
}, [condition]);
```

## Q: What is `SPA`?

A: `Single Page Application (SPA)` is a web application that dynamically updates the webpage with data from web server without reloading/refreshing the entire page. All the HTML, CSS, JS are retrieved in the initial load and other data/resources can be loaded dynamically whenever required. An SPA is sometimes referred to as a `single-page interface (SPI)`.

## Q: What is the difference between `Client Side Routing` and `Server Side Routing`?

A: In `Server-side routing or rendering (SSR)`, every change in URL, http request is made to server to fetch the webpage, and replace the current webpage with the older one.

In `Client-side routing or rendering (CSR)`, during the first load, the webapp is loaded from server to client, after which whenever there is a change in URL, the router library navigates the user to the new page without sending any request to backend. All `Single Page Applications uses client-side routing`.


The `useParams` hook in React Router is a powerful tool that allows you to access dynamic parameters in the URL within your components. This hook is particularly useful when you have routes that include dynamic segments, which are parts of the URL that can change. By using `useParams`, you can retrieve these dynamic segments and use them to fetch data, render specific components, or perform other actions based on the URL.

## How `useParams` Works

- **Dynamic Parameters in Routes**: When defining routes in your application, you can specify dynamic segments by prefixing the segment name with a colon (`:`). For example, in a route like `/users/:userId`, `:userId` is a dynamic segment that can represent any user ID.

- **Accessing Dynamic Parameters**: Inside a component that is rendered by a route with dynamic segments, you can use the `useParams` hook to access these segments. The hook returns an object where the keys are the names of the dynamic segments as defined in the route, and the values are the actual segments from the current URL.

- **Example Usage**:

 ```jsx
 import { useParams } from "react-router-dom";

 const UserProfile = () => {
    const { userId } = useParams();
    // Now you can use userId to fetch user data, render specific content, etc.
 };
 ```

 In this example, if the current URL is `/users/123`, `useParams` will return `{ userId: '123' }`, allowing you to access the `userId` directly within your component.

### Important Considerations

- **Matching Parameter Names**: The names of the parameters you access from `useParams` must match the names specified in the route definition. For example, if your route is defined as `/users/:userId`, you must use `const { userId } = useParams();` to access the user ID.

- **Dynamic Routing**: `useParams` is essential for creating dynamic routes in your application. It allows you to render different content based on the URL, making your application more flexible and user-friendly.

- **Real-World Applications**: `useParams` is widely used in applications that require dynamic content rendering, such as e-commerce platforms displaying product details, social media platforms showing user profiles, or blogging platforms displaying articles.

In summary, the `useParams` hook is a fundamental part of React Router that enables the creation of dynamic and interactive routing in React applications. By leveraging this hook, developers can build applications that respond to changes in the URL, providing a more engaging and personalized user experience .
# How to pass data from a child component to its parent component in React

To pass data from a child component to its parent component in React, you typically use a callback function. This involves defining a function in the parent component that will handle the data received from the child, and then passing this function as a prop to the child component. The child component can then call this function with the data it wants to pass up to the parent.

Here's a step-by-step guide based on the information provided in the sources:

### Step 1: Define a Callback Function in the Parent Component

In the parent component, create a function that will be responsible for handling the data received from the child component. This function can update the parent's state or perform any other action with the data.

```jsx
// Parent component
import React, { useState } from "react";
import Child from "./Child";

function Parent() {
 const [dataFromChild, setDataFromChild] = useState("");

 function handleDataFromChild(data) {
    setDataFromChild(data);
 }

 return (
    <div>
      <h1>Data from Child: {dataFromChild}</h1>
      <Child sendDataToParent={handleDataFromChild} />
    </div>
 );
}

export default Parent;
```

### Step 2: Pass the Callback Function to the Child Component as a Prop

When rendering the child component within the parent component, pass the callback function as a prop. This allows the child component to call this function and pass data back to the parent.

### Step 3: Call the Callback Function in the Child Component

In the child component, call the callback function passed as a prop with the data you want to send to the parent component. This can be done in response to an event, such as a button click or a form submission.

```jsx
// Child component
import React, { useState } from "react";

function Child({ sendDataToParent }) {
 const [data, setData] = useState("");

 function handleClick() {
    sendDataToParent(data);
 }

 return (
    <div>
      <input type="text" value={data} onChange={(e) => setData(e.target.value)} />
      <button onClick={handleClick}>Send Data to Parent</button>
    </div>
 );
}

export default Child;
```

### Summary

Passing data from a child component to a parent component in React involves using callback functions. Here's a simple explanation you can provide to an interviewer:

1. **Parent Component**: This is the component that contains the child component and wants to receive data from it.

2. **Child Component**: This is the component that holds the data you want to pass to the parent.

To pass data from the child to the parent:

1. **Define a Function in the Parent**: In the parent component, define a function that will handle the data received from the child.

2. **Pass the Function to the Child as a Prop**: Pass the function from the parent component to the child component as a prop.

3. **Call the Function in the Child**: In the child component, when you want to send data to the parent, call the function passed from the parent.

4. **Send Data as an Argument**: When calling the function in the child component, you can send any data you want to pass to the parent as an argument.

5. **Parent Receives Data**: The function defined in the parent component will receive the data passed from the child, and you can then use this data in the parent component as needed.


# Vice verca Passing data from a parent component to a child component

Passing data from a parent component to a child component in React involves using props. Here's a simple explanation you can provide to an interviewer:

1. **Parent Component**: This is the component that contains the data you want to pass to the child component.

2. **Child Component**: This is the component that will receive the data from the parent.

To pass data from the parent to the child:

1. **Parent Passes Data as Props**: In the parent component, pass the data to the child component as props. You can pass any data, such as variables, functions, or even JSX elements.

2. **Child Receives Data via Props**: In the child component, access the data passed from the parent through props. You can use this data in the child component as needed, such as displaying it or using it to trigger actions.

Here's a simple example:

Parent Component:
```jsx
import React from 'react';
import Child from './Child';

const Parent = () => {
  const message = 'Hello from Parent';

  return (
    <div>
      <h2>Parent Component</h2>
      <Child messageFromParent={message} />
    </div>
  );
};

export default Parent;
```

Child Component:
```jsx
import React from 'react';

const Child = ({ messageFromParent }) => {
  return (
    <div>
      <h3>Child Component</h3>
      <p>Message from Parent: {messageFromParent}</p>
    </div>
  );
};

export default Child;
```

In this example, the parent component passes the message `'Hello from Parent'` to the child component as the prop `messageFromParent`. The child component then receives this prop and displays the message `'Hello from Parent'` within its JSX.



