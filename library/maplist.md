## Check all elements of a list

```
?- maplist(atom, [a, b, c]).
true.

?- maplist(atom, [a, 2, c]).
false.

?- maplist(between(1, 3), [1, 2, 3]).
true.

?- maplist(between(1, 3), [1, 2, 99]).
false.
```

## Fill a list

```
?- length(L, 5), maplist(=(foo), L).
L = [foo, foo, foo, foo, foo].
```

## Convert all elements

```
?- maplist(atom_chars, [foo, bar, baz], Cs).
Cs = [[f, o, o], [b, a, r], [b, a, z]].
```

## With a non-deterministic goal

```
?- length(L, 3), maplist(between(0, 1), L).
L = [0, 0, 0] ;
L = [0, 0, 1] ;
L = [0, 1, 0] ;
L = [0, 1, 1] ;
L = [1, 0, 0] ;
L = [1, 0, 1] ;
L = [1, 1, 0] ;
L = [1, 1, 1].
```
