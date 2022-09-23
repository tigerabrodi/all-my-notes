So, this article is a bit different. These are my notes and thoughts I've written down as I've gone through each chapter of the book **A Philosophy of Software Design**.

The difference here compared to other notes I've taken is that I'm writing down my opinions and thoughts.

# Introduction

I agree that the greatest limitation in writing software is understanding our systems, especially as they grow, not just understanding them but also making sure they work correctly is definitly one of the great challenges when building scalable systems.

Complexity is inevitable when writing software, as the software grows, it will continue to grow.

The author speaks about two approaches to fighting complexity, one is to eliminate it and the other is to encapsulate it, to develop a system that is divided up into modules.

I find it super interesting how in the early days of software engineering, people tried approaching it using the Waterfall method since it works great in many other fields. We've come to the conclusion though that it doesn't work well because designing and developing software is a process that never ends.

When you think of a building, oftentimes it'll be architected and planned out, then built, and eventually just be left there. Software engineering is truly a different craft from other engineering fields, also considering how unique it is since there is no limit to the creativity.

# The Nature of Complexity

I never thought of it personally, but I completely agree, the ability to recognize complexity has to be one of the best design skills in software engineering. When you think about it, one wrong choice can have a negative effect on the entire system.

The author defines complexity as:

> Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system.

Makes sense.

> You can also think of complexity in terms of cost and benefit. In a complex system, it takes a lot of work to implement even small improvements. In a simple system, larger improvements can be implemented with less effort.

I completely agree here, systems that are hard to work with and change, that is when you know the complexity is quite high. Such systems are always a pain to work with, especially when they don't include tests. That's even worse in my opinion, when you can't work with the tests too, then you know it will take a long time to get anything done.

> If you write a piece of code and it seems simple to you, but other people think it is complex, then it is complex.

This is such an important point. Many engineers forget that building software is a team effort, and you aren't the only one who is gonna be reading your code. Code is more read than written, and read not by you, but by your team members, hence make sure the code is readable for everyone, or at least strive to do so.

This is also one of the points that makes me shout **pair programming**. Pair programming helps here a ton. I should probably write a separate piece about pair programming itself, because there are so many things I could talk about when it comes to it.

The author speaks about the symptoms of complexity.

1. Change amplification: Simple changes require code modifications in many different places.
2. Cognitive load: Developers have to spend more time learning the require information, understanding the existing code and keeping that in your head when working with it.
3. Unknown unknowns: It is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully.

> Sometimes an approach that requires more lines of code is
> actually simpler, because it reduces cognitive load.

Goes back to the point that code is more written than read, don't write code that is easy to write, write code that will be easy to read.

The author mentions complexity is caused by two things: dependencies and obscurity.

The author brings up a strong point about dependencies, it is inevitable, but we should strive to reduce them.

> one of the goals of software design is to reduce the number of dependencies and to make the dependencies that remain as simple and obvious as possible.

# Working Code Isn’t Enough

The author speaks about tactical and strategic programming, and says that most programmers approach writing software with a mindset he calls tactical programming, where your main focus is to get something working.

> The problem with tactical programming is that it is short-sighted. If you’re programming tactically, you’re trying to finish a task as quickly as possible. Perhaps you have a hard deadline. As a result, planning for the future isn’t a priority. You don’t spend much time looking for the best design; you just want to get something working soon.

This reminds me of my younger self, perhaps even my current self depending on the situations, but yeah, this approach is quite dangerous.

Interesting, the author speaks of the tactical tornado, the programmer on the team who is able to pump out code and features faster than everyone on the team. They could even at times often be seen as the heroes of the team, but in reality they are doing more bad than good, considering the mess and complexity they will leave behind.

> Strategic programming requires an investment mindset. Rather than taking the fastest path to finish your current project, you must invest time to improve the design of the system. These investments will slow you down a bit in the short term, but they will speed you up in the long term.

It is a good point, invest time in understanding what is required to implement the feature, not just get it working but also change the existing design of the software for the better.

# Modules Should Be Deep

> For the purposes of this book, a module is any unit of code that has an interface and an implementation.

This is nice, makes sure that the book isn't just relevant for object-oriented code.

A clearly specified interface helps eliminate the **unknown unknowns** problems.

> An abstraction is a simplified view of an entity, which omits unimportant details.

