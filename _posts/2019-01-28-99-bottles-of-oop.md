---
title:  "99 Bottles of OOP"
categories:
  - Jekyll
last_modified_at: 2019-01-28T08:06:00-05:00
---

# 99 Bottles of OOP

**Chapter 1 - Rediscovering Simplicity**

Design is about picking the right abstractions. Pick the right ones and everyone will love both it and you. If you choose the wrong ones, code will be convoluted, confusing and costly.

Early abstractions are not quite right and therefore they create a catch 22. Don't reach for abstractions but instead resist them until they absolutely insist upon being created.

**Value/cost questions -**

_How difficult was it to write?_

_How hard is it to understand?_

_How expensive will it be to change?_

_Incomprehensibly Concise_

_Speculatively General_

_Concretely Abstract_

_Shameless Green_

_Evaluating code based on opinion_

**_What is clean code?_**

**_What is Clean code? A collection of quotes - "full of crisp abstractions", "clean code is written by someone who cares", "highest value for the lowest cost",_**

**_Evaluating code based on Facts_**

Metrics are crowd-sourced opinions about the quality of the code.

Three different metrics - source lines of codex cyclomatic complexity and ABC

ABC - Assignments, branches (of control - function calls) and conditions

There's something beyond complexity, a higher level of simplicity.

**Chapter 2 - Test Driving Shameless Green**

"Quick green excuses all sins" - Kent Beck.

Consider the problem, sketch out an overall plan but don't overthink it.

"As tests get more specific, code gets more generic"

Use metrics, but don't rely on them completely.

**Transformation Priority Premise**

Simple operations that change the behaviour of the code in priority order.

When a problem can be solved with any of several transformations, the transformation with the highest priority is simplest and therefore best.

'Pluralize' abstraction is the wrong concept for verse 2, even though it leads us to that abstraction.

DRY is important but if applied too early (overzealous programmers) it can end up in the incorrect abstractions.

Ask yourself these questions when making any change -

- _Does the change I'm contemplating make the code harder to understand?_

- Incorrect abstractions make the code harder to understand. Insufficient understanding of the problem.

- _What is the future cost of doing nothing now?_

- _Some changes cost the same whether done now or later, waiting saves you money_

- _When will the future arrive, i.e. how soon will I get more information?_

- _"_**_Better to tolerate duplication than to anticipate the wrong abstraction_**_"_

Three of Kent Beck's _Green Bar Patterns_ are -

- Fake it till you make it
    
- Obvious implementation
    
- Triangulate - conservatively drive abstraction with tests. Write several tests at once, then make them all pass with one bit of code

API Design - _song_ API vs _verses(99,0)_ API

**Intention vs Implementation**

_The distinction between intention and implementation allows you to understand a computation first in essence and later, if necessary, in detail._

_Tests are not the place for abstractions, but concretions_

**Chapter 3 - Unearthing Concepts**

Refactor now or later? Weigh up opportunity cost Vs benefits.

**Refactoring Systematically**

_Refactoring is the process of changing a software system in such a way that it does not alter the external behaviour of the code yet improves its internal structure._

If tests are bad, improve them first and then start refactoring.

**Flocking Rules**

1. Select the things that are most alike
    
2. Find the smallest difference between them
    
3. Make the simplest change that will remove that difference

Always make the smallest changes, if you accidentally make a big one and things break, undo and make the smallest change. This gives you a very precise point of failure when things break.

Flocking Rules allow code abstractions to appear by grouping similar things together etc.

**Why "flocking"?**

**Watch the Science of Sync TED talk**

Birds flock, fish school and insects swarm. A flock's behaviour can appear so synchronized and complex it gives the illusion of being centrally coordinated.

The flocking behaviour is a result of a continuous series of small decisions made by each participating individual.

1. Alignment - steer towards the average heading of neighbours
    
2. Separation - don't get too close to neighbours
    
3. Cohesion - steer towards the average position of the flock

Complec behaviour emerges from the repeated application of simple rules.

**Converging on Abstractions**

_DRYing out sameness has some value, but DRYing out difference has more._

