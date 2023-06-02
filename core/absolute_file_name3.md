# Using absolute_file_name/3 to find files

With `swipl` started from ``/home/janw/src/swipl-devel/library/``:

```
?- absolute_file_name('lists.pl', Abs, [access(read)]).
Abs = '/home/janw/src/swipl-devel/library/lists.pl'.
```

Using a search path from any directory.  Using `file_type(prolog)`
sets the extensions to search for.

```
?- absolute_file_name(library(lists)', Abs,
                      [access(read), file_type(prolog)]).
Abs = '/home/janw/src/swipl-devel/library/lists.pl'.
?- absolute_file_name(path(ls), Abs, [access(execute)]).
Abs = '/bin/ls'.
```

We can create our own search path using user:file_search_path/2. In this
example we define two places to search  for `data` files. Search happens
in the order in which file_search_path/2 generates answers.

```
:- multifile user:file_search_path/2.

user:file_search_path(data, MyData) :-
    expand_file_name('~/data', [MyData]).
user:file_search_path(data, '/usr/local/share/data').
```

```
?- absolute_file_name(data(myfile), Abs, [access(read)]).
Abs = '/home/janw/data/myfile'.
```
