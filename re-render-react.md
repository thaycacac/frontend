# How/When does React re-render? Virtual DOM? What is React's reconciliation? -> Two phases commit?

## Re-render can be caused due to any of the three reasons listed

- Update in State
- Update in prop
- Re-rendering of the parent component

## Why do components get re-rendered?

- **Update in state**: The state change can be from a prop or setState change to update a variable(say). The component gets the updated state and React re-renders the component to reflect the change on the app.
- **Update in prop**: Likewise the change in prop leads to state change and state change leads to re-rendering of the component by React.
- **Re-rendering of parent component**: Whenever the components render function is called, all its subsequent child components will re-render, regardless of whether their props have changed or not.

## What is the Virtual DOM?

The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called reconciliation.

This approach enables the declarative API of React: You tell React what state you want the UI to be in, and it makes sure the DOM matches that state. This abstracts out the attribute manipulation, event handling, and manual DOM updating that you would otherwise have to use to build your app.

Since “virtual DOM” is more of a pattern than a specific technology, people sometimes say it to mean different things. In React world, the term “virtual DOM” is usually associated with React elements since they are the objects representing the user interface. React, however, also uses internal objects called “fibers” to hold additional information about the component tree. They may also be considered a part of “virtual DOM” implementation in React.

## What is React's reconciliation?

[https://reactjs.org/docs/reconciliation.html](https://reactjs.org/docs/reconciliation.html)

## Two phases commit?

The lifecycle has three main sections:

- **Mounting**: Runs once when the component is created.
- **Updating**: Runs each time a change is made to the component.
- **Unmounting**: Runs once when the component is about to be destroyed.

There are also three phases, which run multiple times during the lifecycle:

- **Render phase**: Is used to calculate changes, and may be aborted if the user wants to. If this phase is aborted the DOM isn’t updated.
- **Pre-commit phase**: Is a period where you can read changes made to the VDOM, before they are applied to the actual DOM. To learn more about the VDOM I recommend this article.
- **Commit phase**: Here the changes are applied and any side effects are triggered.
