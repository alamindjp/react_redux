### Welcome To React Redux Cheat Sheet.

# What is redux ?

Redux is a state management library for JavaScript apps. We can use with any JS library or framework like React, Angular, or Vue. it is a global state management library.

#### We use React Redux. So, I will be assuming that you're familiar with React.

<br/>

### Here, We learn react redux fundamentals.

#### Like:

- Why we will learn redux ?
- Redux Toolkit.
- Core principles of redux.
- Redux three key principles.

# Why we will learn redux ?

Redux is itself a standalone library that is used with any UI library or framework. It can be used with frameworks such as React, Angular, Vue, and vanilla JavaScript. However, Redux and React are commonly used together.

# Redux Toolkit.

Redux Toolkit is their designed Redux logic. It's creating a Redux app esely. It repeatedly leverages the Redux core, and it provides the necessary packages and functionalities to build a Redux app. Redux Toolkit incorporates the best practices, simplifies Redux tasks, and helps prevent common mistakes when writing Redux applications.

# Core principles of Redux.

Redux is three core principles.

1. Store.
2. Actions
3. Reducers.

### Example of Redux core principles in this image

![Redux Core image](./images/redux_core.png)

## 1. What is Store?

A store represents the entire [state tree](https://redux.js.org/understanding/thinking-in-redux/glossary#store) of your application. The only way to modify the state within it is to dispatch an [action](https://redux.js.org/understanding/thinking-in-redux/glossary#action), which encourages the [root reducer function](https://redux.js.org/understanding/thinking-in-redux/glossary#reducer) to recalculate the new state. [More](https://redux.js.org/api/store)

### Example with image

![Redux Core image](./images/Store.png)

### Example with code

```javascript
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";

import { App } from "./App";
import createStore from "./createReduxStore";

const store = createStore();

// As of React 18
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

```javascript
// this is how the store object structure looks like
{
    noOfItemInCart: 2,
    cart: [
        {
            bookName: "Harry Potter and the Chamber of Secrets",
            noOfItem: 1,
        },
        {
            bookName: "Harry Potter and the Prisoner of Azkaban",
            noOfItem: 1
        }
    ]
}


```

<br/>

## 1. What is Actions?

Action is a function. That is used for changing the state of a store in Redux. Actions are dispatched to the store. And they provide information about the type of operation to be performed. An action has a 'type' property, it is describing the type of action. And contains additional data as needed. [more](https://redux.js.org/understanding/thinking-in-redux/glossary#action)

### Example with image

![Redux Core image](./images/Actions.png)

### Example with code

```javascript
// Rest of the code

const dispatch = useDispatch()

const addItemToCart = () => {
return {
    type: "ADD_ITEM_TO_CART"
    payload: {
        bookName: "Harry Potter and the Goblet of Fire",
        noOfItem: 1,
        }
    }
}

<button onClick = {() => dispatch(addItemToCart())}>Add to cart</button>

// Rest of the code

```

```javascript
// Action that got created by the action creator addItemToCart()

{
    type: "ADD_ITEM_TO_CART" // Note: Every action must have a type key
    payload: {
        bookName: "Harry Potter and the Goblet of Fire",
        noOfItem: 1,
    }
}

```

<br/>

## 1. What is Reducer ?

Reducer is a function. That determines how the application's state changes. And it dispatches an action to the Redux store.
It works with the current state and an action. And based on the type of action, it returns the new state.The main purpose of the reducer is to manage state changes. [more](https://redux.js.org/understanding/thinking-in-redux/glossary#reducer)

### Example with image

![Redux Core image](./images/Reducers.png)

### Example with code

```javascript
const initialCartState = {
  noOfItemInCart: 0,
  cart: [],
};

// NOTE:
// It is important to pass an initial state as default to
// the state parameter to handle the case of calling
// the reducers for the first time when the
// state might be undefined

const cartReducer = (state = initialCartState, action) => {
  switch (action.type) {
    case "ADD_ITEM_TO_CART":
      return {
        ...state,
        noOfItemInCart: state.noOfItemInCart + 1,
        cart: [...state.cart, action.payload],
      };
    case "DELETE_ITEM_FROM_CART":
      return {
        // Remaining logic
      };
    default:
      return state;
  } // Important to handle the default behaviour
}; // either by returning the whole state as it is
// or by performing any required logic
```

<br/>

# Installation Redux Core

The Redux core library is available as a package on NPM for use with a module bundler or in a Node application:

[More here](https://redux.js.org/introduction/getting-started#redux-core)

###### # If you use NPM

```
npm install redux
```

###### # Or if you use Yarn

```
yarn add redux
```

<br/>

# Installation Redux Toolkit and React Redux

Redux Toolkit is available as a package on NPM for use with a module bundler or in a Node application:

[More Here](https://redux.js.org/introduction/getting-started#installation)

###### # If you use NPM

```
npm install @reduxjs/toolkit react-redux
```

###### # Or if you use Yarn

```
yarn add @reduxjs/toolkit react-redux
```

# Create a React Redux App

The recommended way to start new apps with React and Redux is by using our official [Redux+TS template for Vite](https://github.com/reduxjs/redux-templates), or by creating a new Next.js project using [Next's with-redux template](https://github.com/vercel/next.js/tree/canary/examples/with-redux).

```javascript

# Vite with our Redux+TS template
# (using the `degit` tool to clone and extract the template)
npx degit reduxjs/redux-templates/packages/vite-template-redux my-app

# Next.js using the `with-redux` template
npx create-next-app --example with-redux my-app

```

<br/>

### Create the Redux Store.

Create a file and this file is named `store.js`. And path is `src/app/redux/store.js`. In this file, you'll use `configureStore` from @reduxjs/toolkit to set up your Redux store.

### Example

Create `src/app/redux/store.js`

```javascript
// store.js
import { configureStore } from "@reduxjs/toolkit";

const store = configureStore({
  reducer: {
    // Your reducers will go here
  },
});

export default store;
```

#### Provide the Redux Store to React with a Provider

Then import `store` from `./redux/store`. And The `<App />` component needs to be wrapped with the `<Provider>`. and makes it aware of the entire Redux's `store`.

### Example

`src/index.jsx`

```javascript
// index.js
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";
import store from "./redux/store";
import App from "./App";

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);
```

<br/>

### Create a Redux State Slice

Create a folder `features`. features folder inside create `counter` and that inside create `counterSlice.js` file. And path is `src/app/redux/features/counter/counterSlice.js`

### Example

`features/counter/counterSlice.js`

```javascript
i; // counterSlice.js
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

### Add Slice Reducers

Now we import the `reducer` function from the `counterSlice` and add it to our `store.js` file.

### Example

`src/app/redux/store.js`

```javascript
// store.js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./counterSlice";

const store = configureStore({
  reducer: {
    counter: counterReducer,
    // Add other reducers here
  },
});

export default store;
```

<br/>

### Use Redux State and Actions in React Components

### Example

`src/app/counter.js`

```javascript

// counter.js
import React from "react";
import { useSelector, useDispatch } from "react-redux";
import { decrement, increment } from "./counterSlice";
import styles from "./Counter.module.css";

export function Counter() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <div>
        <button
          aria-label="Increment value"
          onClick={() => dispatch(increment())}
        >
          Increment
        </button>
        <span>{count}</span>
        <button
          aria-label="Decrement value"
          onClick={() => dispatch(decrement())}
        >
          Decrement
        </button>
      </div>
    </div>
  );
}

```
## 
## The End