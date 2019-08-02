# Programming as Conversation 2: Introduction

## Learning Goals

* Define a statement versus an expression
* Identify the `nil` value and its purpose
* Identify three core categories of code statements
* Provide example of sequence statement
* Provide example of selection statement
* Provide example of repetition statement

## Introduction

Welcome to Programming as Conversation, Part 2!

When we were children learning to talk, we reached an ability to make simple
statements, and be responded to in a simple fashion. But once we'd learned to
make simple statements in the form of complete sentences, we were asked to
"elevate" our communication. We were expected to provide context to our
requests and state our thoughts in an order that others could receive. In
writing we were expected to move from simple, on-line answers to writing
_paragraphs_.

A two-year old might be able to express (and might well have a tantrum if denied):

> I want a cookie!

But an eight-year old might be expected:

> Mom, that cookie smells good! If I clean my room, may I have one? I want one
> of those cookies!

This second example shows _maturity_. We can see a hint of cause and effect
(If...then), a hint of personal responsibility, an understanding that cookies
are treats, etc.

The same is true in code: while we can do a great amount of work and expression
using _expressions_. Every mature "speaker" of code will use _expressions_ quite
a lot. However, _mature_ code "speakers" learn to wrap their _expressions_ in
other decisions and _context_ so that the most-correct _expressions_ are
_evaluated_.

That will be the purpose of this module, Programming as Conversation, Part 2.
Here we will learn to wrap _expressions_ in _statements_ that will give us
greater flexibility and enrich our communication.

## Define a Statement Versus an Expression

**_Expressions_ always return a value. Statements do not.**

This is an expression: `result = 1 + 1 #=> 2`.

This is a statement: `puts result #=> nil`.

Unlike _expressions_, _statements_ in _most_ programming languages do not
return a value. We're going to use this difference in mind as we learn
more about Ruby's statements.

What the heck was the return value of `puts` there just a moment ago? Let's
take a look at it a bit further.

## Identify the `nil` Value and Its Purpose

The `nil` value means "no value." You might recall it is one of the `falsey`
values in Ruby. It is the value that means "nothing." It's not `true` or
`false` it's the void. It's not 3 and it's also not any other number. It's the
lack of the idea of a number. It's not the point on the number line `0` which
means "no distance from the `0` point," rather it is the **true** nothing where the idea of
things at all (including `Integer`s, `Float`s, etc.) _does not exist_.

Some programming languages hate `nil` and make you squash it away as much as
possible (Swift), others embrace this Zen or Vedic mystery value (Ruby,
JavaScript), and others permit programmers to play fast-and-loose with it:
reaping speed rewards and but also crashing million-dollar systems (C). In
time, you'll form an opinion on this, but the fact we must accept is that Ruby
has it.

But why does a `puts` return `nil`? It's printing something to the screen,
that's "returning" a _return value_, right?

Think of it this way:

Consider:

```ruby
result = 1 + 1
puts result
```

|Code|Process|
|-|-|
|1 + 1 | Return values of constant `1` and `1` and summed due to `+` operator|
| result =  2 | Calculated `2` from previous step is assigned to result|
| result #=> 2 | `result` now holds `2`|
| puts result | constant lookup returns 2 and prints it to the screen|

What is the return value of printing to the screen? Was it `true` because it
was read (can a computer know that?) Is it the value that was sent out, `2`?
Even if the value was sent to the screen, what if the monitor was off or
broken, could the programming language know that? Because Ruby doesn't know
_what_ to return, it returns `nil`. In this case it's a bit like "No comment."

It certainly makes sense for Ruby to take this attitude, but it'd be horrible
if Ruby were to take this same attitude toward expression:

```ruby
1 + 1 #=> Nah, not feeling like adding today, so....nil!
```

Well, that'd be really unhelpful...and scary! But again, this underscores the
difference between _expressions_ and _statements_: _expressions_ always return
values. Statements usually do not.

Let's try a slightly more complex example. You've not been introduced to the `if`
_statement_ formally yet (soon!), but you should be able to follow this:

```ruby
if result == 2
  puts "things match"
end
```

You see, the `if` doesn't have a return value, it structures whether or not the
`puts` expressions will send the `String` constant expression to the screen.

