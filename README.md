# todo-app-react
simple to do app

### Understanding State

- What is state?
    
     it’s an object that lives inside of a component that stores all of the data that that component and maybe some of its children need. 
    
- Think of state as a single source of truth
    
    With vanilla javaScript if you want to have data sometimes that data lives in multiple places so you might have some of that data in a variable but then you might have some more data in a data attribute on a DOM element and then you might pull it out of there and and put it back in and use that as a place to store your data -  with react the golden rule is don’t touch the DOM, instead of thinking about updating all of the pieces on our website we want to think about just updating our data and then letting react take it. 
    
    With react we keep our data in state and whenever state changes - react reacts to that change and it knows where that data is anywhere in the application and it will go and update all of that data on the website. 
    

### Hooks

Hooks are functions that let you “hook into” React state and lifecycle features from function components. Hooks don’t work inside classes — they let you use React without classes. 

React provides a few built-in Hooks like `useState`. You can also create your own Hooks to reuse stateful behaviour between different components.

Hooks embrace JavaScript closures and avoid introducing React-specific APIs where JavaScript already provides a solution.

- What is a closure?
    
    A closure happens when an inner function reaches into an outer function to grab a value defined in the outer function
    

`useState()`

Before hooks functional components had no state. We can now use state with useState(). Let’s break down how this works: 

we declare a variable with an array `const []` inside of our array we add our variable to read the state and our function to write the state `const [state, setState]` we set that equal to `useState()` and inside of the parenthesis we set our initial state. `const [state, setState] = useState({varName: initalState});`

- What is a side effect?
    
    React transforms our data into UI. Each component plays its part, returning its contribution to the overall user interface. React builds the tree of elements, compares it with what’s already rendered, and commits any necessary changes to the DOM. When the state changes, React goes through the process again to update the UI. React is really good at efficiently deciding what should update and scheduling any changes.
    
    Sometimes, however, we need our components to reach outside this data-flow process and directly interact with other APIs. An action that impinges on the outside world in some way is called a *side effect*. Common side effects include the following:
    
    - Setting the page title imperatively
    - Working with timers like `setInterval` or `setTimeout`
    - Measuring the width, height, or position of elements in the DOM
    - Logging messages to the console or other service
    - Setting or getting values in local storage
    - Fetching data or subscribing and unsubscribing to services
    

`useEffect()`

We are writing functional components so you may not be familiar with this but class components manage side effects using life cycle methods like `componentDidMount()` - this is a method you would call if there are any DOM modifications. `useEffect()` lets us perform side effects in functional components. 

By default, effects run after every completed render. But, you can choose to fire it only when certain values have changed, passing an array of variables as a second optional parameter

```
// Without the second parameter
useEffect(() => {
  console.log('I will run after every render');
});

// With the second parameter
useEffect(() => {
  console.log('I will run only when valueA changes');
}, [valueA]);

// With empty array
useEffect(() => {
  console.log('I will run only once');
}, []);

//To have the same result as componentDidMount() we can send an empty array. Knowing that an empty set does never change, the effect will run only once.
```
