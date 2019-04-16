# Therapeutic Refactoring

To refactor a complicated piece of code:

1. Scan the method for chunks.
1. Add characterization tests for the method. A characterization test is essentially a safety net to make sure that nothing breaks while performing the refactor.
1. Break out the pickaxe!

### Writing the Characterization Tests
1. Write a test that calls the method with a stub/stubbed input.
1. Assert and use the error message to determine output.
1. Check where it fails and add methods/properties onto stub.
1. Make sure the test exercises the low level details of the method (ie. improve the test input).
1. Instead of reasoning about tough parts of the code, just write a test. This means that we assert our assumptions and the unhappy flows.

With the characterization tests in place, we can extract the method into its own sandbox environment using the refactoring technique [Replace Method with Method Object](https://refactoring.com/catalog/replaceMethodWithMethodObject.html). Now:

1. We start by deleting any cruft we can find (ie. unnecessary code).
1. We extract chunks into their own methods. Naming these is probably the hardest part of the whole refactor.
1. We scan for local variables, clean them up and repeat step 2.

In other words:

1. Quarantine
1. Extract
1. Illuminate junk
1. Repeat
