# Recognizable-Turing-Machine

## 
Created a Turing Machine using YAML languange to recognize the language 1<sup>n</sup>0<sup>n</sup>1<sup>n+m</sup>


### Template by  [Daniel Chahine](https://github.com/DanielChahine0)
<hr>

This Turing machine Recognizes the language L(M)={1<sup>n</sup> 0<sup>n</sup> 1<sup>n+m</sup> | n,m ≥ 1}

The Machine could be viewd using [THIS LINK](https://turingmachine.io/?import-gist=fc493db5be7246c90e45b934db5dad0a):

## The machine is split into 4 parts:
> # Start
The machine start by crossing of the first 1 from the tape. If the tape doesn't start with 1, it dies and does not get accepted
```
  start:
    1: {write: "x", R: loop1}    
```
<br>

> # Loops
Loop are responsible for skipping some terms in the tape. When crossing off the 1's loops are needed to skip the 0's. When crossing off the 0's loops are needed to skip the crossed off characters.
```
loop1:
    1: R
    0: {R: skip0}
  loop0:
    0: R
    'y': R
    1: {write: "y", L: loopback}
  loopback:
    1: L
    0: L
    'y': L
    'x' : {R: decider}
```
<br>

> # Decider
The decider is important as it decides when to read the 1's, read the 0's, move to the end, and accept the tape 
```
decider:
    0: {write: "x", R: loop0}
    1: {write: "x", R: loop1}
    ' ': {R: accept}
    y: R
```

<br>

> # Accept
The accept state is just the last state the tape could rest in. It is an empty state that do have any transition coming out of it.
```
  accept:
```

<br>
<hr>
<hr>

This is not supposed to be the **perfect solution** or the most efficient one, this is just **my way** of doing this challenge, feel free to improve my Turing Machine and play with its parameters.


```
Daniel Chahine
```