In react, we have some basic concepts, they are:

Reconciliation:

Virtual DOM:

Rendering:

Diffing Algorithm:

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
```

What is happening here is: 
1) the jsx gets converted to many React.createElement function calls
2) Each of those functions returns an object similar to the object above


<------------------------------------------->

What is a React component?