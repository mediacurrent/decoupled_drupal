# Layout components

### What are layout components? <a id="what-are-layout-components"></a>

Layout components are for sections of your site that you want to share across multiple pages. For example, Gatsby sites will commonly have a layout component with a shared header and footer. Other common things to add to layouts are a sidebar and/or navigation menu. On this page for example, the header at the top is part of gatsbyjs.org’s layout component.

### How to create layout components <a id="how-to-create-layout-components"></a>

It is recommended to create your layout components alongside the rest of your components \(e.g. into `src/components/`\).

Here is an example of a very basic layout component at `src/components/layout.js`:

{% tabs %}
{% tab title="src/components/layout.js" %}
```javascript
import React from "react"

export default function Layout({ children }) {
  return (
    <div style={{ margin: `0 auto`, maxWidth: 650, padding: `0 1rem` }}>
      {children}
    </div>
  )
}
```
{% endtab %}
{% endtabs %}

### How to import and add layout components to pages <a id="how-to-import-and-add-layout-components-to-pages"></a>

If you want to apply a layout to a page, you will need to include the `Layout` component and wrap your page in it. For example, here is how you would apply your layout to the front page:

{% tabs %}
{% tab title="src/pages/index.js" %}
```javascript
import React from "react"
import Layout from "../components/layout"

export default function Home() {
  return (
    <Layout>
      <h1>I’m in a layout!</h1>
    </Layout>
  );
}
```
{% endtab %}
{% endtabs %}



