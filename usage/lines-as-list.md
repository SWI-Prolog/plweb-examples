# Read all lines to a list

```
file_lines(File, Lines) :-
    setup_call_cleanup(open(File, read, In),
       stream_lines(In, Lines),
       close(In)).

stream_lines(In, Lines) :-
    read_string(In, _, Str),
    split_string(Str, "\n", "", Lines).
```

This loads all lines to memory as strings. If we use the [[Unix dictionary words][https://en.wikipedia.org/wiki/Words_(Unix)]]:

```
?- file_lines("/usr/share/dict/words", Lines).
Words = ["A", "a", "aa", "aal", "aalii", "aam", "Aani", "aardvark", "aardwolf"|...].
```
