At Bobsled, the start-up I work for, we use Firestore. There are places where we use batched writes and transactions. Before I joined Bobsled though, I didn't know about transactions, and only knew about batched writes.

In this article, I want to clear up when you should use each, as it was slightly confusing for me at the beginning when I heard of transactions.

# Transactions

Transactions should be used when you want to modify a document based on one of its current values, or the value of some other field.

All write operations execute at the end of a successful transaction, they never happen **partially**.

Notes from [Transactions](https://firebase.google.com/docs/firestore/manage-data/transactions#transactions):

- Read operations must come before write operations.
- A function calling a transaction (transaction function) might run more than once if a concurrent edit affects a document that the transaction reads.
- Transaction functions should not directly modify application state.
- Transactions will fail when the client is offline.

Below example taken from [Transactions](https://firebase.google.com/docs/firestore/manage-data/transactions#transactions):

```js
import { runTransaction } from "firebase/firestore";

try {
  await runTransaction(db, async (transaction) => {
    const sfDoc = await transaction.get(sfDocRef);
    if (!sfDoc.exists()) {
      throw "Document does not exist!";
    }

    const newPopulation = sfDoc.data().population + 1;
    transaction.update(sfDocRef, { population: newPopulation });
  });
  console.log("Transaction successfully committed!");
} catch (e) {
  console.log("Transaction failed: ", e);
}
```

# Batched writes

If you don't need to read data, and based on that data write to Firestore, you can execute multiple write operations as a single batch.

Below example taken from [Batched writes](https://firebase.google.com/docs/firestore/manage-data/transactions#batched-writes):

```js
import { writeBatch, doc } from "firebase/firestore";

// Get a new write batch
const batch = writeBatch(db);

// Set the value of 'NYC'
const nycRef = doc(db, "cities", "NYC");
batch.set(nycRef, { name: "New York City" });

// Update the population of 'SF'
const sfRef = doc(db, "cities", "SF");
batch.update(sfRef, { population: 1000000 });

// Delete the city 'LA'
const laRef = doc(db, "cities", "LA");
batch.delete(laRef);

// Commit the batch
await batch.commit();
```

A batched write can consist of up to 500 operations. Batched writes are atomic, and don't need to make sure that documents read remain un-modified.

# When should you use each?

To recap:

- If you need to do multiple writes at the same time, but don't need to write based on data you've read from Firestore, then go with **batched writes**.

- If you need to read data from Firestore and based on that data make writes, then go with **transactions**.

# Conclusion

Batched writes and transactions can come across as quite similar when hearing them for the first time, and sometimes it can be hard to know when to use each, I hope this cleared up the topic.
