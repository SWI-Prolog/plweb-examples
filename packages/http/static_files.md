# Serve static files from an HTTP server

The SWI-Prolog HTTP server doesn't not   server static files by default.
You explicitly have to  add  a  _handler_   telling  it  to  do  so. The
declarations below tell the  server  to   serve  files  from the current
directory under `/` on the server.

```
:- use_module(library(http/http_server)).
:- use_module(library(http/http_files)).

:- http_handler(root(.), http_reply_from_files('.', []), [prefix]).
```

Now, start the server and visit   http://localhost:8080/.


```
?- http_server([port(localhost:8080)]).
% Started server at http://localhost:8080/
true.
```

## Remarks

  - Note that the ``localhost:`` only binds the  _loopback   network_,
    avoiding to expose your website to the outside world.
  - The first argument of http_reply_from_files/3 is subject to search
    using absolute_file_name/3.  This allows to abstract the physical
    location of the directory as well as virtually merge the contents
    of multiple physical directories.
