# REACT Hooks - An alternative to classes

```
1. React Hooks allows you to add local states to functional components.

2.  Allows you to hook into REACT states and cycles. 

3. With functions when you exit, variables are destroyed. 

4. Which is not how REACT works. So the use of Hooks like user data 
allows you to preserve local states on re-render.

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

## Counter with Hooks

In the example below the counter has been purely created from Hooks without the use of "props" and "state" keywords. 
We have used variable and function name directly.

```

import React, { useState } from 'react';

const HooksContainer = () => {

  const [value, setValue] = useState(0) //destructuring

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
