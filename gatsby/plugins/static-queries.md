# Getting runtime data from APIs \(useEffect or useQuery\)

Gatsby static queries are a funny thing. Typically, as explained in the 'Creating Pages' chapter, queries against the internal Gatsby GraphQL server can only happen in designated Page or Template files. At some point though, people really wanted to be able to query for data very deep in the data tree, or just in isolation of whatever Page or Template they may be building. This certainly increases the resuability of a component by tightly coupling it to its own data.

## Components with StaticQuery

So while static queries are rarely used for creating the Pages themselves, they are very useful for composing pages with components that may not rely on that Page's query.

We will be using the [example from the Gatsby docs](https://www.gatsbyjs.org/docs/use-static-query/) for creating a `Header` component that can exist anywhere and queries its own data, regardless of the Page it is on.

```jsx
import React from "react"
// Import the useStaticQuery hook.
import { useStaticQuery, graphql } from "gatsby"

// Create a normal react component as you would.
export default function Header() {
  // The `useStaticQuery` hook is a function that takes a GraphQL query string, and 
  // returns the data object.
  const data = useStaticQuery(graphql`
    // This query is same structure as if it were on a Page.
    query HeaderQuery {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)

  return (
    <header>
      <h1>{data.site.siteMetadata.title}</h1>
    </header>
  )
}
```

It is important to note, that although this query certainly _looks_ like it is happening _in_ the component at runtime, it is not. Gatsby extracts all static queries during the build and runs them at build time. So this data would still be static, just as if it were done at the page level. That's it! This allows you to build self-sufficient components that are statically rendered without deeply nesting or repeating the query on different Pages.

## Custom Reusable StaticQuery

Have a static query that you want to reuse? That's also [found in the docs here](https://www.gatsbyjs.org/docs/use-static-query/#composing-custom-usestaticquery-hooks). Say that `Header` query above is also the data you need for the `Footer`, you could extract that to its own function like this:

```jsx
import { useStaticQuery, graphql } from "gatsby"

export const useSiteMetadata = () => {
  const { site } = useStaticQuery(
    graphql`
      query SiteMetaData {
        site {
          siteMetadata {
            title
            siteUrl
            headline
            description
            image
            video
            twitter
            name
            logo
          }
        }
      }
    `
  )
  return site.siteMetadata
}
```

Then, to use the hook somewhere:

```jsx
import React from "react"
import { useSiteMetadata } from "../hooks/use-site-metadata"

export default function Home() {
  const { title, siteUrl } = useSiteMetadata()
  return <h1>welcome to {title}</h1>
}
```

