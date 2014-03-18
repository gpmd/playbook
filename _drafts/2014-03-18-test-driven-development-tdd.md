---
layout: blog
category: blog
published: false
title: "Test-Driven Development [TDD]"
---


## What

Test-Driven Development is a discipline for writing software. The developer works in a short repetitive cycle known commonly as: Red, Green, Refactor. Each phase of the cycle requiring different action to be undertaken:

- **Red**: Write a failing test
- **Green**: Write just enough code to pass the test
- **Refactor**: Refactor both tests and production code

## Why

Writing the minimum amount of bug free code to satisfy the clients requirements is hard, really hard. Every line of code written by a developer has the potential to introduce new bugs into the system, every method composed has the potential to veer away from the customer requirements and every design pattern introduced has the potential to add un-needed complexity. Add to this that there are many solutions to any given software problem and that developers come with their own set of flaws and you quickly see the cocktail of complexity emerging. No wonder then why ~65% of software projects undertaken fail (note that the developer isnt the sole reason for this failure rate, but is definitely apart of it).

It is for these reasons we use TDD. TDD provides an assurance that bare back development does not, and its not just as developers that we see the benefits. Benefits that we have found from practising TDD are as follows:

####Beneficiaries:
- Code
- Developer
- Business
- Process (Software development process)

####Benefits:
- **Facilitating change**: Being able to make large changes to your existing system is much less daunting and risky when you know you have tests to cover your back. [Developer, Business]
- **Better design**: You naturally develop with modularisation in mind, otherwise you wouldn't be able to test the code you are writing. [Code, Developer]
- **Living documentation**: Provided you name your tests well, all the documentation required for another developer to understand your code is in the tests. [Code, Developer]
- **Ease integrations**: Connecting distant services becomes much less of an ordeal when you practise TDD as both ends have already been tested with mocks. [Business, Developer]
- **Flow and productivity**: Spending less time debugging (which naturally reduces with TDD) means you spend more time developing, and moving forwards is much more productive. [Process, Developer]
- **Stronger guarentees**: When you practise TDD you have larger guarentee that the code you deploy works. [Business, Developer, Code]
- **Regression**: Regression tests are baked into the TDD process, thus you get regression tests for free. [Business, Developer, Code]