There are two ways an abstraction can go wrong:

1. Include details that are not really important. -> Increased cognitive load.
2. Omits details that are really important. -> Results in obscurity.

This reminds me of the single-responsibility principle, not entirely, but if we make sure each abstraction does the thing it says it does, then we wouldn't encounter both problems above, though this is also taking into account that it include **only** the necessary details.

> Deep and shallow modules. The best modules are deep: they allow a lot of functionality to be accessed through a simple interface. A shallow module is one with a relatively complex interface, but not much functionality: it doesn’t hide much complexity.

Interesting, I never thought of it, but it completely makes sense, when I look back at the technologies I've used myself and their APIs. Some are easy to use and understand, some provide a great amount of functionality but feel more low-level and are complex to work with.

> A shallow module is one whose interface is complicated relative to the functionality it provides. Shallow modules don’t help much in the battle against complexity, because the benefit they provide (not having to learn about how they work internally) is negated by the cost of learning and using their interfaces. Small modules tend to be shallow.

I never thought of shallow modules this way, but I agree with the point that an interface that is more complicated than the functionality it provides isn't helping since it just increases the cognitive load.

# Information Hiding (and Leakage)

The author mentions information hiding as the most important technique for achieving deep modules. A module's knowledge is embedded in the module's implementation but does not appear in its interface.

> When designing a new module, you should think carefully about what information can be hidden in that module. If you can hide more information, you should also be able to simplify the module’s interface, and this makes the module deeper.

Information leakage is an interesting red flag, I've never thought of it or read it elsewhere I won't lie. It happens when a design decision is reflected in multiple modules.

> Information leakage occurs when the same knowledge is used in multiple places, such as two different classes that both understand the format of a particular type of file.

Temporal decomposition is something I rarely have come across or seen, if never honestly throughout my development career (might just be my bad memory).

> In temporal decomposition, execution order is reflected in the code structure: operations that happen at different times are in different methods or classes. If the same knowledge is used at different points in execution, it gets encoded in multiple places, resulting in information leakage.

By hiding more information of a module, it tends to increase the amount of functionality provided by the module and reduce its interface. Modules that don't hide much information on the other hand, wouldn't provide much functionality or it has a complex interface.

# General-Purpose Modules are Deeper

The author says from his experience the sweet spot is to implement modules in a somewhat general-purpose way. So instead of implementing it in a way that reflects on the current needs, you make it a bit generalised. The author also clarifies saying the functionality should be for today, but the interface should be general enough to support multiple uses.

He claims that the benefit of the general-purpose approach is that it results in simpler and deeper interfaces than a special-purpose approach.

Honestly, I could see that being the case, but I'd have to see it practically myself in my career to be completely convinced. I'm a huge fan of YAGNI, and have always strongly adhered to implementing modules that reflect on their current needs.

I will make sure to keep this mind, and think about it as I'm implementing modules, to me it is super interesting that the author's takes, at least from books I've read (read over 40 books last year), are different, not in a negative way, but in a way that the standard isn't used to in the industry, especially when we think of books like Clean Code and methodologies like TDD for example.

> The general-purpose interface also reduces cognitive load: a developer working on the user interface only needs to learn a few simple methods, which can be reused for a variety of purposes.

The author brings up how generality leads to better information hiding, which I can see be the case.

# Different Layer, Different Abstraction

The author explains that in a well-designed system each layer of the system provides a different abstraction from the layers above and below it.

He brings up the pass-through method as a red flag here.

> A pass-through method is one that does nothing except pass its arguments to another method, usually with the same API as the pass-through method. This typically indicates that there is not a clean division of responsibility between the classes.

The author brings up a similar problem which is pass-through variable, when a variable just keeps getting passed down, from function to function. This reminds me of prop-drilling in React, and in fact, the author suggest the same solution which is to introduce a context object where you can use its data throughout the whole hierarchy.

Though, in React, you should try colocating the state before extracting it to some sort of global solution.

# Pull Complexity Downwards

The author in this chapter seems to be emphasizing the importance that you suffer more than the users of your module.

> As a module developer, you should strive to make life as easy as possible for the users of your module, even if that means extra work for you. Another way of expressing this idea is that it is more important for a module to have a simple interface than a simple implementation.

He brings up configuration parameters leading to increased complexity of the system, ideally each module should solve a problem completely.

