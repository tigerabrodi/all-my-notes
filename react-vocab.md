In this article I want to go over terms in React that you may have heard but never fully understood. I hope this shines some clarity and helps you better learn and understand React as you hear these terms.

# Render phase

React breaks up the work it has to do to render your app in two phases, the render and commit phase.

During the render phase React executes all of your components and gets a JSX tree as a result. If it is the first time React renders your app, it will just return the entire JSX tree.

INSERT IMAGE

If it is a re-render (update) React is going to get the new JSX tree and compare it with the old one and compute a diff. This is called **reconciliation**.

INSERT IMAGE

# Commit phase

# State

# Side effects

# Purity

# Idempotence

# Conclusion

I hope this helped!

Continue shipping amazing web applications.
