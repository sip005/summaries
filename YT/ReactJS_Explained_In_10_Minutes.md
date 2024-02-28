# [React JS Explained In 10 Minutes](https://youtu.be/s2skans2dP4?si=nGOTp52Lxba-gIwn) 

1. Single page application - With react we can build singlel page application easily. in our traditional websites we have templates for each of our pages and we return them when requested. But single page application we are working with one single template and only updating the DOM with different components in that template.  

2. Components - It splits up our visual layer and ui into reuseable contents. Each part of our ui will be built out in separate componets and then added into ui for specific page. Component is a javaScript class or function that returns html which is known as JSX. Components can be nested as deep as we want, one component can hold another component, that can hold another components. There are two types of components, 1-Class based components, 2-Function based components.  

3. JSX - Instead of writing traditional HTML tags, in react we will be using something call `JavaScript XML`. JSX looks a lot like HTML with slight syntax differences. Which gives few functionalities such as inside of curly braces `{}` we can use variables, we can give chance to us JS logics directly in HTML. JSX tags are similar to HTML tags, where in JSX we add classnames and handle events in a different manner. Browsers can not read jsx, so the code will be run through `Transpiler` first then will be converted into HTML and JS.  

4. URL Routing - React router is way of having multiple page in single page, we actually dont change pages so router takes the responsibity of updaing and refashing the pages, UI is insync with urls router will take care of the components

5. Props - when we need to passdown data one componet to another we will use props, it is like function parameter, props are passed down data componet to component. Onec prop is passed we can use it anywhere in components, it can be passed multiple layer, which is called prop drilling

6. State - it is a js object used for representing information about particular components. Traditionally we use class based component to set the values, Now a days we use react hook, state to create component state. we can loop through state using map, also we can initialize state, update using empty array

React hooks with usestate to create component state.

7. component lifecycle - a react componet has lifecycle, usually react component has four parts initialization , mounting, updating, unmounting. In the class lifecycle we have -  componentDivMount, componentDivUpdate, componentDivUnmount, with the functional we use useeffect for the lifecycle

8. React hooks - It allows us to add state without using the class based components. before hooks functional components could not hold any state. Hooks are simply functions that allows us to hook into stae and manage them. Most common types of hooks are 1. useState() // --> Set and update state
2. useEffect() // --> perform side effecting in lifecycle 

React gives us whole set of hooks with the ability create custom hooks  

9. state management - component state and global state. To make the data available across multiple places we use the state. there is builtin context api or we can use Redux for this. for example take logged in user we may need to user data in multiple places across several components

10. Virtual dom - How react builds and update the component, 

11. keyprop - each dynamically updated data should have key prop, it should be uniqe

12. Event listeners - handleing event with react is very smilar to the JS event listeners

13. Handling froms

14. conditional rendering

15. Commands 