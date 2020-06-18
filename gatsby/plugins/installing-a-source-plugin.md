# Installing and configuring a plugin

Installing Gatsby plugins is as simple as installing any other NPM package. Let's take the example of the **gatsby-sitemap** plugin to create a sitemap for your gatsy site:

## Install <a id="install"></a>

```text
npm install --save gatsby-plugin-sitemap
```

## Configure the new plugin

In your `gatsby-config.js` file, add the following code:

{% tabs %}
{% tab title="gatsby-config.js" %}
```javascript
siteMetadata: {
  siteUrl: `https://www.example.com`,
},
plugins: [`gatsby-plugin-sitemap`]
```
{% endtab %}
{% endtabs %}

Most plugins allow you to do additional customization and configuration as is the case of the **sitemap** plugin. All the available options for configuring and customizing a plugin are found in the project's page for each plugin.

{% hint style="info" %}
Brow all the [Gatsby plugins](https://www.gatsbyjs.org/plugins/).
{% endhint %}

