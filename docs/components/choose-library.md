---
layout: page
title: How to choose your library?
permalink: /components/how-to-choose/
parent: Third party integration
nav_order: 0
---

# How to choose your JavaScript library?

Vaadin 14 is using NPM (Node Package Manager) for managing Vaadin frontend JavaScript dependencies. So your library has to be on [npmjs](https://www.npmjs.com/).

Note: You can use JavaScript library if you copy/paste it in your folder or do some magic.
{: .fs-1 }

## Dependencies

Avoid JavaScript libraries that requires React, Angular, JQuery.

If you really need a library that requires JQuery, you can read this [tutorial](https://vaadin.com/learn/tutorials/integrate-jquery-into-vaadin-flow).

I don't have any advice for React or Angular.

Use small library and with few dependencies or dependencies that are already imported in your application like Vaadin dependencies or Polymer.

Use web components or vanilla Javascript.

Warning
{: .label .label-red }
Do not use library that depends on different version of your dependencies. It won't work.
For example, you have to exclude all the Polymer 2 components. Vaadin 14 requires Polymer 3.2.
You can't also use a component that requires Vadin-dialog 1.x if you have a component that requires Vaadin Dialog 2.x.
That's a major problem of web components.