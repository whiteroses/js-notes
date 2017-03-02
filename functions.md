# Functions


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

