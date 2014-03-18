---
layout: blog
category: blog
published: false
title: "Test-Driven Development [TDD]"
---


## What

Test-Driven Development is a discipline for writing software. The developer works in a short repetitive cycle known commonly as: Red, Green, Refactor. Each phase of the cycle requiring different action to be undertaken:

1. [**Red**: Write a failing test][#red]
2. **Green**: Write just enough code to pass the test
3. **Refactor**: Refactor both tests and production code

As TDD is a discipline, it like other disciplines requires practise. Practising TDD on a particular problem is commonly called a 'Code Kata'. Code Katas should be practised regularly when an active project employing TDD is not being undertaken, this will ensure the developers doesn't loose the discipline.

## Why

Writing the minimum amount of bug free code to satisfy the clients requirements is hard, really hard.

Every line of code written by a developer has the potential to introduce new bugs into the system, every method composed has the potential to veer away from the customer requirements and every design pattern introduced has the potential to add un-needed complexity. Add to this that there are many solutions to any given software problem and that developers come with their own set of flaws and you quickly see the cocktail of complexity emerging. No wonder then why ~65% of software projects undertaken fail (note that the developer isn't the sole reason for this failure rate, but is definitely apart of it).

It is for these reasons we use TDD. TDD provides an assurance that bare back development does not, and its not just as developers that we see the benefits. The benefits that we have found from practising TDD are as follows:

#### Beneficiaries:
- Code
- Developer
- Business
- Process (Software development process)

#### Benefits:
- **Facilitating change**: Being able to make large changes to your existing system is much less daunting and risky when you know you have tests to cover your back. [_Developer, Business_]
- **Better design**: You naturally develop with modularisation in mind, otherwise you wouldn't be able to test the code you are writing. [_Code, Developer_]
- **Living documentation**: Provided you name your tests well, all the documentation required for another developer to understand your code is in the tests. [_Code, Developer_]
- **Ease integrations**: Connecting distant services becomes much less of an ordeal when you practise TDD as both ends have already been tested with mocks. [_Business, Developer_]
- **Flow and productivity**: Spending less time debugging (which naturally reduces with TDD) means you spend more time developing, and moving forwards is much more productive. [_Process, Developer_]
- **Stronger guarantees**: When you practise TDD you have larger guarantee that the code you deploy works. [_Business, Developer, Code_]
- **Regression**: Regression tests are baked into the TDD process, thus you get regression tests for free. [_Business, Developer, Code_]

## How

### <a name="red"></a>RED: Writing Failing Tests

#### Naming Tests

Naming tests is the first step of the Red phase and sometimes seen as the hardest part of TDD, and rightly so, as everyone knows the 2 hardest problems in computing sciences is cache invalidation and naming things (Phil Karlton). The aim is to summerise in a sentance the specific behaviour you require, and call your test that. Here are a few examples:

Lets imagine we are implementing FizzBuzz. The first and simplest test case we know is that when given the number 1, it prints the number 1, so lets call it just that: '**TestItPrints1WhenGiven1**'. Next test case is that when given the number 2 it prints the number 2, so lets keep consistent and call it: '**TestItPrints2WhenGiven2**'

Lets now imagine we are implementing a javascript powered menu that converts a UL into an interactive menu. Our first behaviour here is likely that given an ID it grabs the DOM element so lets call our first test case: '**TestItGetsDomElementById**'. Now we can get DOM elements our second behaviour is that it will display a warning if the DOM element got by ID is not an UL, so lets call that: '**TestItDisplaysWarningIfDomElementIsNotUL**'

As you can see, each test name is an apt summary of exactly the behaviour we require, there is no ambiguity about what the production code should be doing.

#### Writing The Test Case

Writing test cases is probably the next hardest part of TDD, but much easier than naming. Once you have your name its fairly evident exactly what you need to do, following on from the examples above, here is the first failing test from the FizzBuzz example above:

``` php
function TestItPrints1WhenGiven1() {
	if (Translate(1) != 1) {
		print("FAIL! ". Translate(1) . " != 1");
	}
}

```

I have elected to call the method under test `Transalate()` and it takes a single argument, the int that we want to translate (or not). Notice that `Translate()` doesn't exist yet, another benefit of TDD is that you get to decide on your public interfaces before you write them, not after!

If I were to run the above, I should get an error along the lines of no method `Translate()` exists. This is sufficient for the Red phase, we can now move onto the Green phase.

### GREEN: Writing just enough code

