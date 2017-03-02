# Notes on JavaScript


## To-do

* strict mode?
* `new function f(){}`?
* Read specs
* Babel, transpiler, ES2015/2016/2017?
ECMAScript 6th Edition, officially known as ECMAScript 2015.
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_Next_support_in_Mozilla
* require?
* npm
* Webpack
* https://github.com/getify/You-Dont-Know-JS
* https://leanpub.com/setting-up-es6/read
* https://github.com/thejameskyle/babel-handboo://github.com/thejameskyle/babel-handbook
* Unicode?
* debugger?
* Any security benefits of using parentheses `()` as grouping operator to force
  parsing as expression rather than block, e.g. with eval()?
* Are browser bugs here: http://kangax.github.io/nfe/#function-statements still
  relevant?
* Omitting semicolons at end of statements?
* List of reserved words and keywords?
* https://devfreebooks.github.io/javascript/ ?


## Specs

* https://www.ecma-international.org/publications/standards/Standard.htm
* https://www.ecma-international.org/ecma-262/7.0/
* https://www.ecma-international.org/ecma-262/6.0/
* https://www.ecma-international.org/ecma-262/5.1/
* https://www.ecma-international.org/publications/standards/Ecma-402.htm
* https://www.ecma-international.org/publications/standards/Ecma-262.htm
* https://www.ecma-international.org/ecma-262/7.0/index.html


## comments

`//` and `/**/`


## variables

e.g. `var v1 = "v1", v2 = "v2";`

Uninitialised variables start off with value of `undefined`.

<dl>
	<dt>environment</dt>
	<dd>collection of variables and their values existing at a given time</dd>
</dl>


## types

* boolean
	* true/false (lowercase only)

* number
	* 64-bit
	* signed
	* decimal (integer calculations precise, decimal calculations no)
	* scientific notation: e.g. 2.998e8
	* Infinity / -Infinity
		* Infinity - 1 === Infinity and Infinity + 1 === Infinity
	* NaN
		* e.g. 0 / 0, Infinity - Infinity
		* (NaN == NaN) == false

* string
	* Can concatenate with +.
	* Can be compared with <, >, >=, <=.
	* .length


* undefined
* object
	* null
* function


## type coercion

* When `null` or `undefined` is on either side of the `==` operator, expression
  is `true` only if both sides are one of `null` or `undefined`.
	* When we want to test whether a value has a real value instead of
	  `null` or `undefined`, we can simply compare it to `null` with the
	  `==` or `!=` operator.

* 0, NaN and "" count as false; all other values count as true.
	* e.g. 0 == false, and "" == false



## operators

* === and !== test without type coercion.
* x % y
	* remainder of x/y (known as modulo, but remainder more correct?)
* logical
	* &&, ||, !
	* Convert value to its left to boolean. Left-to-right lazy evaluation,
	  returns last evaluated value rather than the boolean value, e.g. null
	  && false returns null; true && null returns null.
* ?:
	* called the conditional operator
	* lazy-evaluates
* typeof
	* operator not function, so doesn't need brackets


## conditional flow

* if... else
* while
* do... while
* for (var number = 0; number <= x; number += 1) {}
* switch (), case:, default:
	* (!) Must break at end of each case if fallthrough not intended.
	  Potential source of bugs.
* break
	* breaks out of for, while, do... while and switch statements.
* continue
	* jump to start of loop's next iteration.


## blocks

* Sequence of statements wrapped in braces


## functions

[Functions](functions.md)


## built-in functions

* alert()
* confirm()
* isNan()
* prompt()


## built-in objects

* console
	* log()
* Math
	* max()
	* min()
