So, Solid, the UI library I've been building a lot of fun stuff within the past 2 months roughly.

I love it, so much. It is truly a UI library that brings me joy, how it works, and every line of code I've written.

I want to share my journey into Solid and my experience with it.

# React

When I was writing React, I was constantly looking around myself, seeing how the JavaScript world is progressing. I was listening to tech talks, and still love listening to tech talks.

To be completely honest, I didn't feel satisfied enough with React. The fact that I need to worry about re-renders and when I'm supposed to use `useCallback` or `useMemo` to optimize the performance of my React app wasn't sitting right with me. It felt like more cognitive overhead, more mental effort involved to write good React apps.

I like React though, otherwise, I wouldn't have chosen it as my main UI library back then.

The reasons I would choose React when developing my apps were primarily how I'm able to compose UI and use hooks. I can even create my own hooks to extract and reuse logic, I loved this part about React, encouraging the separation of concerns and decoupling logic. I like how I could nicely manage my state and pass around props. React gave me a lot of power.

# Attraction to Svelte

In 2020, I came across talks by the creator of Svelte, [Rich Harris](https://twitter.com/rich_harris). My favorite one was [Rethinking reactivity](https://www.youtube.com/watch?v=AdNJ3fydeao). I remember the times back then, I was looking for my first developer job. When coding on my side projects, I would actually put podcasts sometimes but many times talks by Rich Harris in the background when coding. He is such a good speaker and it was motivating for some reason.

When I got my job as a developer, Junior Frontend Developer back then working with React, I was eager to try out Svelte in my spare time.

I did the workshop by Rich Harris on Frontend Masters: https://frontendmasters.com/courses/svelte/.

After having done the workshop and tried out Svelte I wasn't vibing with it. The more Svelte I wrote, the more I missed React. I know it sounds weird, but I loved the way I would write my code in React.

I ended up just following my heart and sticking to React.

# First sight of Solid

After hearing about Solid, how it is sort of React syntax but works like Svelte under the hood, I got excited!

I didn't get around to Solid right away as I was busy with other stuff, but I kept my eye on it and joined their community where I also asked questions.

I eventually learned that under the hood, Svelte and Solid are different.

- [Solid compilation](https://www.youtube.com/watch?v=FB_kBYO_vIw&t=5167s)

- [Svelte compilation](https://www.youtube.com/watch?v=FB_kBYO_vIw&t=5634s)

This made me also see why Solid is more granular and made me love it even more, believe it or not.

# Unlearning React

When I finally got around to building side projects with Solid, I had to understand and get used to the fact. It felt weird at first, how you'd write Solid, and oftentimes I'd forget that I'm writing Solid and not React, perhaps not forget but the React ways of doing things would just be natural inside of me, I guess you could call it habits or whatever.

An example of this would be `useState` and `createSignal` in Solid.

The difference here is that the `createSignal` primitive of Solid returns _a getter_ as its first value. You'd have to invoke it in order to get the value. Let me show some code below.

```jsx
// Solid style
function someComponent() {
  const [count, setCount] = createSignal(0);

  return <div>{count()}</div>;
}
```

```jsx
// React style
function someComponent() {
  const [count, setCount] = useState(0);

  return <div>{count}</div>;
}
```

There are some more differences in terms of the way you write your code in Solid, you will discover them as you start writing it, and yes you should!

# Increasing love

My love for Solid just keeps increasing the more I write it.

## Fine-grained reactivity

This 10-minute video introduces you nicely to reactivity with Solid: [Introduction to Reactivity with SolidJS](https://www.youtube.com/watch?v=J70HXl1KhWE).

In short: In Solid we'd render components once, and after that, we're updating the content within the DOM nodes. Compared to React which is quite bloated and verbose, you'd re-render the component every time the state changes, Solid handles this much more efficiently and smarter.

## Primitives

I love the primitives Solid offers. It feels really nice and encourages composition. I like how the primitives in Solid are very decoupled from each other, it sort of gives you a sense of responsibilities of each primitive.

Examples that stood out to me are effects & lifecycles in Solid. I know in React we have a single hook, the `useEffect` hook which manages that, but in Solid we have different primitives with different responsibilities, I really like this approach, feels more decoupled and declarative to me.

- `createEffect` to make side effects run whenever dependencies change.
- `onMount` runs after the initial render and elements have been mounted.
- `onCleanup` runs on disposal or recalculation of the current reactive scope.

There are more and other primitives, this was just an example, I'm trying to keep things short, so you get to see the real deal when trying Solid out, you will be stunned!

## Less magic

As mentioned above, linking both compilations of Solid and Svelte, the output of Solid just contains much less magic than other UI libraries. I really like this part about Solid, and compared to React, trying to understand how it works under the hood wasn't too difficult.

## JSX

If you know me, I love JSX baby, the way you write the code there feels so nice.

I want to bring up that Solid also has its own components for certain things, i.e. [For](https://www.solidjs.com/docs/latest/api#for) component if you want to map over a collection and render the items inside of it. I like this approach, though, it is quite subjective and some dislike it.

# Conclusion

I love Solid. It is the best UI library at the moment (fair, that's subjective). I'm excited for its future and the future of the Web.

FYI I'm building a new side project with it soon. It is gonna be a keyboard typing game for small children. I've a sister that is in a few months turning 1 year old, it is gonna be for her as she grows up. Though, I'm excited to see how others' children find the game.
