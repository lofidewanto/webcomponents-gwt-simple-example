# webcomponents-gwt-simple-examples

Web Components Simple Examples with GWT

To run the examples: just go to the Maven project directory and run

```
mvn gwt:generate-module gwt:devmode
```

## Example 1: my-button-gwt-example

This example shows how to build Web Component completely in Java / GWT / JsInterop. Afterwards you
can use it by just adding the component ```<my-button></my-button>``` in the index.html

- This example is taken from this introduction: https://www.robinwieruch.de/web-components-tutorial 
- Also using this GWT / J2CL example: https://github.com/vegegoku/gwt-j2cl-mind-palace/tree/poc-gwt-j2cl-web-component/gwt-j2cl-web-component

Comments from Colin: See: https://gitter.im/gwtproject/gwt
- You can't do this in es5 js - and gwt2 won't generate es6 classes j2cl can do that.
- It is possible to shim this - creating the actual custom element ctor in some cheater code which sets it up so you can call it from JS
the problem is that the "subclass" calls its superclass, which is HTMLElement - but in es5, that means calling HTMLElement.call(this), roughly, instead of just saying "extends HTMLElement" and in the js constructor calling "super()"
- The HTMLElement constructor doesn't permit calling the constructor as a function, only as a super constructor (its possible i am not mapping that error correctly, its easier to tell from the JS instead of the sourcemapped java, but the idea is right at least)
