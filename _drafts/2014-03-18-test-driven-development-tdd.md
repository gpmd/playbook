---
layout: blog
category: blog
published: false
title: "Test-Driven Development [TDD]"
---


## What

Test-Driven Development is a discipline for writing software. The developer works in a short repetitive cycle known commonly as: Red, Green, Refactor. Each phase of the cycle requiring different action to be undertaken:

1. [**Red**: Write a failing test](#red)
2. [**Green**: Write just enough code to pass the test](#green)
3. [**Refactor**: Refactor both tests and production code](#refactor)

As TDD is a discipline, it like other disciplines requires practise. Practising TDD on a particular problem is commonly called a 'Code Kata'. Code Katas should be practised regularly when an active project employing TDD is not being undertaken, this will ensure the developer doesn't lose the discipline.

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

<a name="fizzbuzz-naming"></a>Lets imagine we are implementing FizzBuzz. The first and simplest test case we know is that when given the number 1, it prints the number 1, so lets call it just that: '**TestItPrints1WhenGiven1**'. Next test case is that when given the number 2 it prints the number 2, so lets keep consistent and call it: '**TestItPrints2WhenGiven2**'

Lets now imagine we are implementing a javascript powered menu that converts a UL into an interactive menu. Our first behaviour here is likely that given an ID it grabs the DOM element so lets call our first test case: '**TestItGetsDomElementById**'. Now we can get DOM elements our second behaviour is that it will display a warning if the DOM element got by ID is not an UL, so lets call that: '**TestItDisplaysWarningIfDomElementIsNotUL**'

As you can see, each test name is an apt summary of exactly the behaviour we require, there is no ambiguity about what the production code should be doing.

#### Writing The Test Case

Writing tests at an abstract level is about 2 things:

1. Scaffolding how you intend your code to work. E.g. The method name you intend to call and what parameters (if any) it will accept, and what it may or may not return.
2. Defining the acceptance criterea that signals if the code is working or not. E.g. In our FizzBuzz example above, when our method receives a '1' it is only considered working if it returns a '1' and not if it returned a '2'.

Once you have your behaviour and name hopefully its fairly evident exactly what you need to do. To help solidify this, follow along the FizzBuzz example below: 

##### Red: FizzBuzz Step 1

Following on from the [FizzBuzz test name](#fizzbuzz-naming) examples above, here is the first failing test for '**TestItPrints1WhenGiven1**':

``` php
function TestItPrints1WhenGiven1() {
	if (Translate(1) != 1) {
		print("FAIL! ". Translate(1) . " != 1");
	}
}
```

I have elected to call the method under test `Transalate()` and it takes a single argument, the int that we want to translate (or not). Notice that `Translate()` doesn't exist yet, another benefit of TDD is that you get to decide on your public interfaces before you write them, not after!

If I were to run the above, I should get an error along the lines of no method `Translate()` exists. This is sufficient for the Red phase, we can now move onto the [Green phase](#green).

##### <a name="fizzbuzz-red-2"></a>Red: FizzBuzz Step 2

Now that we have 1 passing test and nothing to refactor, we can move onto writing our second test '**TestItPrints2WhenGiven2**':

``` php
function TestItPrints2WhenGiven2() {
	if (Translate(2) != 2) {
		print("FAIL! ". Translate(1) . " != 2");
	}
}
```

Running the above produces:
```
FAIL! 2 != 2
```

This looks rather similar to our first test, and that has been noted. We will get to it in the next Refactor phase, but for now onto [Green phase](#fizzbuzz-green-2)

##### <a name="fizzbuzz-red-3"></a>Red: FizzBuzz Step 3

We now have 2 passing tests, albeit very simple, our next test however is where things get interesting. We now hit the case where by we pass '3' to our `Translate()` method and require it to return 'Fizz'. I think we should call our test '**TestItPrintsFizzWhenGiven3**', and heres what it looks like:

``` php
function TestItPrintsFizzWhenGiven3() {
	assertItTranslatesArgIntoExpected(3, "Fizz");
}
```

Running the above produces:
```
FAIL! 3 != Fizz
```

Luckily as we refactored our code implementing this test was just a 1 liner. Onto the [Green phase](#fizzbuzz-green-3)

###  <a name="green"></a>GREEN: Writing just enough code

Writing just enough code to pass your test is probably the next hardest part of TDD. Its very easy to get carried away implementing more functionality into your target method without writing more tests, especially in the beginning. Your target is to satisfy the current failing test with the smallest amount of change to your production code. That may sometimes require you just to return a constant only to know in the next test you are going to replace that with a variable, but in the beginning its best to be more pedantic to really ingrain the discipline. Over time you will start to notice patterns and will be able to save your self the pedanticism.

##### Green: FizzBuzz Step 1

Here is our code to pass our first test:

``` php
function Translate($i) {
	return 1;	
}
```

Notice how we are literally returning just a constant '1'. This is perfectably acceptable as our test runs with no failures, and is the smallest amount of change required to pass.

We now move into our [Refactoring phase](#refactor).

##### <a name="fizzbuzz-green-2"></a>Green: FizzBuzz Step 2

Keeping in mind the least amount of change required to implement the next failing test, here is our passing production code:

``` php
function Translate($i) {
	return $i;	
}
```

We have turned our constant '1' into the arg varibale $i. Arguably we could of added an if statement to check the value of $i and return the appropriate constant, but I believe this to be a simpler code change.

Tests are passing, so now onto the [Refactoring phase](#fizzbuzz-refactor-2)

##### <a name="fizzbuzz-green-3"></a>Green: FizzBuzz Step 3

We now have our first interesting test case, we need to get our function to return 'Fizz' when it receives a '3'. I believe the easiest way to do that would be to add a condition to check the `$i` variable. Here is what I have chosen to implement:

``` php
function Translate($i) {
	if ($i == 3){
		return "Fizz";
	}
	return $i;	
}
```

Our tests are passing so we can move onto the next [Refactoring phase](#fizzbuzz-refactor-3)

### <a name="refactor"></a>REFACTORING: Refactor both tests and production code

The refactoring phase is akin to tidying up as you go along. This is where we enforce our over-arching ideologies such as DRY (Don't repeat yourself) and YAGNI (You ain't gunna need it). We must refactor BOTH production and test code as arguably both are as important as the other. It is vital to note that during this phase no new behaviour should be introduced, the definition of refactoring for the purposes of TDD is: _Changing the structure of the code without changing the behaviour_. All tests must still pass at the end of this phase to be able to continue back into Red.

##### Refactor: FizzBuzz Step 1

Following our FizzBuzz example there isn't anything to be refactored so we would skip back into the [Red phase](#fizzbuzz-red-2)

##### Refactor: FizzBuzz Step 2

Our current code base looks as follows:

``` php
function TestItPrints1WhenGiven1() {
	if (Translate(1) != 1) {
		print("FAIL! ". Translate(1) . " != 1");
	}
}

function TestItPrints2WhenGiven2() {
	if (Translate(2) != 2) {
		print("FAIL! ". Translate(1) . " != 2");
	}
}
```

``` php
function Translate($i) {
	return $i;	
}
```

I believe we have a DRY violation in our test code base, the 2 test contents look rather similar, and I'd like to refactor into a helper function as follows:

``` php
function assertItTranslatesArgIntoExpected($arg, $expected) {
	if (Translate($arg) != $expected) {
		print("FAIL! ". Translate($arg) ." != ". $expected);
	}
}
```

This leaves us with in our test code:

``` php
function TestItPrints1WhenGiven1() {
	assertItTranslatesArgIntoExpected(1, 1);
}

function TestItPrints2WhenGiven2() {
	assertItTranslatesArgIntoExpected(2, 2);
}

function assertItTranslatesArgIntoExpected($arg, $expected) {
	if (Translate($arg) != $expected) {
		print("FAIL! ". Translate($arg) ." != ". $expected);
	}
}
```

There is still nothing to refactor for the production code, and that is ok. Back into the [Red phase](#fizzbuzz-red-3)