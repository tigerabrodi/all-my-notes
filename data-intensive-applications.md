# Chapter 1

Reliability, Scalability and Maintainability.

Reliability: The system should continue to work correctly despite faults happening.

Scalability: As the system gets bigger, there should be ways of handling this growth in reasonable ways.

Maintainability: As the system changes or gets bigger, people should still be able to work on it productively.

## Reliability

This means the system should continue to work correctly, even when things go wrong. Reliability is designing and developing the system in a resilient way. The system should still work when faults are happening. Faults and failures are not the same, failures stop the system from working entirely, and hence the users can't use the system at all when it happens.

Making systems reliable, despite human errors:

- Make sure components of the system are decoupled and design the system in a way that minimizes opportunities for errors.
- Make sure to test the system thoroughly resembling the user. Ideally, follow the TDD flow. Make sure to start a bug fix with a failing test.
- Allow quick and easy recovery from human errors.
- Set up detailed monitoring, such as performance metrics and error rates. Monitoring the requests being made. This is also referred to as telemetry. Monitoring can also show us early warning signals.

Systems need to be reliable, otherwise, customers can become disappointed or it can also lead to a loss of revenue.

## Scalability

Even if the system works well now, how will it work in the future when we have another million users? How will it work when the daily requests are 10x times more?

In an early-stage startup or an unproven product, it’s usually more important to be able to iterate quickly on product features than it is to scale to some hypothetical future load.

## Maintainability

Most of the time, initially the cost of writing the code is low, compared to later. As more code gets added, complexity increases. This makes the system harder to change or add new things too, or at least the cost becomes higher than initially.

# Chapter 2

## Relational Model Versus Document Model

In the last 30 years, SQL has dominated, relational databases.

### Birth of noSQL

NoSQL started in the 2010s, which is just a term for distributed, nonrelational databases.

Reasons to adopt NoSQL:

- A need for greater scalability than SQL can achieve.
- Specialized query operations that don't work well with SQL.
- Frustration with the restrictiveness of relational schemas.

### The Object-Relational Mismatch
