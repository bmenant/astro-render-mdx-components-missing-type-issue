# render-mdx-components-missing-type-issue

Minimal reproduction repo for `astro:content` module’s `Render['.mdx']` type definition
lacking a `components` property.

1. `npm ci`
2. `npx astro build` (ok)
3. `npx astro check` (will give typescript errors)
4. `npm run dev` (ok)

![screenshot-import-mdx.png](public/screenshot-import-mdx.png)
![screenshot-post-render.png](public/screenshot-post-render.png)

## Summary

- Two MDX files:
  1. content/blog/using-mdx.mdx (regular).
  2. content/blog/using-mdx-with-components.mdx (with an exported custom component h3=CustomH3).
- Two pages directly importing MDX and replacing components (h2=CustomH2):
  1. import-mdx-1.astro imports the regular MDX.
  2. import-mdx-2.astro imports the MDX with an exported custom component.
- The dynamic blog section `[...slug].astro` replacing components (h2=CustomH2).

## Notes

Project created from `npm create astro@latest`. 
Some unused pieces have been removed.

```
> npx
> create-astro


 astro   Launch sequence initiated.

   dir   Where should we create your new project?
         ./shaggy-shepherd

  tmpl   How would you like to start your new project?
         Use blog template

    ts   Do you plan to write TypeScript?
         Yes

   use   How strict should TypeScript be?
         Strict

  deps   Install dependencies?
         Yes

   git   Initialize a new git repository?
         No
      ◼  Sounds good! You can always run git init manually.

      ✔  Project initialized!
         ■ Template copied
         ■ TypeScript customized
         ■ Dependencies installed

  next   Liftoff confirmed. Explore your project!

         Enter your project directory using cd ./shaggy-shepherd 
         Run npm run dev to start the dev server. CTRL+C to stop.
         Add frameworks like react or tailwind using astro add.

         Stuck? Join us at https://astro.build/chat

╭──☠️─╮  Houston:
│ ◠ ◡ ◠  Good luck out there, astronaut! 🚀
╰──🦴─╯
```

