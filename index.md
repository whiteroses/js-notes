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

Function expression:

	var v = function name(param1, param2) {
		return;
	}

or function declaration:

	function f(param1, param2) {
		return;
	}

or Function constructor:

	new Function (paramsList, "return;");

where paramsList can be
`"param1", "param2"` or
`"param1, param2"` or
`["param1", "param2"]`

* Empty brackets if no parameters.
* Functions by default return `undefined`, and so does a `return` statement
  without an expression after it.
* Parameter variables and variables created with `var` within function braces
  are local to function (variables declared without `var` are global).
  Lexical/static scoping.
* Without `let`, functions are the only things that create a new scope (other
  blocks do not). `let` works like `var`, but creates a variable that is local
  to the enclosing block, not the enclosing function.
* `(function f(){});` is a function expression rather than a declaration,
  because parentheses `()` are grouping operators and grouping operators can
  only contain an expression.

* Function name can be omitted in function expressions to create anonymous
  functions. A function expression can be used as a IIFE(Immediately Invoked
  Function Expression) which runs as soon as it is defined.
* The `name` in a named function expression is local to the function body, so
  it can only be referenced from within the function body (e.g. with
  recursion). This avoids using the non-standard `arguments.callee` property.
* Named function expressions are also useful for debugging, so we can have
  helpful function names in call stack.
* Function expressions are not placed into memory during compile phase
  ("hoisted"), but function declarations are. (Except older browser quirks and
  bugs.)
* Function declarations are not supposed to appear in blocks (blocks can only
  contain statements), and when it happens it should be considered a syntax
  error, but browser implementations vary. Create functions conditionally with
  function expressions.
* Function objects created with the Function constructor allow JavaScript code
  to be dynamically created and compiled at runtime. However, the Function
  constructor parses the function body and creates a new function object each
  time it is called, so if the call to the constructor appears within a loop or
  a frequently-called function, this can be inefficient. Functions
  created with the Function constructor do not use lexical scoping; they are
  always compiled as if they were top-level functions, so do not capture local
  scope.
* Invoking the Function constructor as a function (without the `new` operator)
  has the same effect as invoking it as a constructor.


## "hoisting"

Variable and function declarations are loaded into memory during compile phase,
before any code is executed. This means we can refer to them in the code before
they are declared. Initialisations are not "hoisted" though: a variable is
`undefined` if it is declared and initialised together at a later point in the
code.

Functions are hoisted first, then variables.

Multiple/duplicate `var` declarations are effectively ignored, but function
declarations do override previous ones.


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
