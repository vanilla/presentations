# ES6 __*Intro*__

---

## [fit] Quick intro, but __*incomplete*__

This is meant as a, hopefully usefull, intro to get you going. But there's still more to learn.

Note that we don't have full browser support for all these features. To get proper support, you need to transpile your code. Out build process includes __*Babel*__ to do this.

https://kangax.github.io/compat-table/es6/

___

## [fit] Our old friend __*var*__

We've all used __*var*__ but it causes a lot of issues. It can be *redifined* and __updated__, which causes a lot of __*bugs*__. 

The scope of a variable declared with var is its __*current execution context*__, which is either the enclosing function or, for variables declared outside any function, global. 

Examples: https://tinyurl.com/ycsn2ssa
___

## [fit] __*let*__ and __*const*__

These are *block* __scoped__ variables. (__*i.e.*__ a "__*block*__" is in curly brackets)

Variables declared by let have their __scope__ in the __*block*__ for which they are defined, as well as in any contained __*sub-blocks*__. In this way, let works very much like __*var*__. The main difference is that the __scope__ of a __*var*__ variable is the entire enclosing function.

___

## [fit] __*let*__ examples

Using __*let*__ to define the same variable twice in the same block, will give you an error: "Identifier 'x' has already been declared".

You can, however, redeclare it in a sub block.

Examples: https://codepen.io/slafleche/pen/odPBrV

___

## [fit] __*const*__ examples

__*const*__ have the same block scoping as __*let*__. It is not immutable, but the value of a constant cannot change through re-assignment, and it can't be redeclared.

Examples:

https://codepen.io/slafleche/pen/MGPpmr

___

## [fit] tldr

If you're unsure what to use, start with __*const*__ and see if you get an error. If you do, evaluate if it's your fault or if it makes sense to use __*let*__. 

Don't use __*var*__. *ES6* forces you to have better structured code and you should take advantage of that. 

___

## [fit] Arrow functions *=>*

Replaces __*anonymous functions*__ 

`function () {}` __*replaced with*__ `() => {}`

Examples:

https://codepen.io/slafleche/pen/YLJZgy

___

## [fit] __*Lexical scoping*__ for arrow functions

Lexical Scoping just means that it uses __*this*__ from the code that contains the arrow function.

The thing to pay attention to is the scope of __*this*__ and the function in `setInterval`

https://codepen.io/slafleche/pen/aGRWmo

___

## [fit] __*forEach*__ and __*map*__

__*forEach*__ : regular loop through items.

__*map*__ : returns new array, applying a transformation on each element. You can also chain the results to other array 
functions like __*filter()*__ or __*reverse()*__.

Examples: https://codepen.io/slafleche/pen/LmgdmQ

___

## [fit] __*spread*__ operators

Passes each value inside array or object with a handy syntax. Important to note that the spread operator *does not* do a deep copy. While the spread operator __does__ create a new object, the properties’ values are simply references and not new instances

Examples: https://codepen.io/slafleche/pen/pVxLmE

___

## [fit] Template literals

Built in templating style strings! Just use back ticks "__*\`*__".

Insert varaibles with *`${vaName}`*.

Examples: 
https://codepen.io/slafleche/pen/OZBZPJ
___

## [fit] Default params

Default params are finaly supported:

```
function sayMsg(msg='This is a default message.') {
  console.log(msg);
}

sayMsg(); // This is a default message.
sayMsg('This is a different message!'); // This is a different message!`
```

___

## [fit] Proper __*Classes*__!

We finaly have "proper" classes in ES6. 

The __*constructor*__ is the initialization method for the object. When you inherit from another class and you want to call their constructor, you call __*super*__ in your constructor method.

Simple inheritance example: 
https://codepen.io/slafleche/pen/mLzLEN

___

## [fit] importing/exporting

If you want to import modules from a file, you must add the proper type on the script tag: `<script type="module" src="module.js"></script>`

Examples: 
Export: https://codepen.io/slafleche/pen/ZomJzL
Import: https://codepen.io/slafleche/pen/rvQwbj

___

## [fit] importing/exporting (__*cont’d*__)

ES6 makes it easy for everything to be modular and properly scoped. Split your files, include what you need.


More examples:
https://tinyurl.com/y8sggsu5

___

## [fit] There's still __*more*__!

There's still more feature. I encourage you to do some research. 

There's a lot to know, but hopefully I've eased you into __*ES6*__.

___

## [fit] Resources:

__*MDN Web Docs*__:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference

Books: __*You don't know Javascript*__ (free version on Github):
https://github.com/getify/You-Dont-Know-JS

Also, you know, just __*Google*__ this stuff!

