

# Espd - 8 Classy

## Q: What is the order of life cycle method calls in `Class Based Components`?

A: Following is the order of lifecycle methods calls in `Class Based Components`:

1. constructor()
2. render ()
3. componentDidMount()
4. componentDidUpdate()
5. componentWillUnmount()

For more reference [React-Lifecycle-methods-Diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## Q: Why do we use `componentDidMount`?

A: The `componentDidMount()` method allows us to execute the React code when the component is already placed in the DOM (Document Object Model). This method is called during the Mounting phase of the React Life-cycle i.e after the component is rendered.
Wwe can run any piece of react code to modify the components. For ex. It's the best place to `make API calls`.

## Q: Why do we use `componentWillUnmount`? Show with example.

A: `componentWillUnmount()` is useful for the cleanup of the application when we switch routes from one place to another. Since we are working with a SPA(Single Page Application) the component process always runs in the background even if we switch to another route. So it is required to stop those processes before leaving the page. If we revisit the same page, a new process starts that affects the browser performance.
For example, in Repo class, during `componentDidMount()` a timer is set with an interval of every one second to print in console. When the component is unmounted (users moves to a different page), the timer will be running in the background, which we might not even realize and causing huge performance issue. To avoid such situations the cleanup function can be done in componentWillUnmount, in this example `clearInterval`(timer) to clear the timer interval before unmounting Repo component.

## Q: (Research) Why do we use `super(props)` in constructor?

A: `super(props)` is used to inherit the properties and access of variables of the React parent class when we initialize our component.
super() is used inside constructor of a class to derive the parent's all properties inside the class that extended it. If super() is not used, then Reference Error : Must call super constructor in derived classes before accessing 'this' or returning from derived constructor is thrown in the console.
The main difference between super() and super(props) is the this.props is undefined in child's constructor in super() but this.props contains the passed props if super(props) is used.

## Q: (Research) Why can't we have the `callback function` of `useEffect async`?

A: `useEffect` expects it's callback function to return nothing or return a function (cleanup function that is called when the component is unmounted). If we make the callback function as `async`, it will return a `promise` and the promise will affect the clean-up function from being called.


# Error Boundry

An Error Boundary in React is a React-specific feature that wraps a component and prevents any errors from spreading to other parts of the application, thus preventing the entire application from crashing. It is designed to catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. This is similar to a JavaScript `catch {}` block but specifically for components. Error boundaries are crucial for enhancing the dependability and stability of React applications, improving user experience by preventing errors from crashing the entire program [1][3].

Error boundaries are implemented using class components with either or both of the following lifecycle methods:
- `static getDerivedStateFromError()`: This method is used to render a fallback UI after an error has been thrown.
- `componentDidCatch()`: This method is used to log error information [1][3].

However, error boundaries have some limitations:
- They cannot catch all errors, such as those in event handlers, asynchronous programming, or server-side rendering.
- They can add overhead to your application due to the monitoring of the component tree's condition.
- They can make debugging errors more difficult as they can hide the initial mistake.
- They do not replace good coding principles; components should still have strong error handling and validation processes [1].

For functional components, the `useErrorBoundary` hook from third-party libraries can be used to achieve a similar feature. The `react-error-boundary` library provides a more modern approach with React Hooks and functional components, offering a flexible way to handle JavaScript errors in React components. It includes a `useErrorHandler` hook that allows throwing errors from anywhere in function components, which will be caught by the nearest error boundary [3].

React-error-boundary also supports retry mechanisms through the `resetErrorBoundary` function and the `resetKeys` prop, allowing the application to attempt to recover from an error by retrying the failed operation [3].

### in simple terms:-

In simple terms, an Error Boundary in React is like a safety net for your app. It's a special component that catches errors in your app and prevents them from crashing the whole app. Instead, it shows a fallback UI, like an error message, so the user knows something went wrong but the rest of the app can still work. This helps keep your app running smoothly even when there's a problem. Error Boundaries are used by wrapping them around parts of your app that might have errors. They catch those errors and handle them gracefully, without letting the whole app stop working
