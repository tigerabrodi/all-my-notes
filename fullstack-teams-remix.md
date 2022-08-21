# Intro

In this article, I want to talk about being on a team of full-stack developers using Remix, and how we are able to move faster than other teams, with Remix specifically.

## My previous experience

In my previous company, Tonies, the backend and frontend developers were separated, there were two different teams.

A lot of companies work this way, now, this is my previous experience, but I'm quite sure this happens for many other companies too, let me elaborate.

One issue we had, which already led to the development being slower, was the communication back and fourth with the backend team.

Issues that would regularly (at least every other week if not monthly) occur which caused time to be wasted or slowed down the team:

- Something isn't done on the backend, hence a task is blocked.

- A backend API was not complete, leading to unnecessary debugging time and further communication with the backend team.

- Miscommunication between both teams.

Obviously, you can tell over time, how much time has been wasted, that could've gone into shipping features and delivering user value.

## My current experience

At Bobsled we're using Remix for our product, which covers both the backend and frontend side of things.

Obviously, the first thing which goes away as with any fullstack teams, is the communication between frontend and backend.

As for writing tests, at Bobsled, we write E2E Tests with Cypress mainly. We don't need to write tests for every single API, which people would often end up having to do at the backend. We write our tests resembling the user, hence getting the most confidence out of them.

When a member on the team needs to implement a feature they can just go from A to Z and implement it.

### Remix

With Remix specifically, its simplicity makes everything SUPER nice. You could imagine every file being really bloated, but the nice part with Remix is how easy it is to scale down with it.

In every single route (file), we can have all the logic. Fetching data, mutating data, handling expected and unexpected errors, and also rendering the HTML (JSX). Despite all that, the code and the structure of the code is quite simple, and we aren't forced to write a bunch of boilterplate in case we want to scale down and wouldn't need all of the logic.

Another thing with Remix is how it handles data fetching with its loaders, the hook `useMatches` and nested routing. This makes working with Remix really nice, the fact that a lot of the stuff you'd seek to complete a stack, is already included for you by default, in a way that scales both up and down.

## Conclusion

I love Remix, and I think it is a great fullstack web framework, that has the centrlized bridge between backend and frontend, and the data that gets shared between both parts.

Remix is awesome, and it lets us focus on implementing the actual features, and not writing more code than necessary to do so.
