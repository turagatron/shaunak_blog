## Background
- I'm a product manager that transitioned from being a software engineering several years ago
- Technologies for web app development have changed since then and I want to invest in learning more skills, methodologies, and standards
- I'm interested in exploring new software ideas and feel that becoming familiar with modern tech stacks and tooling will enable more efficiences for myself and others that I work with

## Goal
- I don't currently have a personal blog page and was considering a no-code tool like Webflow, that that isn't as fun as building something from scratch
- I was to be able to learn how to develop the client only using React and maintain the middle and backend with no or low-code platforms

## Notes

### NextJS

1. Next.js polyfills fetch() on both the client and server. You don't need to import it.
2. Since Static Generation happens once at build time, it's not suitable for data that updates frequently or changes on every user request. In cases like this, where your data is likely to change, you can use [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering). Let's learn more about server-side rendering in the next section.