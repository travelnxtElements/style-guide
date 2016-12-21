# Tavisca Web Components Style Guide

This guide serves as an extension to the Google [Web Component Style Guide](https://github.com/GoogleWebComponents/style-guide). It is targeted at developers creating components for Tavisca.

## General conventions

* All elements should be created using [Polymer CLI](https://www.polymer-project.org/1.0/start/first-element/intro) (refer build an element) as starting point. This provides a clean base for authoring elements.
*	All elements should be well documented (refer [document your elements](https://www.polymer-project.org/1.0/docs/tools/documentation))
*	All elements should have proper test cases (refer [test your elements](https://www.polymer-project.org/1.0/docs/tools/tests))
*	All elements should pass polymer lint with no errors or warnings (refer [lint elements](https://www.polymer-project.org/1.0/docs/tools/polymer-cli))
*	Ensure all elements are created using Polymer 1.7+ and are 2.0 compatible (refer [release 1.7.0](https://www.polymer-project.org/1.0/blog/2016-10-03-1.7-release.html))

## Naming

* Elements should contain a dash in their name (e.g `<my-tabs>` vs `<tabs>`), per the Custom Element [specification](http://w3c.github.io/webcomponents/spec/custom/#concepts),
* Tavisca elements should be prefixed with “t” (e.g `<t-header`> vs `<tavisca-header>`).
* Where multiple words are required for the name, they should be separated with a dash (e.g `<t-hotel-search>` vs `<t-hotelsearch>`) for readability.

## Attributes

* Published attributes should be camel-cased where multiple words are in use.
* Provide sensible default values as part of your API if values will be bound and displayed anywhere in your template. Default property values in attributes are null.
* Use '@default' and `@required` for parameters that either have a default value or are required.


## Events

* Event names should have a prefix strongly related to the name of the element in use (e.g `hotel-search-fired` vs `search-fired`). This allows you to drop in multiple elements in the page without event namespacing clashing.
* A unique event name should be fired for unique actions in your element that will be of interest to the outside world.
* Events should either end in verbs in the infinitive form (e.g. `t-client-api-load`) or nouns (e.g `t-hotel-results-success`).
* Use declarative event handlers over JS based (e.g. don't write `addEventListener` in your element code).

## Variables

* Do not use $ to prepend your own object properties and variables. Consider this style of naming reserved for use by Polymer and jQuery. Polymer allows you to use `$.*` within `<template>` and `this.$.*` within script to access the content of element children.
* Define constants outside of the `Polymer()` constructor, wrapped in an anonymous self-executing function. If you are using ES5.
* If you need to define private or static variables, wrap your script using [standard techniques](http://www.polymer-project.org/docs/polymer/polymer.html#static) like anonymous self-calling functions. For more details refer [old polymer developer guide](https://docs-05-dot-polymer-project.appspot.com/0.5/docs/polymer/polymer.html#static)

## Methods

* Methods should be camel-cased where multiple verbs/words are in use (e.g `doSearch()` vs `dosearch()`).

## Tests

* Polymer CLI based components have basic test project setup using Mocha and Chai that should be adapted to exercise your own element’s functionality. Examples of existing tests written by the Polymer team can be found in components test folder (e.g. [paper-tabs test](https://github.com/PolymerElements/paper-tabs/tree/master/test))
* Ensure your element and their tests run for both shadow and local DOM.
* We expect minimal test coverage to be > 90%
*	We prefer istanbul for test coverage (refer [WCT-Istanbul](https://github.com/thedeeno/web-component-tester-istanbul))

## Assets

* Assets such as icons, graphics and other forms of media should live inside an `assets` directory.
* Assets should be optimized (e.g using tools such as [ImageOptim](https://imageoptim.com/)) to minimize the size of resources package consumers need to download.

## Polymer-specific recommendations

* Where possible, use `on-tap` instead of `on-click` to benefit from additional help provided for touch screens
* Avoid excluding the outer `<template>` when attempting to use a conditional or repeat template
* Avoid binding to native attributes that can cause issues. See the Polymer [data-binding](https://www.polymer-project.org/1.0/docs/devguide/data-binding) docs for more information.
* Be careful when placing content inside the `<shadow>` element. This will not render.
