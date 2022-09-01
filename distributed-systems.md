# Read Replication

Read replication is a solution for distributed systems that are read-heavy, but don't write a lot of data. We'd have a leader node, and then follower nodes. The goal is to **remember** a specific value that has been sent by the client and written by the leader node.

This means everytime someone wants to read a specific data, they can get it right away, the **cached** version of it, from one of the follower nodes. If they write new data, that will take some time to get updated for the follower nodes, leading to a consistency problem.

This solution was invented early in web history, since web architects discovered that there were lots more reads than writes to web traffic.

# Sharding

What if things gets too tough for the leader node (referring back to read replication). Writing and distributing the data to all the follower notes, here we've to come up with a different solution.

Sharing is splitting up the work load into multiple read replicas. For an instance, if we have users with names that begin with the letters A to Z, we want to have 4 different replicas, responsible for different set of users. One replica for example would be responsible for users whose name begin with A to D.

## Complexity & Limitations

Sharing fits nicely for key-value stores, but what if you're not a key-value store. If you don't luck out on being able to shard every single query, life can get a little hard, to a point sharing just won't work for you.

# Consistent Hashing

The different nodes responsible for remembering the values are sort of in graph, in a circle, tied to each other, they need to know their position, and the previous and next position.

Whenever we come and ask for a value, we get a hash that connects us to one of the nodes, so when we come again and ask for the value, the nodes see our hash and know which one is responsible for our value.

What if one of the nodes isn't available for some reason, this could lead to an issue if a node isn't available. We can make sure that the previous and next node, also stores the hash and its value, this way if one of the nodes aren't available, we can still give the user the value that they are mapped to via their hash.

Another issue is, what if two nodes are down, and then the user decides to ask for something new, the node that is available will know of the update, but the nodes that were down won't. This leads to the problem of the other nodes becoming stale.

This would be called eventual consistency. We will be consistent with the values, but it could happen that we're getting the stale value.

The solution for this, though the drawback here is that the latency increases due to more work, is for the nodes to communicate with each other, and come to an agreement which write by the user was the latest one, and use that value.

# CAP Theorem

## Consistency

Whatever I read from the database, I'll always see what I have most recently written.

## Availability

When I read from the database, I always get a value returned. When I write to the database, I can write.

## Partition Tolerance

In a distributed system, there will be cases where parts of the database won't be able to communicate with other parts of the database. When this happens, the database should be able to deal with things till the partition is healed.

---

P is something we must have, because some parts of the database will be cut off from others. We should design the nodes to fail independently, and not cause the whole system to fail.

# Distributed Transactions

ACID transactions: Atomic, Consistent, Isolated and Durable.

A transaction is a bundle of changes.

Atomic means the transaction either goes through successfully if all changes have been made and no errors occurred, otherwise it will fail.

Consistent means upon completion of the transaction, the database is left in a valid state.

Isolation means that one transaction can't see another until the first one completes.

Durable means once a transaction commits, the database remembers those things.

In a transaction the work gets split up. This is in order to parallelize the work, and because workloads can be uneven, it is more effcient to split work up, some workloads will take longer than others.

If a failure happens, we can: do a write off, retry, or compensate the action. Write off means just discarding what happened, and retry is obviously retry.

# Distributed Computation

## Map Reduce

In MapReduce all of our computation is gonna be done in two functions, Map and Reduce. It is a framework that allows us to perform distributed and parallel processing on large data sets in a distributed environment. We're gonna keep try to keep data where it is.

It is a way to structure your computation so it can be run on lots of machines.

## Hadoop
