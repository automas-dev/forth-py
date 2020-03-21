# Forth PY

A Forth parser written in Python 3.5

## Description

This is a very elegantly written Forth implemented in Python.  [Some Forth's](https://github.com/howerj/forth-cpu/blob/master/embed.c) 
are implemented very close to the hardware and thus with 
convoluted logic.   This Forth is implemented 
very close to the concepts, making it very easy to understand. 
Really quite a work of love.

The author carefully divides the code up into different files with 
meaningful names.   [Many other Forths](https://github.com/utoh/pygmy64/blob/master/pygmykernel.py) just have a single file. It is well worth reading his code. 

Start off by taking a look at main.py. 

The class State holds the state of the Forth Interpreter.  
It is a proper object. Perhaps you could have many Forth machines in your 
application. Other Forths take a more functional approach. 

The main routine reads a line of text, calls parse text, and if all is good, 
return ok. 

Predefs.py contains all of the predefined words.  
It includes both words written in Python and in Forth. 
They are added to the dictionary of words at startup. 
It would be good if the words defined in Forth were in a different file. 

The compiler is very interesting.  
If recognizes nested blocks, things like if-then-else, and do loops, and then 
creates a node in the word definition, which executes 
the child statements.  Sort of generates a tree representation of the word around blocks.   I have not seen this elsewhere.  

Parse text calls a lexer on the input line, and processes each word. 

The lexer is in file lexer.py, very carefully written. 

He does custom __repr__ methods for each class. 
Lots of error checking throughout the code.  That is good. 

Overall lots of code.  All very nicely written.  After reviewing many Python 
Forths I have chosen to use this one. 


## Usage

``` bash
$ python main.py
> : foo ." Hello World" ;
 ok
> foo
Hello World ok
> 
```

## Licence

forth-py uses the [MIT](LICENCE) licence
