# elldn

ℒ Data Notation

## Overview

EllDN (ℒ Data Notation, pronounced "*ell* done") is ℒ's Data Notation. It is a superset of JSON, adding lists, symbols,
keywords, types, and generalized typed objects.

Commas are consider whitespace in EllDN, so the following are equivalent:

    [1, 2, 3]
    [1 2 3]

Symbols are tokens that are not valid numbers.
The JSON reserved values `null`, `true`, and `false` are symbols that are defined to have the expected meaning.
EllDN also defines a _keyword_ to be a token ending with a colon (`:`). A _type_ is a symbol surrounded by
angle brackets, i.e. `<string>`.

All other colons are treated as whitespace, like commas are. So the following are valid and equivalent:

    [foo: bar]
    [foo:: bar]
    [foo::::: bar]

All of these represent an vector with one keywords and one symbol as elements, all other colons are ignored. So for example
the following are equivalent:

    {"x": 23, "y": 57}
    {"x" 23, "y" 57}
    {"x" 23 "y" 57}

Symbols, and more commonly, keywords, are useful as keys in an struct (a JSON object):

    {x 23 y: 57}

This has the symbol `x` as a key, and a keyword `y:` as a key. It is valuable to distinguish between symbols and keywords
when using EllDN as language source like the [Ell](https://github.com/boynton/ell) language, as the two are interpreted
differently.

Some more examples:

    () - an empty list
    true - the true value
    foo?
    foo - some other symbol
    foo: - a keyword
    <foo> - a type
    (1 2 3) - a list of 3 elements
    (1, 2, 3) - same thing (commas are optional)
    {"foo": 2, "bar": 3} - a regular JSON object
    {foo: 2, bar: 3} - an object using keywords as keys
    {foo: 2 bar: 3} - commas are optional here, too
    {list-items: (1 2 3) vector-items: [1 2 3]} - an object with list and vector values
    (<string> <number>) - a list of types
    #<point>{x: 23 y: 57} - an object _instance_ of type _<point>_, with a structured value.

Valid JSON is readable as EllDN, although not all EllDN can be expressed as JSON.

For the syntax, see the [Syntax Diagrams](http://boynton.github.io/elldn/elldn.xhtml), generated
from [EBNF](https://github.com/boynton/elldn/blob/master/elldn.ebnf).
