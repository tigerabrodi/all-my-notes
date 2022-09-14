In this article, I want to share my notes after having finished the course [Master the Code Review](https://curtiseinsmann.com/) by Curtis Einsmann and also share my thoughts on the course.

# Why?

Why did I take the course?

Personally, I'm always hungry to improve in every aspect of software development, and realizing that code reviews is an inevitable process that will be with me throughout my lifetime as a software engineer, I decided to take the course.

I also want to state, that via my own research, there isn't a single resource out there covering what Curtis covers in his course, which is also why I was excited for it.

# Notes

## Forge a better code review process

In order to better write and review code, we first need to setup the process for it.

### Bad reviews

Signs of a bad code review process:

- You are constantly shipping bugs as you ship stuff.
- There are rarely any comments and reviews are being rushed.
- They make members anxious.
- PRs get blocked for minutiae.
- It gets common for PRs to go through many review cycles.
- Long discussion threads happen continously.

### Good reviews

#### Synchronous

Pair reviewing the PR. This is good when you're making fragile changes, and large, complex changes. Ideally, such large complex changes should be avoided whenever possible, as the goal is to not try to make the PRs too big.

This isn't good for finding flaws and defect. It also hurts the individual productivity.

#### Asynchronous

By doing the code reviews async, it increases the individual productivity. The reviewer can focus on the code they are reviewing. Writing comments ensures the reviewer is clear with what they are recommending or commenting on, forces clarity of thought.

The reviewer gets to see the code from a fresh perspective, which also simulates developers seeing the code for the first time.

#### Author expectations

The PR should be small. This makes it easier to review the PR, less risks for bugs, and is time effective for both author and reviewer.

The PR should be able to be shipped with confidence. The builds should pass, it should include tests or extend existing tests.

Include the **what** and **why** in the code review description. What the code does and why a specific solution was implemented (may not be necessary all the time).

Extras you may want to include: Related tickets, issues, test coverage, screen captures, rollback safety, backwards compatibility.

Make sure to assign the right reviewer.

Drive resolution to conflicts, and make sure the PR gets merged.

#### Reviewer expectations

Take ownership and responbility. The code you review should be as if you had written the code. Get to the reviews fast, i.e. two specific times during the day you'd review, mornings and after lunch.

Set high standards and raise the bar for the code, but don't strive for perfectionism, rather be pragmatic. There will always be ways to improve the existing code somehow, remember that our goal is getting the PR merged.

Be kind, and listen to your teammates when they've something to say.

Be thorough, and don't rush through the code. Take ownership of the code, as if it was your own code, it is your pride and will reflect back on you.

Don't comment on style, use linters.

Reasons you'd want to block a PR & request changes:

- Doesn't fulfill all requirements of the ticket.
- Missing tests for new functionality.
- Risks are involved, i.e. merging a PR with a new feature during times where there are loads of traffic, like christmas.
- Obvious readability gaps where it even takes you yourself time to understand what the code is doing.

Don't block PRs over nitpicks and during emergencies.

Utilize **comment and approve** when it is apprioriate and trust that your teammembers will address the comments you made, this also fosters trust between the teammembers.

#### Guidelines

The team should have a document with the code review guidelines.

Guidelines you may want to include:

- When and how to open a code review
- Size and scope of PRs.
- Author and reviewer expectations
- PR templates
- Escalation procedures

### Performance Indicators

How to measure that your code review process has improve.

- Decreased number of defects.
- Decreased number of review cycles.
- Speed of new developer onboarding.
- Discussion quality.

## Give better reviews

### What to look for in a code review?

You first want to look for flaws.

The second thing you want to look for is improving the readability. It is important as other engineers will work on the code, add features on top of the code or change it, hence we don't to make the cognitive effort to work with the code as low as possible.

Look for learning oppoturnities, learning from the author of the PR, the way they wrote the code or how they solved a particular problem, call them out.

#### Before reading the diff

Things you want to look for before reading the diff in detail:

- Make sure the teammate is following the guideline of keeping the PR scoped to the ideal size.
- Make sure builds, checks and tests are in place and pass.
- Make sure there are no merge conflicts, otherwise ask the author of the PR to rebase the branch first.
- Screenshots or PR deployment in place if any frontend has been changed.
- Did they solve the problem the right way? The easiest code to maintain is the code that never gets written. You want to check whether the code was over-engineering or the problem could've been solved by using a service, library, API etc.

#### Flaws within the diff

Look for edge cases and testing within the diff. Make sure the edge cases are covered somehow and the tests properly written.

It doesn't always happen that all business requirements are sorted out before the code gets written, these sort of edge cases are also to look for, ones we didn't think of that we discovered when writing the code.

If there were unexpected changes in the code, ask about why those have been implemented.

Is there any code that could be optimised, if so, is the optimisation important?

Could something be rewritten to be more simple? Always try to favor simplicity whenever possible.

#### Flaws outside of the diff

Be aware of changes that haven't been updated in other places. For example, if you modify a function for your needs, but don't update the usage of this function in other places (ideally this should cause the builds or tests to fail). This also ties to being aware of side effects, changes you may make in the codebase of yours may affect other components of the system, that they might behave differently which causes problems in other places.

Make sure changes that need to be backwards compatible, are being so.

### How to perform a code review

Start off by gathering context. Read the code review description and related tickets. If you aren't the appropriate reviewer, then it is better to assign the review to one of your peers who is more familiar with the place the code was written. Understand whether your peer is optimizing for speed or quality.

When reading the code, read for understanding. Start with the crux, scan the entire diff and find the critical changes. Code isn't written from top to bottom, in a structured way, hence it also makes sense to read randomly and to try understanding how the different pieces work together.

Don't forget, to fully grasp the context, you will likely have to read other code than just the diff, and check out the existing repository code locally to see how changes may be affecting other places in the system.

Write comments as you go, as you try to understand all of the changes and put all the puzzle pieces together. Once you're done, you can rewrite or delete those comments if your assumptions were wrong when you first wrote them. Leave positive comments if the author of the code did something elegantly or taught you something new.

### Writing effective code review comments

Don't use **you** when writing comments. Address the code, not the person. If time allows, you could ask a more open question in some scenarios to let the author come to the solution themselves, pretty useful if you want junior developers to grow.

You should nitpick when reviewing code. Prefix such comments with **Nit, non-blocker:**. Make sure the comment doesn't sound like a command (imperative) and rather a friendly recommendation.

When requesting changes you should have a reason why and explain it thoroughly as well. Depending on the experience of the author, you may find yourself explaining it more verbosely or not.

Sometimes you may want to share more background or information on something by linking it to an article or the documentation.

### Key performance indicators

How to measure that your code reviews are good and having an effect.

- Peers aren't repeating the same mistakes that you've called out.
- Peers are shipping in less reviews over time.
- Teammates are repeating similar comments to the ones you've brought up when reviewing code, this shows you're having an affect on your teammembers.
- You can ask for feedback from your peers, especially ones more senior than you, like your managers/mentors.

## Write better code

### Principles to write better code

3 keys to write readable code:

1. Be empathic. Think of the people that are going to read your code. Favor readability over write conveniance.
2. Be opinionated. Have an opinion for how good could should look like, and a reason behind it.
3. Be intentional with the code you write, make sure the code communicates the intent.

### Process to write better code

You want to create small PRs, do so by taking on smaller tasks. Break down a large task into smaller tasks.

Descriptions that tell a story, doesn't mean they 100% resemble what is happening in reality. Make sure to investigate and set out to do the right thing before committing to the code you're writing.

Pull the latest code, make sure builds and tests are passing before proceeding to check out into a new branch.

Read the existing code, understand the current paradigm and code conventions. Leverage existing examples. Look for opporunities to reuse existing code. You may want to refactor the existing code before implementing the feature, especially if it makes implementing the feature easier.

When coding, make it work (with tests), make it right and make it faster if necessary.

Before submitting the PR, make sure to prepare it. Include the **what** and **why** in the description. Review the code yourself in the web browser and make sure to reread the task and that all requirements have been fulfilled. Make sure builds are passing and there are no conflicts. Don't open a PR at the end of the day, it is better to wake up the next day with a fresh mind and review your PR yourself before opening it for review.

Seek the relentless and thorough reviewer, in order to get a lot of feedback and learn more + faster.

### Addressing code review comments

Reading the comments in monotone will help you not become defensive, reading them as if you were having a conversation with your teammate.

Make sure to clarify and have a path forward before proceeding to do anything. Sometimes what you **think** your teammate is suggesting isn't actually what they have in mind, so be aware of that.

It is important to have the **why** behind every comment. This way you can better decide whether to debate the point or you will understand why something should be changed and won't repeat the mistake in the future.

If a reviewer leaves an incorrect comment on the code, you should of course explain the reason why you did what you did to them. Though, bear in mind oftentimes when the reviewer leaves an incorrect comment, it can mean that your code wasn't **clear** enough on what it was doing. If this is the case, you may want to find a way for the code to be better communicated to the readers of the code.

# My thoughts

The course was phenomenal!

I learned a lot, and from now on will do my code reviews and pull requests differently. I was actually thinking of including a section with mistakes I have done and how I would do them differently from now on, but that'd make the article too long and isn't too interesting.

Curtis went over numerous examples, and even went as far as showing real examples from his work over at Gumroad. I was super happy seeing that because I didn't expect him to show real examples from his own work.

I also liked how he used the descriptions of engineering levels over at Dropbox, and explained the importance of different things he was teaching, in fact before every module he would go in-depth about why you should go through the module.

It was pragmatic, and also taught you some of the soft-skills involved.

I'm very happy to have taken this course, I wish I took it sooner.

It surely has levelled me up as a software engineer by a great amount. Though, I will say if you are i.e. working solo, then you may not benefit from this course.

# Conclusion

If you want to level up yourself as a software engineer, and are working in an environment where code reviews take place, then this course definitly for you.
