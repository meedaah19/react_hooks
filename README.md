React hooks

useRef

    useRef is a React Hook that creates a mutable ref object which can be used to persist values between renders without causing the component to re-render. The ref object has a current property that is initialized with the value passed as an argument to useRef.

    useRef is primarily used for accessing DOM elements directly, managing mutable values that don't affect rendering, and storing previous values.

    EXAMPLES
    import React, { useRef, useEffect } from 'react';

    function MyComponent() {
    const inputRef = useRef(null);

    useEffect(() => {
        inputRef.current.focus();
    }, []);

    return (
        <input type="text" ref={inputRef} />
    );
    }
    In this example, useRef is used to create a ref object that is then assigned to the input element using the ref prop. The useEffect hook is used to focus the input element when the component mounts.



useState

    We initialize our state by calling useState in our function component.

    useState accepts an initial state and returns two values:

    The current state.
    A function that updates the state.

    To read the state, we will use the state variable in the rendered component.

    To update our state, we use our state updater function.

    It can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!
    We can also use state and include an object instead by creating a single Hook that holds an object.

    If we want to update only one object in an array, we use the javascript spread operator, because we need the current value of state, we pass a function into our updating function. This function receives the previous value. We then return an object, spreading the previousState and overwriting only the object we want to change.



useEffect

    The useEffect Hook allows you to perform side effects in your components.

    Some examples of side effects are: fetching data, directly updating the DOM, and timers.

    useEffect accepts two arguments. The second argument is optional.

    useEffect runs on every render. 

    We should always include the second parameter which accepts an array. We can optionally pass dependencies to useEffect in this array.

    Some effects require cleanup to reduce memory leaks, like the timeout, eventlistner and to do so we will include a return function at the end of the useEffect Hook.

    EXAMPLE
    import { useState, useEffect } from "react";
    import ReactDOM from "react-dom/client";

    function Timer() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        let timer = setTimeout(() => {
        setCount((count) => count + 1);
    }, 1000);

    return () => clearTimeout(timer) //return a function
    }, []);

    return <h1>I've rendered {count} times!</h1>;
    }


useContext

    React Context is a way to manage state globally.

    It can be used together with the useState Hook to share state between deeply nested components more easily than with useState alone.
    We use context to avoid prop drilling, and prop drilling is passing of prop from one component to another

    To avoid prop drilling, we create context by initializing createContext, we then use the Context Provider to wrap the tree of components that need the state Context, so all component will have access to the context.
    In order to have access to the context in child component, we will use useContext.


useReducer

    It is use when having a complext logic, it works like useState.

    The useReducer Hook accepts two arguments, a reduce and initialState.

    The reducer function contains your custom state logic and the initialStatecan be a simple value but generally will contain an object.

    The useReducer Hook returns the current state and a dispatch method.



useCallback

    We use the useCallback hook to prevent the function from being recreated unless necessary. It memoized function.


useMemo

    The React useMemo Hook returns a memoized value. It memoized value.
    The useMemo Hook can be used to keep expensive, resource intensive functions from needlessly running.


Custom hooks

Custom Hooks start with "use". In a case when we want to fetch a data and it will be needed in a multiple component, we can create a custom hook, then fetch the data inside the custom hook, the call the custom hook whenever it needed, that is reuse them.