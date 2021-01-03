# Find the run-length encoding of a list

The list in the first argument must be ground.

```
list_rle(L, R) :-
    pairs_keys_values(Pairs, L, L),
    group_pairs_by_key(Pairs, Grouped),
    maplist(group_encoding, Grouped, R).

group_encoding(X-Xs, X-N) :-
    length(Xs, N).
```

```
?- list_rle([a,a,b,a,a,a,a,c,c,c], R).
R = [a-2, b-1, a-4, c-3].
```
