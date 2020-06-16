# Components

To use Gatsby, you will need a basic understanding of React components.

### What are components in React? <a id="6076"></a>

Components are the building blocks of any React app and a typical React app will have many of these. Simply put, a component is a JavaScript class or function that optionally accepts inputs i.e. properties\(props\) and returns a React element that describes how a section of the UI \(User Interface\) should appear.

### Why React components? <a id="why-react-components"></a>

React’s component architecture simplifies building large websites by encouraging modularity, reusability, and clear abstractions. React has a large ecosystem of open source components, tutorials, and tooling that can be used seamlessly for building sites with Gatsby. Gatsby is built to behave almost exactly like a normal React application.

### How does Gatsby use React Components?

Everything in Gatsby is built using components.  A basic directory structure of a project might look like this:

```text
.
├── gatsby-config.js
├── package.json
└── src
    ├── html.js
    ├── pages
    │   ├── index.js
    │   └── posts
    │       ├── 01-01-2017
    │       │   └── index.md
    │       ├── 01-02-2017
    │       │   └── index.md
    │       └── 01-03-2017
    │           └── index.md
    ├── templates
        └── post.js
```

{% hint style="info" %}
Learn more about [React components](https://reactjs.org/docs/components-and-props.html) and how [Gatsby works with React components.](https://www.gatsbyjs.org/docs/building-with-components/#how-does-gatsby-use-react-components)
{% endhint %}

