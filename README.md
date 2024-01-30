<center>

### Welcome To React Redux Cheat Sheet.

</center>

# What is redux ?
Redux is a state management library for JavaScript apps. We can use with any JS library or framework like React, Angular, or Vue. it is a global state management library.

#### We use React Redux. So, I will be assuming that you're familiar with React.
<br/>



### Here, We learn react redux fundamentals. 
#### Like:
* Why we will learn redux ?
* Redux Toolkit.
* Core principles of redux.
* Redux three key principles.


# Why we will learn redux ?
Redux is itself a standalone library that is used with any UI library or framework. It can be used with frameworks such as React, Angular, Vue, and vanilla JavaScript. However, Redux and React are commonly used together. 

# Redux Toolkit.
Redux Toolkit is their designed Redux logic. It's creating a Redux app esely. It repeatedly leverages the Redux core, and it provides the necessary packages and functionalities to build a Redux app. Redux Toolkit incorporates the best practices, simplifies Redux tasks, and helps prevent common mistakes when writing Redux applications.

# Core principles of Redux.
Redux is three core principles. 
1) Store. 
2) Actions 
3) Reducers.

### Example of Redux core principles image
![Redux Core image](./images/redux_core.png)

### 1. What is the Redux Store?
A store represents the entire [state tree](https://redux.js.org/understanding/thinking-in-redux/glossary#state) of your application. The only way to modify the state within it is to dispatch an action, which encourages the root reducer function to recalculate the new state.

![Redux Core image](./images/Store.png)