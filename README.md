# Programming as Conversation 2: Introduction

## Learning Goals

* Define a statement versus an expression
* Identify the `nil` value and its purpose
* Identify three core categories of code statements
* Provide an example of sequence statement
* Provide an example of selection statement
* Provide an example of repetition statement

## Introduction

Welcome to Programming as Conversation, Part 2! In this module, we'll be
enriching the kinds of conversations we have with Ruby. In Part 1 we learned to
recognize _expressions_ and saw that the data and the operations are
_evaluated_ to produce a result or "return value." We also learned three
important expressions: the constant expression, the assignment expression, and
the variable lookup expression. In this module we'll see that evaluations of
expressions, while powerful, need _statements_ to control when (sequence),
whether (selection), and how many times (repetition) they are _evaluated_. Code
of this type is called a "statement."

We can see a parallel between expressions and statements to how children
_first_ learn to speak and how they enrich their communication with time.
Learning to talk is a gigantic achievement. It's a much-loved moment for
parents when a child learns to communicate through words instead of screaming
fits. In this early phase, however, some of their statements lack politeness
and sensitivity.

![Raw id, uncouth expression of desire for a cookie](https://curriculum-content.s3.amazonaws.com/programming-univbasics-2/introduction/Image_92_CookieNOW.png)

Part of growing in their ability to converse is learning to wrap their desires
in politeness and consideration for the listener. "Would you mind giving me a
cookie?" and "Would you care to join me for a cookie?" both express the same
desire as our "rougher" example above, but show maturity.

![A mannerly cookie request](https://curriculum-content.s3.amazonaws.com/programming-univbasics-2/introduction/Image_93_CookiePolite.png)

The same is true in code: while we can do a great amount of work using
_expressions_. _Mature_ "speakers" of code learn to wrap their _expressions_ in
other _decisions_ and _context_ so that the right thing happens ***but also***
so that others can understand the code easily. Learning to "wrap" expressions
in reader-friendly context will continue into Programming as Conversation
Part 3 as well.

Let's start learning how to wrap our _expressions_ in _statements_ that will
give us greater flexibility **and** enrich our communication.

## Define a Statement Versus an Expression

**Statements alter the order in which code is evaluated from the default
execution order of top-to-bottom, left-to-right. The default execution order is
sometimes called the default code "flow." Statements usually return no value.***

Below, `1 + 1` is an expression:

```ruby
result = 1 + 1 #=> 2`
```

Below, `puts result` is a ***statement***:

```ruby
result = 1 + 1 #=> 2`
puts result #=> nil`
2
```

Here's an important distinction. The return value, after the `#=>` is `nil` but
a "side-effect" of running the `puts` statement is printing `2` to the screen.
Expressions ***always*** return a value. Sttatements do not, as we see with `puts`.

## Identify the `nil` Value and Its Purpose

The `nil` value means "no value." You might recall it is one of the `falsey`
values in Ruby. It is the value that means "nothing." It's not `true` or
`false`. It's a world without the scale of `true` or `false`.

It's not `3` and it's also not any other number. It's also not `0`, a value
that's no distance from `0` on the number scale. It's a world without the scale
of `Integer`s or `Float`s.

In short, `nil` is The Void.

The return value of `puts` (print something to something) is `nil` because
Ruby can't know whether the printing was successful. It knows whether adding
`1` to `1` was successful. But what if the monitor is disconnected? What if no
one is looking at it? Because Ruby can't know, it says `nil`.

Again, this behavior underscores the difference between _expressions_ and
_statements_: _expressions_ always return values. Statements might, but they
might not.

## Identify Three Core Categories of Code Statements

There are three types of statement that change the order of what gets run and
in what order:

* **Sequence**: What code will run next by default?
* **Selection**: Given the default order (or "sequence"), can we choose to run
  certain lines of code and not others? How do we do so?
* **Repetition**: Given the default order (or "sequence"), can we choose to do
  something until a condition is met or until code has run some number of
  times?


> **NOTE**: Be sure to try the following examples yourself in IRB.  These
> examples assume you're working in a fresh, new IRB session _for each
> example_. If you define `result` and _don't_ restart IRB and a later example
> might assume `result` is `nil`, you might get a surprising result. Use `exit`
> to leave IRB and launch a fresh session if you're surprised by a result.

## Provide An Example of Sequence Statement

![Sequence Image](https://curriculum-content.s3.amazonaws.com/programming-univbasics-2/sequence-and-comments/Sequence_thick.png)

_As you'll see in the next lessons, we've created a little icon for each of
these types of statement. We're going to introduce you to these icons now so that we
remind you which type of statement you're looking at._

The sequence statement isn't so much a statement, as an assumption. Ruby by
default will read our code according to the rules of a **default sequence** or
**default flow**: "every line, top to bottom, left to right as ruled by order
of operations." The "icon" above shows that rule. When you see it, you should
immediately think about "execution order."

```ruby
result = 1 + 1
puts result #=> 2
```

You probably have an intuitive model of the **default sequence** since you
have the general mindset that English text is read "top to bottom, left to
right" and expect that to apply to code. It does! Isn't' it nice when things
meet our default assumptions?

This is why you intuitively grasp why Ruby would throw an error with the
following code:

```ruby
puts result #=> Error
result = 1 + 1
```

This error makes sense because this code is trying to do a variable lookup
_before_ setting the variable that is looked up.

## Provide An Example of Selection Statement

![Seelection Image](https://curriculum-content.s3.amazonaws.com/programming-univbasics-2/introduction/Image_94_Selection_LARGE.png)

Sometimes we need to deviate from the default **sequence**. We might need to
**select** a different path. There's a poem by Robert Frost about it:

> Two roads diverged in a yellow wood,
> And sorry I could not travel both
> And be one traveler

In this case, the traveler is Ruby, traveling fatefully down the default
sequence. We, as programmers, create a fork, a "split" in fate, and ask Ruby to
take one path (or the other, or a third, or a fourth...and so on) based on a
Boolean "test" expression's return value. We ask Ruby to _select_ the path.

The first tool we'll learn to do **selection** is `if`. The `if` statement
disrupts the "default sequence" by asking Ruby to run a test, decide whether to
follow the path, and then move back to the default sequence.

```ruby
favorite_number = 2 * 2 * 2 * 2 * 2 * 2 * 2 * 2
if favorite_number >= 10 # evaluating favorite_number >= 10 returns true
  favorite_number = favorite_number + 10
  puts "And now your favorite_number is 10 more!"
end
puts "THE END"
```

**Selection** lets us disrupt default flow by _making a choice_.

## Provide An Example of Repetition Statement

![Repetition Graphic](https://curriculum-content.s3.amazonaws.com/programming-univbasics-2/introduction/Image_94_Repetition_LARGE.png)

**Repetition** lets us disrupt default flow by _repeating_. The `.times`
method, which will introduce formally in a few lessons, means "do something
`<value>` times." That "something" is held inside a `do...end` block. Other
programming languages like JavaScript like to use curly braces (`{}`) to set up
a "block of stuff to do". Ruby prefers `do...end`.

```ruby
favorite_number = 2 * 2 * 2 * 2 * 2 * 2 * 2 * 2
10.times do
  favorite_number = favorite_number + 1
end
puts "And now your favorite_number is 10 more! It is #{favorite_number}"
```

## Conclusion

This concludes our introduction to this module. This module is like a writing
class: we know how to write basic _sentences_ with a simple subject and a
simple verb. We're now going to try to write complete sentences with
conjunctions and punctuation (like the cookie examples!). We improve our basic
sentences by bringing in statements from the SELECTION and REPETITION class
which deviate from the default "flow' or SEQUENCE.

