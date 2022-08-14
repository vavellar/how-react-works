# In react, we have some basic concepts, they are:

### Reconciliation:

### Virtual DOM:

### Rendering:

### Diffing Algorithm:

First of all we, need to understand what is the difference between React Components X React Elements X Component instances

Lets look at a simple react component that uses JSX

```
const App = () => {
    return (
        <div>
            App component
        </div>
    )
}
```

The converted code to this snippet is:

```
const App = () => {
    return React.createElement("div", null, "App component")
}

the first argument of createElement function is the type of the element, the second argument is the props and the third is the children
```

For react, this is the what this functions returns

````
{
    "$$typeof: Symbol(react.element), -> this is a just security measure, to more details visit: https://overreacted.io/why-do-react-elements-have-typeof-property/
    key: null,
    props: { children: "App component" },
    ref: null,
    type: "div"
}
```` 

What is happening here is: 
1) the jsx gets converted to many React.createElement function calls
2) Each of those functions returns an object similar to the object above

___
# What is a React component?

The definition is: class or a function that outputs an element tree

if it is a function, the output is the return value of the function, if is a class the output is the return value of render method. React components not only has a output, they also have input, the props.

___
# What is a component instance?

- React keeps track of this component by creating an instance of it
- Each instance has a lifecycle and internal state]

#### In function component, we can access the state and the lifecycle using react hooks like useState and useEffect

#### In class components, we make use of predefined methods like componentDidMount and componentWillUnmount, we also use the this keyword whi refers to individual component instance

___

# Reconciliation

- All of what react does is create a tree of elements and this is very fast, because react elements are just plain javascript objects.
- This tree of elements is kept in memory, it is the virtual DOM.
- The next thing to do is to sync the virtual DOM with the real DOM
- During the initial render, there is no other way than to insert the full tree

###### But what if the tree of elements changes?

React once agan very quickly generates a new tree of elements and we now have two trees. I'ts has to once again sync the virtual DOM cointaing the new tree with the real DOM. Would be very inefficient to re-render the whole tree. Then what react does is compares the trees and finds the smallest number of operations to transform one tree into the other. This is handled by the diffing algorithm.

___

# The Diffing algorithm assumptions

1) Two elements of different types will produce different trees
2) When we have a list of child elements which often changes, we should provide an unique "key" as a prop

___

# Rendering

Rendering is handled by packages called renderers (React DOM, React Native, etc.)

React on its own is just a libary that allows us to define components, elements and so on + it does the diffing part

Most of the actual implementation lives in the renders. They begin with reconciliation proccess. They generate the tree of elements and insert it wherever it has to bed inserted

Its extremally important to understand that react React communicates with the renderer
