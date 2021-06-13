# Strip	text from leading and trailing white space

We can use split_string/4 to strip   leading  and trailing characters by
using an empty set of _split_ characters.  Now   we  get a list with one
element as reply. This can also be  used   to  check  that a string only
holds a certain set of characters,   e.g., the second examples validates
that a string only holds white space.  The last example illustrates that
split_string/4 accept atoms as input.


```
?- split_string(" Hello world ", "", "\t\s", [Stripped]).
Stripped = "Hello world".

?- split_string(" \t", "", "\t\s", [""]).
true.

?- split_string(' \t', "", "\t\s", [""]).
true.
```
