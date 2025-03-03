When it comes to react performance, it's really re-render of react components.

And when it comes to component re-renders, there are 3 aspects of it:

1. heavy computation
2. scope
3. frequency

## Profiler

`<Profiler />` is a built-in component in React, useful for profiling a component's re-renders.

see: https://react.dev/reference/react/Profiler

## optimize for heavy computation

A react component is just a normal function, everytime it renders, the function is executed.

If there's a heavy computation in the process, you'd want to only execute it when necessary.

For this you can use `useMemo`.

## optimize for scope

By default, everytime a component re-renders, all sub components under it will re-render even if its props haven't changed.

So a general rule of sum is to scope state only to the component that absolutelu needs it.

This problem is particularly common in context (since in the setup process of context, you'd wrap components with a context provider components). So don't over use context.

To share state and only update components that uses the shared state, consider using publish-subscribe based state containers such as `zustand`.

You can also use `memo` to wrap components, basically telling react to not re-render the component if its props haven't changed.

## optimize for frequency

This is a case-by-case optimization.

First you need to identify excessive re-renders and find out what's causing it.

Since frequency is a time related concept, you'd most want to limit rate of state change using techniques such as `debounce` or `throttle`.





