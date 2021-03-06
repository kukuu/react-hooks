# REACT Hooks - An alternative to classes

```
1. React Hooks allows you to add local states to functional components.

2.  Allows you to hook into REACT states and cycles. 

3. With functions when you exit, variables are destroyed. 

4. Which is not how REACT works. So the use of Hooks like user data 
allows you to preserve local states on re-render.

5. React Hooks are simple functions that work in conjunction with the React dispatcher.
As such, they need to be called at rendering time (of the respective component),
and they have to appear in the same order. 

6. React Hooks should never be inside a condition or loop. 

7. They can only be used by functional components.

```
## What does it do?

A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components. 

 If you write a function component and realize you need to add some state to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function component.

For example, In a function component, we have no this, so we can’t assign or read this.state. Instead, we call the useState Hook directly inside our component.

## Refactoring a React class to a React Hook

Open  App.js file and turn it into a Hook. Refactor your App.js to the following:
Basically just turn the class into an arrow function and delete the render method. 

```
import React, { Component } from 'react';
import Routes from './routes';

const App = () => {

    return(
      <div>
      React
      <Routes />
      </div>
    )
}

export default App;

```

```
import React, { useState } from 'react';

const HooksContainer = () => {

    return(
      <div>

      </div>
    )
}

export default HooksContainer;`

```

The useState() hook is similar to the React setState() function. It is setup with array destructuring, where the first element in the array is the state value and the second element is a function to change the state i.e:


``` 
const [value, setValue] = useState(0)

```


## STATE MANAGEMENT

React comes with built-in hooks to manage local state: useState, useReducer, useContext. All of these can be used for sophisticated local state management in React. 

All of React's built-in hooks are great for local state management. When it comes to state management of remote data,  recommend to use Apollo Client, if the remote data comes with a GraphQL endpoint. Alternatives for Apollo Client are urql and Relay.

If the remote data doesn't come from a GraphQL endpoint, try to manage it with React's Hooks. If it doesn't work out, a solution like Redux or MobX/Mobx State tree may help.

### Recommendations:

1. Local State: React's useState, useReducer, useContext Hooks

2. Remote State via GraphQL: Apollo Client

3. Remote State via REST: React Hooks or Redux/MobX/Mobx State Tree

## Counter with Hooks

In the example below the counter has been purely created from Hooks without the use of "props" and "state" keywords. 
We have used variable and function name directly.

```

import React, { useState } from 'react';

const HooksContainer = () => {

  const [value, setValue] = useState(0) //destructuring. Array of 2 signatures: i. value/state and a function(setter).

  const incrementValue = () => {
    setValue(value + 1 )
  }

  const decrementValue = () => {
    setValue(value - 1 )
  }

    return(
      <div>
      //You can call the function directly
        <button onClick={() => incrementValue()}> Add Local Value </button>
        <button onClick={() => decrementValue()}> Dec Local Value </button>
        <br />
        <div>
          Local React State: {value}
        </div>
      </div>
    )
}


export default HooksContainer;

```

## More reading 

 1. https://reactjs.org/docs/hooks-state.html 

2. https://reactjs.org/docs/hooks-state.html 

3. https://www.taniarascia.com/crud-app-in-react-with-hooks/comment-page-1/#comment-11850 

4. https://blog.logrocket.com/building-carousel-component-react-hooks/