This reminds me of inversion of control as well as optional parameters, though, oftentimes optional parameters mean that a module **can** have multiple responsibilities. I won't say I'm not writing them myself even though I'm a huge fan of the single-responsibility principle, but I try to make sure my abstraction/module solves **one** particular problem well, sometimes it will mean it is gonna have a few more responsibilities.

# Better Together Or Better Apart?

The author speaks about whether you should implement multiple functionalities in the same place or their implementations should be separated.

> Bringing pieces of code together is most beneficial if they are closely related. If the pieces are unrelated, they are probably better off apart.

He mentions points for when to bring functionalities together:

- Bring together if information is shared
- Bring together if it will simplify the interface
- Bring together to eliminate duplication

> If the same piece of code (or code that is almost the same) appears over and over again, that’s a red flag that you haven’t found the right abstractions.

I can sort of relate to this. Every time I try to create an abstraction, but I don't know what exactly to abstract or what pieces, that makes me realize I haven't found the sweet spot for the right abstraction to create.

Another thing the author mentions is that oftentimes it is better to join methods. A red flag he brings up is Conjoined Methods:

> It should be possible to understand each method independently. If you can’t understand the implementation of one method without also understanding the implementation of another, that’s a red flag. This red flag can occur in other contexts as well: if two pieces of code are physically separated, but each can only be understood by looking at the other, that is a red flag.

# Define Errors Out Of Existence

Exceptions in systems are inevitable. In this chapter, the author speaks about the complexity that comes with handling exceptions. He brings up that throwing exceptions is easy, but handling them is hard.

> The best way to reduce the complexity damage caused by exception handling is to reduce the number of places where exceptions have to be handled.

He says that the best way to eliminate exception handling is defining your APIs so that there are no exceptions to handle at all.

Another approach is exception masking, where exceptions are detected and handled at a low level in the system, this is quite common in distributed systems.

The third technique is exception aggregation, where you'd handle many exceptions with a single piece of code, rather than writing multiple handlers for many individual exceptions.

# Design it Twice

An approach to figure out the best design for a module or abstraction is by designing it twice, in two different ways. It is easier to identify the best approach if you can compare a few alternatives, than just implementing the one that came to your mind.

# Why Write Comments? The Four Excuses

This is an interesting chapter, because personally, I think comments should be avoided and only used in cases where it is necessary to explain the **why**.

> the process of writing comments, if done correctly, will actually improve a system’s design.

> If users must read the code of a method in order to use it,
> then there is no abstraction: all of the complexity of the method is exposed.

I completely agree here. If I create methods i.e. in a library or so at work, I'll add comments as documentation for the method, we use JavaScript at work, so I'd add JS DOC as documentation. It makes it easier to use the method and understand how to work with it.

> Comments do sometimes get out of date, but this need not be a major problem in practice. Keeping documentation up-to-date does not require an enormous effort.

I disagree strongly here, and this is exactly the mentality that gets developers writing a bunch of comments and never keeping them up to date. In my previous company, there were so many comments, and many of them were completely out-of-date.

To me a comment is a red flag, it makes my eyes go wide and see whether it is necessary or not. Many times I've rewritten code to be more clear, which has lead to removing the comments of the code.

> The overall idea behind comments is to capture information that was in the mind of the designer but couldn’t be represented in the code.

# Comments Should Describe Things that Aren’t Obvious from the Code

> The guiding principle for comments is that comments should describe things that aren’t obvious from the code.

I'm not entirely sure about this, because if this was really the case, then are we supposed to add comments everywhere? I don't think so.

> Developers should be able to understand the abstraction provided by a module without reading any code other than its externally visible declarations. The only way to do this is by supplementing the declarations with comments.

This makes more sense, that modules/abstractions should be documented, like using JS DOC for an instance which I mentioned before.

The author brings up comments that repeat the code as a red flag, which to me completely makes sense, without a doubt and I agree. I wish it was obvious for more people.

He proceeds to show some comments as good examples which I disagree with, for an instance below explaining that the value is in pixels:

```c
/*
* The amount of blank space to leave on the left and
* right sides of each line of text, in pixels.
*/
private static final int textHorizontalPadding = 4;
```

Just rename the variable if that is such an important information, this is in my opinion a bad comment, get rid of it, it just another 4 lines that brings no value.

