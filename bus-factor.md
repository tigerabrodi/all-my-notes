In this article I'd like to go over practices to increase the bus factor of the team.

# What is the bus factor?

The definition Wikipedia gives us:

> The bus factor is a measurement of the risk resulting from information and capabilities not being shared among team members, derived from the phrase "in case they get hit by a bus".

To me, it means more or less: **How many engineers need to be gone before the development either slows down immensly or stops?**

You will have to look at the whole team, and it isn't too difficult to measure.

Example points:

- A single person knows the ins and outs of a part of the system, but others have little knowledge of it.
- A few engineers on the team know the area they work mostly in, but not the other areas, leading to the team feeling dependent on those few engineers due to those parts of the system.

There can be many more scenarios of course, but the point is to increase the shared knowledge on the team, and there are numerous ways we can achieve that. Two major principles:

- Collaborating with different people on the team
- Working in not just a single part of the system, but multiple parts, even if it isn't comfortable.

You may wonder whose responsibility it is to ensure the bus factor is kept high, in my opinion, it is the whole team, but especially the engineering leaders.

Why engineers as well? **Because I believe professionalism in software engineering is more than putting your head down and writing code, it is about making sure that the software & product succeeds short-term and long-term in multiple aspects, and among them is the lifespan and pace of development of the software**.

# Practices

Let's go over practices to increase the bus factor.

## Pair programming

In pair programming, two engineers come together and work on something. Oftentimes one is the driver and the other passenger, meaning, one is the typer and the other behind as a support.

Pair programming is great because the engineers get to collaborate in real-time when working on something. This leads to knowledge being shared through exchanging ideas, discussions & giving each other feedback.

Ideally, pairing partner should be rotated often, so you get to work with different people on multiple parts of the system, and learn from everyone.

## Mob Programming

Mob programming has a few definitions, but the definition I'm going with: Mob programming is when 3 or more engineers on the team get together and work on something.

It is not pair programming, but mob programming.

It is great & can be fun, multiple people learning from one and other.

Points I brought up talking about pair programming could also be said here, about the real-time collaboration for an instance.

## Test-Driven Development (TDD)

If you want an in-depth read about TDD, I recommend this article of mine: [The truth about Test-Driven Development (TDD)](https://tigerabrodi.blog/the-truth-about-test-driven-development-tdd).

By doing TDD, and following the 3 steps of the cycle, we can reduce the cost of change in our software greatly through:

- Testing to achieve confidence
- Refactoring to keep the code clean

Also, tests themselves can serve as documentation when you want to know what a part of the system should be able to do, shouldn't do, and how it responds to i.e. edge cases. In the future, new engineers can refer to the tests when they've to learn more about a part of the system.

## Mob Reviews

Mob Reviews is a practice I introduced in my previous company where after an engineer done with a feature, they would present it quickly to the team. Demoing the feature and also showing the code, how they implemented it from a high-level perspective. I found it amazing, it often lead to discussions and feedback for improvements. I really enjoyed it.

This way features don't get implemented and shipped without engineers on the team missing it, not just how they work of course, but more importantly, how they were implemented.

Mob reviews may not fit for every company or team, but when they do, they are awesome.

## Automate most things

Try to automate most things. Things that you need to do quite frequently, you may want to add documentation for them, **but automating those steps is better, because writing good documentation and keeping it up-to-date over time is NOT the simplest approach**.

There might be things you want to do manually, just make sure to add documentation but be aware that they don't become out-of-date.

## Documentation

There will be things that require documentation, i.e. how to debug a system in a certain environment.

Strive to write good documentation and keep an eye out making sure it doesn't get stale.

It is also good to ask for feedback from your peers when writing documentation, making sure it is understandable and simple.

You may notice you need to either **automate** or **document** something when people consistently ask where to find or how to do something. It is good to document things right away when you know you know that others will have to do the same things following a chronological order.

## Invest in your team

Invest in your team as the title of this section says. Train them, educate them, take them to conferences, book workshops for them where they can learn collectively and more.

You should train your team in areas needed, depending on your software and team:

- Writing code in TypeScript -> Book a TypeScript workshop.
- Using AWS -> Get AWS training for your team members.
- Writing React -> Get your team to go through a course and learn together (collectively).
- Want your team to follow more of the XP practices -> Get them all a book on Extreme Programming and get the team to read through the book together a few times weekly & discuss their learnings.

# Conclusion

There are ways to increase the bus factor within the team. It isn't the easiest problem, but it is also not the hardest.

Keep the bus factor high and increase the lifespan of the software as well as the pace of development whenever members leave and new ones join.
