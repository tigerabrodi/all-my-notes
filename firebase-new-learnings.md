# Firebase

## Dates

When writing to Firestore documents, don't trust your local date, i.e. use `new Date()` for your dates. The date on the client could have a different date and time on it than what the server expects. A user's clock could be different, and they can even try to intercept and write malicious dates to the server.

For dates you should use `serverTimestamp()`. It would act as a placeholder, and when the write is happening on the server, it then inserts what the server time is in that spot.

This way we can be confident with our dates.

## Incrementing values

Incrementing is difficult since a lot can happen in a real time system, and if you're constantly incrementing or decrementing a value, you may be in danger of running into race conditions.

For this firebase has a `decrement()` and `increment()` function, and it will handle that process for you. Whenever these increments and decrements are happening, it will queue up the proper ordering rather than running into any race conditions.

## Limit

Firestore does have a limit of being able to reliably handle one write per second to a single second.

## Synchronization

In Firestore systems, we don't wait for the server responses when writing. We write and let the cache behind the system handle it.

```js
onSnapshot(postDoc, (snapshot) => {
  const post = snapshot.data();
  console.log(post);
  // First time: { text: "First Text" }
  // Second time: { text: "Second Text" }
});

updateDoc(postDoc, { text: "Second Text" });
```

The first data returned from `onSnapshot` will be coming from the server, the second time, Firestore will create a pending write, and write to the cache, so everything happens offline first making the UI really snappy. It assumes things will go well, if it doesn't, then it will roll back.

The snapshot also comes with `metadata` that let's you see whether the data you got is from the cache and the write is still pending (hasn't talked to the server yet).

```js
onSnapshot(postDoc, (snapshot) => {
  console.log(snapshot.data());
  // First time: { text: "First Text" }
  // Second time: { text: "Second Text" }

  console.log(snapshot.metadata);
  // First time: { fromCache: false, hasPendingWrite: false }

  // Second time (data is updated locally): { fromCache: true, hasPendingWrite: true }
});

updateDoc(postDoc, { text: "Second Text" });
```
