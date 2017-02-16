# JavaScript
JavaScript

                      SPEAKING JS

CHAPTER 7
JavaScripts Syntax
--------------------

Overview of Syntax:
  Diff between Expression and Statements:
    An Expression producess a value and can be written whenever a value expected.
    ex:
      myvar   // assining a vlue
      f('a', 'b') //arguments in the function call
      3+y

   Roughly, a statement performs an action. Loops and if statements are examples of statements.
   A Program is basically a sequence of statements.

  Conditional Statemet versus conditional expressions.
    ex:- if statement
      var salutation;
      if (male) {
        salutation = 'Mr.';
      } else {
        salutation = 'Mrs.';
      }
    ex:- conditional operator(expression)
      var salutation = (male ? 'Mr.' : 'Mrs.');

  Object literals(expressions) looks like blocks(statement) :
    {
      foo: bar(3, 5)
    }

  Named function expressions looks like function declarations(statements) :
    function foo() {}

    Javascript does not let you use object literals and function expressions as statements.
    The Expression statements must not start with
      1.A curly brace
      2.The keyword function
    If an expression starts with either of these tokens, it can only appear in the context of expression.

Immediatly Invoking Function Expression :

(function () {return "abc"}())

Javascript function expression can not be a anonymus(if we omit the parenthesis will get syntaxError as function is not aimmediately invoked)


Rules for using Semicolons:
Basic rules are
1.Normally, statements are terminated by semicolons.
2.The exception is statements ending with blocks.
Semicolons are optional in the java script. Missing semicolons are called by ASI(Automatic Semicolon insertion

No Semicolon if statemt end with block.
  Loops: for, while(not do-while)
  Branching: if, switch, try
  Function Declarations (but not function expressions)

  ex: while vs do-while
    while(a > 0) {
    a--;
    }//no semicolon

    do {
    a--;
    }while(a > 0);
  ex: function declaration vs function expression
    function foo() {
      //..
    }//no semicolon
    var foo = function () {
      //..
    };
Automatic semicolon insertion:

1. A line terminator(new line) followed by an illegal token.
  ex:
  if (a < 0) a = 0
  console.log(a)

  token console is illegal after 0 so ASI trigger.
  if (a < 0) a = 0;
  console.log(a);
2. A closing brace is encountered.
  ex:
  function add(a,b) {return a+b}
  ASI converts to
  function add(a,b) {return a+b;}
3. The end of a line encountered

pitfall:
  ASI can unexpectedly breakup the statements:

    //do not do this
    return
    {
      name: 'Jhone'
    };

    ASI will change it to
    return;
    {
      name: 'Jhone'
    };
    That is an empty retun followed by an block.

  ASI might unexpectedly not triggered:
    ex:
    func()
    ['ul', 'ol'].foreach(function (t) { handleTag(t) })
    The square brackets in the second line are interprited as index into the result returned by func()
    func()['ol'].foreach(function (t) { handleTag(t) });



Legal Identifiers:

  Identifiers are used for naming things and appear in various syntatic roles.
  First charater of an identifier is one.
  Any Unicode letter, including Latin letters such as D, Greek letters such as λ, and Cyrillic letters such as Д
  $,_

  Reserved Identifiers are:
  arguments
  break
  case
  catch
  class
  const
  continue
  debugger
  default
  delete
  do
  else
  enum
  export
  extends
  false
  finally
  for
  function
  if
  implements
  import
  in
  instanceof
  interface
  let
  new
  null
  package
  private
  protected
  public
  return
  static
  super
  switch
  this
  throw
  true
  try
  typeof
  var
  void
  while

Following 3 identifiers are not identifiers butshould treat them as if they were:
  infinity
  NaN
  undefined

  Note: Can use reserved words as unquoted property keys.
    var obj = { function: 'abc'};
    obj.function;
    //abc

Invoking methods on number literals:
  //1. toString()
  //(1).toString()
  //1.0.toString()
  //1..toString()

  var num = 1.0.toString();
  console.log(num);

Strict Mode:
  ECMAScript 5 has a strict mode that results in cleaner javascript, with fewer unsafe features, more warnings, and more logical behavior.
  The normal mode (unstrict) sometimes called sloppy mode.
Switching on stict mode:
  you switch strict mode on my typing in javascript file or inside <script> element.
    'use strict';

    if javascript engins that does not support ECMAScipt 5 will simply ignore.
    Can also switch on strict mode per function
    function foo() {
      'use strict';
      ...
    }

Strict mode recomended with caveat(warnings):
  Enabling strict mode for existing code may break it.
  package with care()
