# Aurelia Style Guide

The purpose of this style guide is to provide guidance on building Aurelia applications by showing the conventions that I use and, more importantly.

##About the this style guide
This guide explains the *what* , *why* and *how* to see them in practice. This guide is accompanied by a sample application that follows these styles and patterns.

##Table of Content
 1. [Application Bootstrap Config](#application-bootstrap-config)
 2. [Responsibility](#responsibility)
 3. [Views and ViewModels](#)
 4. [Templating](#)
 5. [Routing](#)
 6. [Extending HTML](#)
 7. [Eventing](#)
 8. [HTTP Client](#)
 9. [Debugging](#)
 10. [Customization](#)
 11. [JSHint](#)
 12. [Naming](#)
 13. [Animations](#)
 14. [Compiler Options](#)
 15. [Doc Generated](#)
 16. [Testing](#)

##Application Bootstrap Config
Aurelia was originally designed for Evergreen Browsers. This includes Chrome, Firefox, IE11 and Safari 8. However, we have identified how to support IE9 and above. To make this work, you need to add an additional polyfill for MutationObservers. This can be achieved by a jspm install of `github:polymer/mutationobservers`. Then wrap the call to `aurelia-bootstrapper` as follows:

```markup
<script src="jspm_packages/system.js"></script>
<script src="config.js"></script>
<script>
  // Loads WeakMap polyfill needed by MutationObservers
  System.import('core-js').then(function() {
    // Imports MutationObserver polyfill
    return System.import('polymer/mutationobservers');
  }).then(function() {
    // Ensures start of Aurelia when all required IE9 dependencies are loaded
    System.import('aurelia-bootstrapper');
  });
</script>
```

**[Back to top](#table-of-content)**

##Responsibility
Most platforms have a "main" or entry point for code execution. Aurelia is no different. If you've read the Get Started page, then you've seen the aurelia-app attribute. Simply place this on an HTML element and Aurelia's bootstrapper will load an app.js and app.html, databind them together and inject them into the DOM element on which you placed that attribute.

The folowing example defines the `app`

```javascript
/**
* App.js
*/
export class App {
  constructor() {
   this.message = "";
  }
  
  activate() {
   this.message = "Hello, World!";
  }
}

```

**[Back to top](#table-of-content)**
