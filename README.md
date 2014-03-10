# elldn

ℒ Data Notation

## Overview

EllDN (ℒ Data Notation, pronounced "*ell* done") is ℒ's Data Notation. It is a superset of JSON, adding lists and symbols.amd relaxing the syntax somewhat.

Commas are treated as whitespace, so the following two forms are equivalent:

    [1, 2, 3]
    [1 2 3]

Colons are also treats as whitespace, so these are also equivent:

	{"x": 23, "y": 57}
	{"x" 23, "y" 57}
	{"x" 23 "y" 57}

Symbols are tokens that are not valid numbers. The JSON reserved values 'null', 'true', and 'false' are symbols that are defined to have the expected meaning.
An additional reserved symbol 'nil' is introduced as a synonym of 'null'.

For example:

    (1 2 3) - a list of 3 elements
    (1, 2, 3) - same thing (commas are optional)
    {"foo": 2, "bar": 3} - a regular JSON object
    {foo: 2, bar: 3} - an object using symbols as keys
    {foo: 2 bar: 3} - commas are optional
    {list-items: (1 2 3) vector-items: [1 2 3]} - an object with list and vector values
 
The syntax is as follows:

    object
        {}
        { members }

    members
        pair
        pair members
        pair, members

    pair
        key value
        key : value

    key
        string
        symbol

    array:
        []
        [ elements ]

    elements
        value
        value elements
        value, elements

    list:
        ()
        ( elements )

    value:
        string
        number
        symbol
        true
        false
        null
        nil
        object
        array
        list

