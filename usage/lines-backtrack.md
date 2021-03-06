# Backtrack over lines in a file

~~~
file_line(File, Line) :-
    setup_call_cleanup(open(File, read, In),
        stream_line(In, Line),
        close(In)).

stream_line(In, Line) :-
    repeat,
    (   read_line_to_string(In, Line0),
        Line0 \== end_of_file
    ->  Line0 = Line
    ;   !,
        fail
    ).
~~~

This will backtrack over consecutive lines in the input. If we use the [Unix dictionary words](https://en.wikipedia.org/wiki/Words_(Unix)):

~~~
?- file_line("/usr/share/dict/words", Word).
Word = "A" ;
Word = "a" ;
Word = "aa" ;
Word = "aal" ; % and so on
~~~

This doesn't load all lines to memory, so it can be used with very large files.

@see read_line_to_codes/2 to read to a code list instead of a string
@see read_string/5 for more control over the separator and stripping
