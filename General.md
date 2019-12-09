# Best practices in Programming

## Motivation (what good practices serve?):
- Efficient programming
- Efficient debugging
- Maintainability and extendability

## Values:
- Simplicity
- Readability
  - Better to have a readable code than heavily commented code, as comments can get outdated.
- Consistency
  - Better to know what to expect than think twice
  - Use of standards and convenitons 

## GUI design

Think of a GUI as a [state machine](http://en.wikipedia.org/wiki/Finite-state_machine).
See also [Model-view-controller model](http://en.wikipedia.org/wiki/Model-view-controller)

- internal states
    - **model**: does computations that change the internal state
    - **view** : GUI state
- external inputs (user input, via 'view')
- **controller**: a transition function (aka synchronisation):

The *model* should be implemented separately from other parts. This ensures testability.

The *controller* is usually integrated with the *view*. If very complex, can be represented by a hash table (dictionary).

