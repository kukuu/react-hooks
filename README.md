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

 If you write a function component and realize you need to add some state to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function component. We’re going to do that right now!

For example, In a function component, we have no this, so we can’t assign or read this.state. Instead, we call the useState Hook directly inside our component:

## More reading 

 1. https://reactjs.org/docs/hooks-state.html 

2. https://reactjs.org/docs/hooks-state.html
