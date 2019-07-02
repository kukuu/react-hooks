# REACT Hooks

Allows the use of pure functions in REACT with "useStates", but note Hooks do not support traditional REACT Lifecycle states (Side effects).

Example of Side Effects are : Data fetching, setting up a subscription, and manually changing the DOM in React components are all examples of side effects.

Hooks allows  you to write  less code.

##  useEffect

useEffect is a React hook which accepts a callback as it’s the first argument. Inside the first argument, we do all the effect related tasks.

Life cycle are used to free up resources due to asynchronous nature i/o, non-blocking single threaded nature of JS.

Also, not the use of setters as second parameters in the array definition to useState in the initial de-structuring, and setting initial default values/states.

1. With CLASS

```

import React, { Component } from "react";

export default class Planets extends Component {
  state = {
    hasErrors: false,
    planets: {}
  };

  componentDidMount() {
    fetch("https://swapi.co/api/planets/4/")
      .then(res => res.json())
      .then(res => this.setState({ planets: res }))
      .catch(() => this.setState({ hasErrors: true }));
  }

  render() {
    return <div>{JSON.stringify(this.state.planets)}</div>;
  }
}

```

2. With Pure Functions (Hooks)

```
import React, { useState} from "react";

const Planets = ()  => {
  const  [hasError, setErrors] =  useState(false)
  const  [planets,setPlanets ]= useState({})

  componentDidMount() {
    fetch("https://swapi.co/api/planets/4/")
      .then(res => res.json())
      .then(res => this.setState({ planets: res }))
      .catch(() => this.setState({ hasErrors: true }));
  }

  return (
     <div>{JSON.stringify(planets)}</div>
  )
}

export default  Planets;


```

3. With useEffect

```
import React, { useState, useEffect } from "react";

const Planets = () => {
  const [hasError, setErrors] = useState(false);
  const [planets, setPlanets] = useState({});

  useEffect(() =>
    fetch("https://swapi.co/api/planets/4/")
      .then(res => res.json())
      .then(res => this.setState({ planets: res }))
      .catch(() => this.setState({ hasErrors: true }))
  );

  return <div>{JSON.stringify(planets)}</div>;
};
export default Planets;

```


4. Moving from this.setState({}) to hooks:

Notice how we put a function inside the callback. The function is named fetchData and does exactly it’s named.

```
import React, { useState, useEffect } from "react";

const Planets = () => {
  const [hasError, setErrors] = useState(false);
  const [planets, setPlanets] = useState({});

  useEffect(() => {
    async function fetchData() {
      const res = await fetch("https://swapi.co/api/planets/4/");
      res
        .json()
        .then(res => setPlanets(res))
        .catch(err => setErrors(err));
    }

    fetchData();
  });

  return (
    <div>
      <span>{JSON.stringify(planets)}</span>
      <hr />
      <span>Has error: {JSON.stringify(hasError)}</span>
    </div>
  );
};
export default Planets;

```


5. Moving fetchData out of the hook entirely.


```
import React, { useState, useEffect } from "react";

const Planets = () => {
  const [hasError, setErrors] = useState(false);
  const [planets, setPlanets] = useState({});

  async function fetchData() {
    const res = await fetch("https://swapi.co/api/planets/4/");
    res
      .json()
      .then(res => setPlanets(res))
      .catch(err => setErrors(err));
  }

//Call a function in a function. Pure functions
  useEffect(() => {
    fetchData();
  });

  return (
    <div>
      <span>{JSON.stringify(planets)}</span>
      <hr />
      <span>Has error: {JSON.stringify(hasError)}</span>
    </div>
  );
};
export default Planets;

```

6. Note; If you want the useEffect to behave like the componentDidMount lifecycle event, pass an array as the second argument, like so;

```
useEffect(() => {
  fetchData()
}, [])

```


The second argument will be dependencies for that effect. If one of the dependencies has changed since the last time, the effect will run again.



7. If all files are in place and your application is not executing.

Try:  

i. Create .env file in the top directory

ii. Insert - SKIP_PREFLIGHT_CHECK=true
