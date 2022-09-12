I want to share my journey into Remix. From being committed to Next.js to not being able to go back.

I think I'll go through it step by step and then end with a conclusion.

I will try my best to remember how I encountered Remix and what happened, because it has been almost a year since I first tried it out.

Disclaimer: I haven't checked out Next.js for roughly 8 months, so I don't know what is currently different.

# Initial impression

I might have read or seen Remix before this, but the truly first time I heard about it, explained as being a fullstack web framework that you _soon_ may want/should to choose over Next.js was in one of the Office Hours by [Kent C. Dodds](https://kentcdodds.com/).

Honestly, at that time, I felt committed to Next.js. I had been doing it for roughly 2 months, and was excited to use it for the next months, possibly years. It also felt overwhelming at the time, that there were so many things to learn, not just in the world of JavaScript, but even in the ecosystem of React.

Not that I felt obliged to learn everything, but it still felt overwhelming.

Hearing how excited Kent was over Remix, and how big of a thing it is gonna become, at first got me annoyed. My first thoughts were: **Oh shit, another thing to learn**.

I also felt annoyed at first, whether my Next.js learnings were worth it, or if I had just wasted my time. Take into account I didn't know any Remix at all by then, whether the barrier to build fullstack web applications with Remix is high or low.

At the back of my mind, I was excited to an extent, I knew that will eventually get around to trying Remix or at least seeing what it is truly about. In that Office Hour I had only heard it from Kent.

# Trying it out

I eventually got around to it.

I decided first to read the article Kent had written: [Why I Love Remix](https://kentcdodds.com/blog/why-i-love-remix). I was astonished. At first because of the simplicity, and how Remix takes the Web Platform, and gives me the control over it.

I ended up digging into Remix examples and repositories that had been built, and from there, the love for Remix grew, and the love story began.

# Loving it

I want to go over the stuff I loved with Remix (still do), that truly stood out to me compared to Next.js.

## Nested Routing

Remix has nested routing.

Websites typically have levels of navigation that control the child views.

These components would be coupled to URL segments AND they're also the semantic boundary of data loading and code splitting.

I can't upload videos here, but you can check out the [landing page of Remix](https://remix.run/).

Below are two images of the nested routing demo.

Not just does Remix have **nested routing**, but the way it does it is really elegant.

### File routing

Below is a small example taken from one of my side projects, but lets quickly go over it.

- `routes/index.tsx` becomes the URL `.../`.
- `routes/$type.tsx` is dynamic. The URL would become. `.../the-type-this-is-dynamic`
- `routes/$type/new.tsx` becomes the URL `.../the-type-this-is-dynamic/new`
- `routes/$type/$id.tsx` consist of two dynamic parts. The URL would become `.../the-type-this-is-dynamic/this-is-the-id-of-the-item`

Image of the actual project's routes.

### useMatches

This hook, `useMatches`, is arguably the most underrated hook/API of Remix.

It is extremely powerful, and here is where I think Remix really nailed it with nested routing.

I want to first mention that you can pass down props to the nested route from the parent route, like in the traditional React way, so that didn't come across as outstanding to me.

Though, `useMatches` I'd describe as the hook that lets you connect, and form a strong bond between the routes, no matter how deeply nested they are, which I think is extremely powerful. It returns the current route matches on the page.

The below code is taken from the [Remix documentation](https://remix.run/docs/en/v1/api/remix#usematches).

```js
function SomeComponent() {
  const matches = useMatches();

  // ...
}
```

```js
[
  { id, pathname, data, params, handle }, // root route
  { id, pathname, data, params, handle }, // layout route
  { id, pathname, data, params, handle }, // child route
  // etc.
];
```

A simple, yet super powerful hook.

## Single File

Believe it or not, this was shocking to me.

Everything from a single file, the data fetching, mutation, UI, error handling and even the meta tags for each route (even if they're nested). This was the thing to me where I was like, oh my goodness, this is a real fullstack web framework, holy shit. The beauty here too, to emphasize, is the server/client model.

What you'd do essentially is export functions that have their own responsiblities.

The default export is the UI/Client of the Route.

Let's take a look at some code.

```jsx
// Allows you to create application conventions with the `useMatches` hook.
export const handle = {
  its: "all yours",
};

// `data` is whatever exported by `loader` function.
// `params` is an object containing route params.
export const meta: MetaFunction = ({ data, params }) => {
  const description = `....`;
  return {
    charset: "utf-8",
    description,
    keywords: "sample,keys",
    "twitter:image": "...",
    "twitter:card": "summary_large_image",
    "twitter:creator": "...",
    "twitter:site": "...",
    "twitter:title": "...",
    "twitter:description": description,
  };
};

// Defines `<link>` elements to add to the page.
export const links: LinksFunction = () => {
  return [
    {
      rel: "icon",
      href: "/favicon.png",
      type: "image/png",
    },
    //     more links.
  ];
};

// This is responsible for handling data mutations and other actions.
export async function action({ dataArgs }: DataFunctionArgs) {
  const formData = await dataArgs.request.formData();
  const item = await fakeCreateItem({
    text: formData.get("text"),
  });

  return redirect(`/items/${item.id}`);
}

// This is responsible for fetching data.
export const loader = async ({ dataArgs }: DataFunctionArgs) => {
   const data = await fakeGetData()
   // `json` is just a helper method around `new Response`. Response itself by the way is just a web API, that's nothing specific to Remix. Remix was built on top of the web platform.
   return json(data)
};

export default function RouteComponent() {
  const data = useLoaderData();

  return (
    // here goes your JSX/mark up/UI
  );
}

// You can have a switch statement here checking the `caught.status`. This function is responsible for handling expected errors like 401, 403, 404 etc. This would get rendered when an action or loader throws a `Response`.
export function CatchBoundary() {
  const caught = useCatch();

  return (
    <div>
      <h1>Caught</h1>
      <p>Status: {caught.status}</p>
      <pre>
        <code>{JSON.stringify(caught.data, null, 2)}</code>
      </pre>
    </div>
  );
}

// Whenever an error has been thrown, or an unexpected error occured anywhere on the route, then the ErrorBoundary will be rendered.
export function ErrorBoundary({ error }) {
  return (
    <div>
      <h1>Error</h1>
      <p>{error.message}</p>
      <p>The stack trace is:</p>
      <pre>{error.stack}</pre>
    </div>
  );
}
```

## Progressive Enhancement

Remix by default works without JavaScript. Both when you fetch and mutate data (loaders and actions).

This means if JavaScript isn't getting loaded for your users for some reason, your product can still deliver value.

There are many reasons for why JavaScript may fail.

This is a great article about this: [Why your website should work without JavaScript.](https://endtimes.dev/why-your-website-should-work-without-javascript/).

## Web Platform

Remix is built on top of the platform (Web). Whatever you can do with any Web APIs, you can do that in Remix.

Not just that, Remix has taken the web APIs and built things on top of them, making it easy and efficient for you to work with the Web, and this is the point I really love with Remix.

I feel like with other frameworks, it is quite opinionated in their own way, how to develop and do everything.

In Remix, yes to an extent it is opinionated, i.e. you got the functions to export and so on, but it doesn't feel like it is forcing me to follow a certain pattern from A - Z, because it is built on top of the platform, there is an incredible amount of flexibility.

# Conclusion

I love Remix and I truly believe at the moment, it is the best fullstack web framework. I say at the moment, because people innovate, and as time pass, greater things come along.

I'm excited for the future of the Web and happy to be alive today.
