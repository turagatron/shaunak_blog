## Background
- I'm a product manager that transitioned from being a software engineering several years ago
- Technologies for web app development have changed since then and I want to invest in learning more skills, methodologies, and standards
- I'm interested in exploring new software ideas and feel that becoming familiar with modern tech stacks and tooling will enable more efficiences for myself and others that I work with

## Goal
- I don't currently have a personal blog page and was considering a no-code tool like Webflow, that that isn't as fun as building something from scratch
- I was to be able to learn how to develop the client only using React and maintain the middle and backend with no or low-code platforms

## Final Output

Here is my basic blog using NextJS! [Click here to view](https://shaunak-blog.vercel.app/)

![Blog Demo](public/images/preview.gif)

## Notes

### NextJS

1. Next.js polyfills fetch() on both the client and server. You don't need to import it.
2. Since Static Generation happens once at build time, it's not suitable for data that updates frequently or changes on every user request. In cases like this, where your data is likely to change, you can use [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering). Let's learn more about server-side rendering in the next section.
3. To use Server-side Rendering, you need to export getServerSideProps instead of `getStaticProps` from your page. You should use getServerSideProps only if you need to pre-render a page whose data must be fetched at request time. Time to first byte (TTFB) will be slower than `getStaticProps` because the server must compute the result on every request, and the result cannot be cached by a CDN without extra configuration.
4. If you do not need to pre-render the data, you can also use the following strategy (called Client-side Rendering). This approach works well for user dashboard pages, for example. Because a dashboard is a private, user-specific page, SEO is not relevant, and the page doesn’t need to be pre-rendered. The data is frequently updated, which requires request-time data fetching.
```
// Example of how to use SWR for CSR ->

import useSWR from 'swr';

function Profile() {
  const { data, error } = useSWR('/api/user', fetch);

  if (error) return <div>failed to load</div>;
  if (!data) return <div>loading...</div>;
  return <div>hello {data.name}!</div>;
}
```

5. Do Not Fetch an API Route from `getStaticProps` or `getStaticPaths`. You should not fetch an API Route from `getStaticProps` or `getStaticPaths`. Instead, write your server-side code directly in `getStaticProps` or `getStaticPaths` (or call a helper function).

Here’s why: `getStaticProps` and `getStaticPaths` run only on the server-side and will never run on the client-side. Moreover, these functions will not be included in the JS bundle for the browser. That means you can write code such as direct database queries without sending them to browsers. Read the Writing Server-Side code documentation to learn more.