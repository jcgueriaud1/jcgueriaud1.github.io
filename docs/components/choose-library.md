---
layout: page
title: How to choose your library?
permalink: /components/how-to-choose/
parent: Third party integration
nav_order: 0
---

# How to choose your JavaScript library?

Vaadin 14 is using NPM (Node Package Manager) for managing Vaadin frontend JavaScript dependencies. So your library has to be on [npmjs](https://www.npmjs.com/).

Note: It's not required to use npm. You can also use a JavaScript library if you copy/paste it in your folder. But it's not the way I recommended because the upgrade it less easy and there is no dependency management.
{: .fs-1 }

## Dependencies

Avoid JavaScript libraries that requires React, Angular, JQuery, Vue...

If you really need a library that requires JQuery, you can read this [tutorial](https://vaadin.com/learn/tutorials/integrate-jquery-into-vaadin-flow).

I don't have any advice for React or Angular.

Use small library and with few dependencies or dependencies that are already imported in your application like Vaadin dependencies or Polymer.

Use web components or vanilla Javascript.


Warning
{: .label .label-red }
Do not use library that depends on different version of your dependencies. It won't work.
For example, you have to exclude all the Polymer 2 components. Vaadin 14 requires Polymer 3.2.
You can't also use a component that requires Vaadin-dialog 1.x if you have a component that requires Vaadin Dialog 2.x.
That's a major problem of web components.

## Examples

I was looking for a tooltip javascript library.

### react-tooltip

You can find all the dependencies information in the npm site.

-- image to copy --

The name is quite obvious and requires react.
The dev dependency is quite long.
It's recently updated and has Typescript definitions (TS logo in the title)

The readme seems quite good with examples and documentation. It's also really important because I recommend to use the simplest example for the integration.

## Tippy.js

The size is quite big. Almost 2Mb and there are a lot of functionalities. It's powered by popper, almost 1.5Mb.
I don't recommend this library if you need one simple tooltip but if you need different themes, animations, ... that's probably a good solution.


## @spectrum-web-components/tooltip

I've changed the search criteria and search "tooltip lit".
This library is already a webcomponent it's quite small with few dependencies.



