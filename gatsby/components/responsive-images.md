# Responsive images

Gatsby provides several plugins to handle responsive images.  These plugins make it possible for gatsby to proess and optimize images to achieve fast and performant image loading.

One of these plguins is the [Gatsby remark responsive image](https://www.gatsbyjs.org/packages/gatsby-remark-responsive-image/).  Some of the features on thsi plugin include creating an elastic container to allow to hold the image size and avoid content jumping while the actual image loads.  Also providades lovides the ability to generate multiple size images to be used as part of the image's `srcset`.  And finally, it provides a series of effects to use when images load.

Another plugin used for handling images is the [gatsby-image](https://www.gatsbyjs.org/packages/gatsby-image/), which works with [gatsby-plugin-sharp](https://www.gatsbyjs.org/packages/gatsby-plugin-sharp/) to provide advanced image loading techniques.