_If two concrete examples represent the same abstraction and they contain a difference, that difference must represent a smaller abstraction within the larger one. If you can name the difference, you've identified that smaller abstraction._

**_Horizontal Vs vertical changes_**

**Naming Concepts**

One way to identify Abstractions is to imagine the concrete examples as rows and columns in the spreadsheet. Naming something should always be one level of abstraction higher than the thing itself.

Use a table like below to come up with the name of the concept/abstraction.

Imagine other concrete examples and the abstraction appears! In the above example, imagine wine instead of beer. "Container".

_Making a slew of simulatenous changes is not refactoring, it's rehaktoring._

**Chapter 4 - Practicing Horizontal Refactoring**

Replace difference with sameness.

Naming strategies for a new concept/abstraction -

- Ponder name for 5-10 mins (timeboxed) with thesaurus in hand
    
- Pick any name and unblock yourself quickly, hoping that the name will become obvious later (_you'll never know less than you know right now_)
    
- Pick a "best effort" name and improve it later as you understand the domain better
    
- Ask someone for help, the "name guru" in the team

**Deriving names from responsibilities**

Best to stay horizontal and concentrate on the current goal instead of thinking too far ahead. When you create an abstraction, first describe it's responsibility **_as you understand it at this moment._** As your understanding improves, you can improve the name later.

**Choosing Meaningful Defaults**

Sometimes you'll want to use a more meaningful default other than FIXME, when you want to execute the TRUE statement of an if condition.

This will still allow you to change one line at a time but you have to be more careful about removing the default value later on.

**Obeying the Liskov Substitution Principle**

The idea of reducing the number of dependencies imposed upon message senders by requiring receivers return trustworthy objects is a generalisation of the Liskov Substitution Principle.

_Liskov prohibits you from doing anything that would force the sender of a message to test the returned result in order to know how to behave._

**Discovering Deeper Abstractions**

The 'shape' of a method should give you a clue if you've got the abstraction wrong.

_When you're confused, don't try to solve the entire problem straightaway._

_The power of iterative application of the Flocking Rules._

**Final solution Vs Shameless Green**

The final solution has a worse score than shameless green but it has clean abstractions and much easier to understand the underlying concepts.

_You don't have to understand the entire problem in order to find and express the correct abstractions - you merely apply these rules, repeatedly, and abstractions will naturally appear._

**Chapter 5 - Separating Responsibilities**

**Identifying Patterns in Code**

- Do any methods have the same shape?
    
- Do any methods take an argument of the same name? This is usually a code smell!
    
- Do arguments of the same name always mean the same thing?
    
- Do the tests in conditionals have anything in common?
    
- How many branches do the conditionals have?
    
- Do the methods contain any code other than the conditional?
    
- Does each method depend more on the argument that got passed, or on the class as a whole?

**Do any methods have the same shape?**

You can identify same-shaped methods by doing the Squint Test.

Testing for equality is better than testing for less than or greater than. It increases precision and hence enables future refactorings.

**_Insisting upon messages_**

_As an OO practitioner, if you see a conditional, the hairs on your neck should stand up. You should feel entitled to send messages to objects._

_There's a big difference between a conditional that selects a correct object and one that supplies behaviour. The forner s acceptable but the latter suggests there are_ **_missing objects in your domain_**_._

**_Extracting Classes_**

_Primitive obsession_ - when primitive data types (string, int etc.)) are used to model concepts in your domain.

_Experienced OO programmers deftly create virtual worlds in which ideas are as real as physical things._

_Name things at one higher level of abstraction_ rule applies more to methods than to classes. Methods should be named after what they **_mean_**_, classes should be named after what they are._

_Extract Class refactoring - Martin Fowler_

**_Appreciating Immutability_**

_A variable us that which varies, or in maths, a quantity which admits an infinite number of values in the same expression._

Easy to test, no thread safety issues with immutable objects.

The costs of caching and mutation are interrelated. If the thing you cache doesn't mutate, your local copy is good forever.

**_Cacher_** - In French, means to conceal or hide

The first solution to any problem should avoid caching, use immutable objects and treat object creation as free.

**_Chapter 6 - Replacing Conditionals with Objects_**

TO READ