The _expressions_ in this _statement_ are the Boolean-returning equality test
(`result == 2`) and the constant expression (`"things match"`), but `if...end`
and `puts` are statements: they don't evaluate an expression; instead they
decide whether something should happen.

***At its heart, programming is structuring which expressions get evaluated and in
what order that happens to solve problems.***

## Identify Three Core Categories of Code Statements

There are three core types of statement that we will cover in this module.

* **Sequence**: What code runs in what order? We make a sandwich before eating it;
  likewise, certain evaluations will run before others. How is that order
  determined?
* **Selection**: Given the default order of sequence, can we deviate from it
  under certain conditions? How do we do so?
* **Repetition**: Given a need to something until a something is `true`, or
  until something has happened a certain number of times, can we change the
  sequence to make something repeat before moving on?

Let's look at a few examples. Try them out in IRB. We'll cover them more
formally later.

> **NOTE**: These examples assume you're working in a
fresh, new IRB session _for each example_. If you define `result` and _don't_
restart IRB and a later example might assume `result` is `nil`, you might get a
surprising result. Use `exit` to leave IRB and launch a fresh session if you're
surprised by a result.

## Provide Example of Sequence Statement

The sequence statement isn't so much a statement, as an assumption. Ruby, by
default, will read our code according to the rules of a **default sequence**:
"every line, top to bottom, left to right as ruled by order of operations."

Like so:

```ruby
result = 1 + 1
puts result #=> 2
```

You probably have an intuitive model of the **default sequence** because you
recognize code as "text" and you probably have the general mindset that English
text is read "top to bottom, left to right."

It's why you intuitively grasp why Ruby would throw an error with the following
code:

```ruby
puts result #=> Error
result = 1 + 1
```

This error makes sense, because this code is trying to do variable lookup
_before_ setting the variable that is looked up.

## Provide Example of Selection Statement

Sometimes we need to deviate from the default **sequence**. We might need to
**select** a different path. There's a poem by Robert Frost about it:

> Two roads diverged in a yellow wood,
> And sorry I could not travel both
> And be one traveler

In this case the traveler is Ruby, traveling fatefully down the default
sequence. We, as programmers, create a divergence, a "split" in fate, and ask
Ruby to take one path (or the other, or a third, or a fourth...and so on) based
on a Boolean "test" _evaluation_. We ask Ruby to _select_ the path.

The first tool we'll learn to do **selection** is `if`. It disrupts the
"default sequence" by asking Ruby to run a test, decide whether to follow the
path, and then move back to the default sequence.

```ruby
favorite_number = 2 * 2 * 2 * 2 * 2 * 2 * 2 * 2
if favorite_number >= 10
  favorite_number = favorite_number + 10
  puts "And now your favorite_number is 10 more!"
end
puts "THE END"
```

**Selection** lets us disrupt default flow by _making a choice_.

## Provide Example of Repetition Statement

**Repetition** lets us disrupt default flow by _repeating_. The `.times`
method, which will introduce formally in just a moment, means "do something
`<value>` times." That "something" is held inside a `do...end` block. Other
programming languages like JavaScript like to use curly braces (`{}`) to set up a "block of
stuff to do". Python likes to use an indented line of code and neither `{}` nor
`do...end`. Ruby prefers `do...end`.

```ruby
favorite_number = 2 * 2 * 2 * 2 * 2 * 2 * 2 * 2
10.times do
  favorite_number = favorite_number + 1
end
puts "And now your favorite_number is 10 more! It is #{favorite_number}"
```

## Conclusion

So concludes our introduction to this module. This module is like a writing
class: we first learn how to write _sentences_, then we learn how to structure
them into paragraphs. As we get more comfortable with the interaction between
sentences and paragraphs we get to use our creativity to be more _expressive_.

The same is true of code. We aspire to write _eloquent_ and _expressive_ code.
We started with the "sentences" of _expressions_ and we will now learn to
structure them into "paragraphs" with _statements_ as the glue between the
sentences.

The big picture is this: evaluations, while powerful, need _statements_ to
control when (sequence), whether (selection), and how often (repetition) they
are _evaluated_. The remainder of this module will be teaching you code
statements in the category of sequence, selection, and repetition. These
statements will allow you to move your code in a more sophisticated and elegant
direction.
