
# Python Cheat Sheet

## Single & Double Underscores


### Single Underscore

In a class, names with a leading underscore indicate to other programmers that the attribute or method is intended to be be used inside that class. However, privacy is not _enforced_ in any way. Using leading underscores for functions in a module indicates it should not be imported from somewhere else.

From the [PEP-8](https://peps.python.org/pep-0008/) style guide:
> [!quote]
> `_single_leading_underscore`: weak "internal use" indicator. E.g. `from M import *` does not import objects whose name starts with an underscore.

### Double Underscores

From the [Python docs](https://docs.python.org/3/tutorial/classes.html#private-variables): 

> [!quote]
> Any identifier of the form `__spam` (at least two leading underscores, at most one trailing underscore) is textually replaced with `_classname__spam`, where `classname` is the current class name with leading underscore(s) stripped. This mangling is done without regard to the syntactic position of the identifier, so it can be used to define class-private instance and class variables, methods, variables stored in globals, and even variables stored in instances. private to this class on instances of other classes.

> [!warning]
> Name mangling is intended to give classes an easy way to define “private” instance variables and methods, without having to worry about instance variables defined by derived classes, or mucking with instance variables by code outside the class. Note that the mangling rules are designed mostly to avoid accidents; _it still is possible for a determined soul to access or modify a variable that is considered private._

