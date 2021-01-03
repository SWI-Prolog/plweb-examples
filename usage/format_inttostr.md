# Convert an integer to a string of 0s and 1s

Take advantage of format/3 to convert an integer to a string of 0s and 1s with
a given minimum length, padding with 0s on the left if necessary.

```
int_to_binary_str(Int, Length, Str) :-
    atomic_list_concat(["~|~`0t~2r~", Length, "+"], Fmt),
    format(string(Str), Fmt, Int).
```

```
?- int_to_binary_str(10, 1, Str).
Str = "1010".

?- int_to_binary_str(10, 10, Str).
Str = "0000001010".
```
