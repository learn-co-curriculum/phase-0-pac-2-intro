# Programming as Conversation 2: Introduction

## Learning Goals

* Define a statement versus an expression
* Understand the Default Execution Order
* Identify two core categories of code statements
* Provide an example of selection statement
* Provide an example of repetition statement

## Introduction

Welcome to Programming as Conversation, Part 2! In this module, we'll be
enriching the kinds of conversations we have with JavaScript. In Part 1, we
learned to recognize _expressions_ and saw that the data and operations they are
comprised of are _evaluated_ to produce a result or "return value." We also
learned three important expressions: the constant expression, the assignment
expression, and the variable lookup expression. In this next module, we'll see
that evaluations of expressions, while powerful, need _statements_ to control
when (sequence), whether (selection), and how many times (repetition) they are
_evaluated_. Code of this type is called a "statement."

We can see a parallel between expressions and statements with how children
_first_ learn to speak and how they enrich their communication with time.
Learning to talk is a gigantic achievement. It's a much-loved moment for parents
when a child learns to communicate through words instead of screaming fits. In
this early phase, however, some of their statements lack politeness and
sensitivity.

![Raw id, uncouth expression of desire for a cookie](https://curriculum-content.s3.amazonaws.com/phase-0/pac-2-intro/Image_92_CookieNOW.png)

Part of growing in their ability to converse is learning to wrap their desires
in politeness and consideration for the listener. "Would you mind giving me a
cookie?" and "Would you care to join me for a cookie?" both express the same
desire as our "rougher" example above, but show maturity.

![A mannerly cookie request](https://curriculum-content.s3.amazonaws.com/phase-0/pac-2-intro/Image_93_CookiePolite.png)

The same is true in code: we can do a great amount of work using just
_expressions_. However, _mature_ "speakers" of code learn to wrap their
_expressions_ in other _decisions_ and _context_. This ensures not only that the
right thing happens, ***but also*** that others can understand the code easily.
Learning to "wrap" expressions in reader-friendly context will continue into
Programming as Conversation Part 3 as well.

Let's start learning how to wrap our _expressions_ in _statements_ that will
give us greater flexibility **and** enrich our communication.

## Define a Statement Versus an Expression

We have learned that all JavaScript expressions have a return value. JavaScript
statements, on the other hand, don't necessarily. We can think of a statement
as an _instruction_ for some action we want to carry out.

We've already seen one type of statement: the variable declaration. A variable
declaration has no return value; this is the case regardless of whether we
assign a value at the time the variable is declared:

```js
const string = "Hello";
//=> undefined
let string2;
//=> undefined
string2 = "World";
//=> "World"
string2;
//=> "World"
```

A _variable declaration_ is a statement, while a _variable assignment_ and a
_variable lookup_ (as we have learned) are expressions.

> **Note:** If you recall the previous lesson on data types, `undefined` is
> _technically_ its own **thing** in JavaScript. However, it is used to
> represent a _lack_ of any particular value, so we treat it as such when we say
> that variable declaration has no return value.

One type of statement you will encounter frequently as you learn JavaScript is a
_block statement_. A block statement (also called a _code block_) consists of
one or more expressions or statements wrapped inside curly brackets (`{}`). We
will see them in action in upcoming lessons.

Some of the most commonly used statements in JavaScript and other languages
allow us to alter the order in which code is evaluated, in other words, to
change the _default execution order_.

## Understand the Default Execution Order

![Sequence Image](https://curriculum-content.s3.amazonaws.com/phase-0/pac-2-intro/Sequence_thick.png)

JavaScript by default will read our code according to the rules of a **default
sequence** or **default flow**: "every line, top to bottom, left to right as
ruled by order of operations." The "icon" above represents that rule. When you
see it in the following lessons, you should immediately think about "execution
order."

```js
const result = 1 + 1;
result; //=> 2
```

You probably have an intuitive model of the **default sequence** since you have
the general mindset that English text is read "top to bottom, left to right" and
expect that to apply to code. It does! Isn't it nice when things meet our
default assumptions?

This is why you intuitively grasp why JavaScript would throw an error with the
following code:

```js
result; //=> Error
const result = 1 + 1;
```

This error makes sense because this code is trying to do a variable lookup
_before_ initializing the variable that is looked up.

## Identify Two Core Categories of Code Statements

There are two types of statements that affect whether code is executed and in
what order:

* **Selection**: Given the default order (or "sequence"), can we choose to run
  certain lines of code and not others? How do we do so?
* **Repetition**: Given the default order (or "sequence"), can we choose to do
  something until a condition is met or until code has run some number of times?

## Provide An Example of Selection Statement

![Selection Image](https://curriculum-content.s3.amazonaws.com/phase-0/pac-2-intro/Selection_thick.png)

As represented in the icon above, sometimes we need to deviate from the default
**sequence**. We might need to **select** a different path. There's a [poem by
Robert Frost](https://www.poetryfoundation.org/poems/44272/the-road-not-taken)
about it.

In this case, the traveler is JavaScript, traveling fatefully down the default
sequence. We, as programmers, create a fork, a "split" in fate, and ask
JavaScript to take one path (or the other, or a third, or a fourth...and so on)
based on a Boolean "test" expression's return value. We ask JavaScript to
_select_ the path.

The first  **selection** tool we'll learn is `if`. The `if` statement disrupts
the "default sequence" by asking JavaScript to run a test, decide whether to
follow the path, and then move back to the default sequence. Go ahead and open
[replit][], paste the code below into the code window, and run it:

```js
let favoriteNumber = 32;
if (favoriteNumber >= 10) { // evaluating favoriteNumber >= 10 returns true
  favoriteNumber = favoriteNumber + 10
} 
console.log(favoriteNumber);
```

**Selection** lets us disrupt default flow by _making a choice_. JavaScript
evaluates the condition in the parentheses and, if it returns `true`, executes
the code inside the _block_ (the code enclosed in `{}`). If `favoriteNumber`
were assigned `0` at the time the `if` statement is evaluated, it would skip
over the code inside the block. That's why our icon shows the default flow
"hopping" from one point to another, skipping what's in the middle.

Try changing the initial value of `favoriteNumber` or using a different
comparison operator and see what happens.

## Provide An Example of Repetition Statement

![Repetition Graphic](https://curriculum-content.s3.amazonaws.com/phase-0/pac-2-intro/Repetition_thick.png)

**Repetition** lets us disrupt default flow by _repeating_. The `while` loop,
which we will introduce formally in a few lessons, means "do something `while`
(or "as long as") some condition is true." That "something" is held inside a
code block:

```js
let favoriteNumber = 0;
while (favoriteNumber < 10) {
  favoriteNumber = favoriteNumber + 1;
}
console.log(favoriteNumber);
```

Run this code in the REPL as well. Try changing the value we're using in our
condition, or experiment with where you put the `console.log()`, and see what
happens.

**Repetition** lets us disrupt default flow by marking off a set of commands
that should be re-evaluated multiple times before resuming default flow. It's
even possible to get into a repetition statement that you never exit.
Programmers call that an "infinite loop." Most of the time, that's not a
desirable situation. Our icon shows the more desirable situation of us following
default sequence, then finding a block that we repeat multiple times, then
returning to default sequence.

## Conclusion

This concludes our introduction to this module. This module is like a writing
class: we know how to write basic _sentences_ with a simple subject and a simple
verb. We're now going to try to write complete sentences with conjunctions and
punctuation (like the cookie examples!). We improve our basic sentences by using
SELECTION or REPETITION statements that allow us to create code that deviates
from the default "flow" or SEQUENCE.

[replit]: https://replit.com/languages/javascript
