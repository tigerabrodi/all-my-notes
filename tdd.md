In this article, I'd like to go over why I do TDD. I think TDD is nice, but there will always be developers who choose not to do it, for their own reasons. So we can conclude saying it is a great strategy for writing code, but may not fit or work for everyone. Also, I don't believe in absolutes, because if we look throughout human history, new or better things have been discovered by being curious and open-minded, instead of believing in something as being an absolute, and just sticking with it.

# What is TDD

Before we dig into why I do TDD, I'd like to talk about what it is. I'll keep things short and from a high-level point of view since there are plenty of resources out there already about what Test-Driven Development is.

To me, I'd describe TDD as a methodology for writing software where you guarantee quality by following a cycle consisting of 3 steps.

1. Write a failing test. -> Make it fail.

2. Write code to make the test pass. -> Make it work.

3. Refactor the code -> Make it right.

IMAGE BELOW

# Why I do TDD

Let's dig into why I enjoy doing TDD.

## User's perspective

When I begin by writing my tests, my focus shifts from being the person that implements the feature to being the user. Now, this may not apply to every single level of test that you write. For an instance, when I write an E2E Test or an integration test where I resemble the user, that allows me to shift my perspective to being the user. I find it interesting because I can see the feature from a different angle.

This could be subjective, but this is how I feel when I begin by writing a failing test, and I do like this way of thinking, it forces me to think of customers in that position, and how they would end up using the feature. Sometimes during these moments I come up with ideas that could improve the user experience.

If you're for an instance building a library, you may write tests for a specific API that your users (developers in this case) would use, it may apply in that scenario as well.

## Negative state & one thing

I like beginning with a negative state. By beginning with a failing test, there is something to fix, more precisely, there is ONE thing to fix. Now, it doesn't mean you're fixing a bug, but it could be writing code for a feature. Still, I love how TDD let's me focus on ONE thing at a time, because after the failing test, the **second** step is to write code to make it pass.

By the way, in the second step, the code isn't supposed to be great, the focus is to get the test to pass.

## Refactor phase

The third step of TDD is the refactoring phase. After you've gotten the failing test to pass, it is time to improve the existing code. By refactoring, I mean improve the existing code & software design without changing the behavior of the system. I **love** this phase of TDD, this is the phase that completes the cycles and really makes sure you ship with QUALITY.

This also makes sure to keep the cost of changing or adding code at a low level (cognitive effort).

I wrote an article about refactoring if you're interested in reading more after this article: [Lessons and takeaways on Refactoring](https://tigerabrodi.blog/lessons-and-takeaways-on-refactoring).

## Quality makes customers happy

Now that we've seen how TDD helps you ship quality software, or at least my perspective on it, you may wonder how quality makes customers happy? Why do customers become happy when software engineers ship quality software? How do they experience or see that?

To me, it is quite straightforward:

- Less bugs.
- Bugs discovered get fixed and prevented.
- Features can get added quite quickly due to the low cost of adding new code.
- You can modify existing code with confidence and not fear because of the tests already in place.

# Conclusion

Test-Driven Development is awesome and I love it. You should give it a shot if you haven't tried it out.

It is really fun to do when you're fixing a bug, because you can reproduce the bug in the test, and make sure it fails, and just focus on fixing the bug. The test will give you feedback whether you've fixed the bug or not.
