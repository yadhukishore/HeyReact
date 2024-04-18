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

In summary, the `useParams` hook is a fundamental part of React Router that enables the creation of dynamic and interactive routing in React applications. By leveraging this hook, developers can build applications that respond to changes in the URL, providing a more engaging and personalized user experience [1][3][4].