> If you want code that presents good abstractions, you must document those abstractions with comments.

I can agree with this, going back to JS DOC as mentioned before, makes sense.

He brings up another red flag which happens when the comments describe the implementation details of an abstraction, which I also agree with, because that removes the value the comment would've brought.

> The main goal of implementation comments is to help readers
> understand what the code is doing (not how it does it).

Makes sense, if we're speaking about adding comments to an abstraction, not **any** code.

# Choosing Names

This chapter is probably gonna be my favorite one haha. Naming is such an interesting topic in software engineering, because the effect bad and good names have, whether it'd be variables, methods, classes, files etc. have a difference, and oftentimes the difference is quite big.

Good names will result in less cognitive load, understanding and working with the code.

> If a variable or method name is broad enough to refer to many different things, then it doesn’t convey much information to the developer and the underlying entity is more likely to be misused.

I completely agree here, variable names should be precise and specific, they shouldn't be confusing.

> If it’s hard to find a simple name for a variable or method that creates a clear image of the underlying object, that’s a hint that the underlying object may not have a clean design.

# Write The Comments First

The author really loves comments. He states that the best time to write them is at the beginning of the process as you write the code, and that delayed comments are bad comments.

Honestly, I'm confused and will still hold my stance that comments should be avoided, though, they can be used as documentation for abstractions or methods using the convention of the language, like in JavaScript for example that'd be JS DOC.

> The comment that describes a method or variable should be simple and yet complete. If you find it difficult to write such a comment, that’s an indicator that there may be a problem with the design of the thing you are describing.

I can see this to be the case. I also want to point out, the author seems to be referring to comments of a class or abstraction, and not just any comments, I'm writing these notes as I'm reading.

# Modifying Existing Code

> If you want to maintain a clean design for a system, you must take a strategic approach when modifying existing code.

Interesting point, being strategic when modifying existing code. When I think about it, I should probably spend more time thinking about the design of the software, and alternatives before I decide to go ahead and refactor existing code.

> Whenever you modify any code, try to find a way to improve the system design at least a little bit in the process. If you’re not making the design better, you are probably making it worse.

I completely agree here, always try to find ways for the existing code and design to be improved.

# Consistency

> Consistency is a powerful tool for reducing the complexity of a system and making its behavior more obvious. If a system is consistent, it means that similar things are done in similar ways, and dissimilar things are done in different ways

I agree here, consistency is king. If you're consistent with the ways you write the code, the cognitive load for working with the code and understanding its patterns is less than if it was to be inconsistent.

> Consistency allows developers to work more quickly with fewer mistakes.

# Code Should be Obvious

> If code is obvious, it means that someone can read the code quickly, without much thought, and their first guesses about the behavior or meaning of the code will be correct. If code is obvious, a reader doesn’t need to spend much time or effort to gather all the information they need to work with the code. If code is not obvious, then a reader must expend a lot of time and energy to understand it.

When it comes to complexity in software, it all goes back to cognitive load. How much mental effort does it take to understand the code and the design of the software?

> If the meaning and behavior of code cannot be understood with a quick reading, it is a red flag. Often this means that there is important information that is not immediately clear to someone reading the code.

When writing software, know that code is more read than written. Software should be designed for ease of reading, not ease of writing.

# Test-driven development

The author states that he is a strong advocate of unit testing, but not a fan of TDD.

> The problem with test-driven development is that it focuses
> attention on getting specific features working, rather than finding the best design.

I haven't practically encountered times where this has been an issue, in fact, during the refactoring stage of TDD when I end up improving the software's design.

He says it makes sense to do so when fixing a bug for an instance, in order to make sure you've fixed the bug.

Personally, I'm a fan of TDD. I enjoy writing Cypress tests that resemble the way my users are gonna use a feature of my product, and seeing that test fail, then implementing the feature and eventually refactoring. Sometimes I'll implement the test and feature bit by bit, it depends.

# Conclusion

The book was phenomenal, the best book I've read this year. I would put this as my top 5 software engineering books. It is about managing complexity, which is one of the hardest things in software engineering, because complexity is inevitable as the system grows, but how to manage it effectively is tough.

I agreed with most of the things, learned new things, and the author also opened my perspective on certain things. I loved how he consistently throughout the book showed practical examples, and the book itself wasn't specific to a particular programming language, so it was an enjoyable and learningful read.
