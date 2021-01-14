# Grabbing an unbound variable from argument 1

## Standard usage 

```
?- nonground(f(_),K).
true.

?- nonground(f(X,_,_),K).
X = K.
```

## Failure if first argument is ground

```
?- nonground(f(x),K).
false.
```

## Unusual usage

```
?- nonground(f(X),X).
true.
```

## Unusual usage leading to instantiation of argument 1

```
?- nonground(f(X,Y,_),Y).
X = Y.

?- nonground(F=f(X,_,_),foo).
F = foo.
```
