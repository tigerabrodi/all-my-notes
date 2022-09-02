In this article I want to speak about why I prefer `const` over `let` when declaring variables in JavaScript.

# Truth about const

Variables declared with `const` often come across as being immutable. Now, if you have written JavaScript for a while, you know that they aren't immutable, rather, they can't be reassigned.

```js
const arr = [];

// This is valid, because we aren't reassigning the variable, but mutating it instead.
arr.push(1);

// This is not valid, because we are reassigning the variable which was declared using const
arr = [22222];
```

# Why const?

You may ask, if both `const` and `let` variables can be mutated/changed, does it really matter which one we pick?

In my opinion, yes it does.

We should stick to `const` whenever we can, and whenever we need to reassign variables, then we should use `let`.

# Problem with reassignment

Reassignments are bad, they are a code smell, they aren't good to write, avoid them whenever you can.

The reason for reassignments being bad goes back to the single responsibility principle.

If a variable is responsible for multiple values, the code gets harder to maintain and the chance for bugs to get introduced are higher.

The mental effort to understand the code when variables have multiple responsibilities is higher, meaning, introducing a higher burden.

This also goes back to the statement that code should be written to be easy to read, not for write convenience.

# Conclusion

This is my take, and some thoughts I've had for a while after seeing people saying it doesn't really matter whether you go with let or const, and some don't even care at all, even if you mix them and things look **not** so nice, to use nice language here.
