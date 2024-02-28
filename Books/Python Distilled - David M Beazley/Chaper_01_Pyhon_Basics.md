# Chapter - One: Python Basics

## 1.0.0 Python Basics  

This chapter is an overview of core python language. Here topics such as variables, data types, expressions, control flow, functions, classes and input/output are covered. This chapter concludes with discussion of modules, script writing, packages and tips on organising large programs

- [1.1.0 Running Python](#110-running-python)
- [1.2.0 Python Programs](#120-python-programs)
- [1.3.0 Primitives, Variables, and Expressions](#130-primitives-variables-and-expressions)
- [1.4.0 Arithmetic Operators](#140-arithmetic-operators)
- [1.5.0 Conditionals and Control Flow](#150-conditionals-and-control-flow)
- [1.6.0 Text Strings](#160-text-strings)
- [1.7.0 File Input and Output](#170-file-input-and-output)
- [1.8.0 Lists](#180-lists)
- [1.9.0 Tuples](#190-tuples)
- [1.10.0 Sets](#1100-sets)
- [1.11.0 Dictionaries](#1110-dictionaries)
- [1.12.0 Iteration and Looping](#1120-iteration-and-looping)
- [1.13.0 Functions](#1130-functions)
- [1.14.0 Exceptions](#1140-exceptions)
- [1.15.0 Program Termination](#1150-program-termination)
- [1.16.0 Objects and Classes](#1160-objects-and-classes)
- [1.17.0 Modules](#1170-modules)
- [1.18.0 Script Writing](#1180-script-writing)
- [1.19.0 Packages](#1190-packages)
- [1.20.0 Structuring an Application](#1200-structuring-an-application)
- [1.21.0 Managing Third-Party Packages](#1210-managing-third-party-packages)
- [1.22.0 Python: It Fits Your Brain](#1220-python-it-fits-your-brain)  

## 1.1.0 Running Python  

Python programs are executed by an interpreter. There are many different environments in which the Python interpreter might run—an IDE, a browser, or a terminal window. However, underneath all that, the core of the interpreter is a text-based application that can be started by typing python in a command shell such as bash. Since Python 2 and Python 3 might both be installed on the same machine, you might need to type python2 or python3 to pick a version. This book assumes Python 3.8 or newer.  

When the interpreter starts, a prompt appears where you can type programs into a so-called `“read-evaluation-print loop” (or REPL)`. For example, in the following output, the interpreter displays its copyright message and presents the user with the >>> prompt, at which the user types a familiar “Hello World” program:  

```python
Python 3.8.0 (default, Feb 3 2019, 05:53:21)
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.38)] on
darwin
Type "help", "copyright", "credits" or "license" for more
information.
>>> print('Hello World')
Hello World
>>>
```  

Certain environments may display a different prompt. The following output is from ipython (an alternate shell for Python):  

```python
Python 3.8.0 (default, Feb 4, 2019, 07:39:16)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.5.0 -- An enhanced Interactive Python. Type '?' for
help.
In [1]: print('Hello World')
Hello World
In [2]:
```  

Regardless of the exact form of output you see, the underlying principle is the same. You type a command, it runs, and you immediately see the output. Python’s interactive mode is one of its most useful features because you can type any valid statement and immediately see the result. This is useful for debugging and experimentation. Many people use interactive Python as their desktop calculator. For example:  

```python
>>> 6000 + 4523.50 + 134.25
10657.75
>>> _ + 8192.75
18850.5
>>>
```  

When you use Python interactively, the variable _ holds the result of the last operation. This is useful if you want to use that result in subsequent statements. This variable only gets defined when working interactively, so don’t use it in saved programs. You can exit the interactive interpreter by typing quit() or the EOF (end of file) character. On UNIX, EOF is Ctrl+D; on Windows, it’s Ctrl+Z.

## 1.2.0 Python Programs  

If you want to create a program that you can run repeatedly, put statements in a text file. For example:  

```python
# hello.py
print('Hello World')
```  

Python source files are `UTF-8-encoded` text files that normally have a `.py` suffix. The `#` character denotes a comment that extends to the end of the line. International (Unicode) characters can be freely used in the source code as long as you use the UTF-8 encoding (this is the default in most editors, but it never hurts to check your editor settings if you’re unsure). To execute the hello.py file, provide the filename to the interpreter as follows:  

```python3
shell% python3 hello.py
Hello World
shell%
```  

`# It is common to use #! to specify the interpreter on the first line of a program, like this:`  
`# !/usr/bin/env python3`  
`print('Hello World')`  

On UNIX, if you give this file execute permissions `(for example, by chmod +x hello.py)`, you can run the program by typing `hello.py` into your shell. On Windows, you can double-click on a .py file or type the name of the program into the Run command on the Windows Start menu to launch it. The `#!` line, if given, is used to pick the interpreter version (Python 2 versus 3). Execution of a program might take place in a console window that disappears immediately after the program completes— often before you can read its output. For debugging, it’s better to run the program within a Python development environment. The interpreter runs statements in order until it reaches the end of the input file. At that point, the program terminates and Python exits.  

## 1.3.0 Primitives, Variables, and Expressions  

Python provides a collection of primitive types such as integers, floats, and strings:  

```python
42 # int
4.2 # float
'forty-two' # str
True # bool
```  

A variable is a name that refers to a value. A value represents an object of some type:  

```python
x = 42
```  

Sometimes you might see a type explicitly attached to a name. For example:  

```python
x: int = 42
```  

The type is merely a hint to improve code readability. It can be used by third-party code-checking tools. Otherwise, it is completely ignored. It does not prevent you from assigning a different kind of value later.
An expression is a combination of primitives, names, and operators that produces a value:  
`2 + 3 * 4 # -> 14`  
The following program uses variables and expressions to perform a compound-interest calculation:  

```python
# interest.py
principal = 1000 # Initial amount
rate = 0.05 # Interest rate
numyears = 5 # Number of years
year = 1
while year <= numyears:
principal = principal * (1 + rate)
print(year, principal)
year += 1
```  

following while in `interest.py` execute on each iteration. Python doesn’t specify the amount of required indentation, as long as it’s consistent within a block. It is most common to use four spaces per indentation level.  

One problem with the interest.py program is that the output isn’t very pretty. To make it better, you could right-align the columns and limit the precision of principal to two digits. Change the `print()` function to use a so-called f-string like this:  
`print(f'{year:>3d} {principal:0.2f}')`  

In the f-string, variable names and expressions can be evaluated by enclosing them in curly braces. Optionally, each substitution can have a formatting specifier attached to it. `'>3d'` means a three-digit decimal number, right aligned. `'0.2f'` means a floating-point number with two decimal places of accuracy. More information about these formatting codes can be found in `Chapter 9`.
Now the output of the program looks like this:  

```bash
1 1050.00
2 1102.50
3 1157.62
4 1215.51
5 1276.28
```  

When executed, it produces the following output:  

```bash
1 1050.0
2 1102.5
3 1157.625
4 1215.5062500000001
5 1276.2815625000003 
```  

The while statement tests the conditional expression that immediately follows. If the tested condition is true, the body of the while statement executes. The condition is then retested and the body executed again until the condition becomes false. The body of the loop is denoted by indentation. Thus, the three statements

## 1.3.1 Identifying Primitive Types

## 1.3.2 Primitive Methods

## 1.4.0 Arithmetic Operators
## 1.5.0 Conditionals and Control Flow
## 1.6.0 Text Strings
## 1.7.0 File Input and Output
## 1.8.0 Lists
## 1.9.0 Tuples
## 1.10.0 Sets
## 1.11.0 Dictionaries
## 1.12.0 Iteration and Looping
## 1.13.0 Functions
## 1.14.0 Exceptions
## 1.15.0 Program Termination
## 1.16.0 Objects and Classes
## 1.17.0 Modules
## 1.18.0 Script Writing
## 1.19.0 Packages
## 1.20.0 Structuring an Application
## 1.21.0 Managing Third-Party Packages
## 1.22.0 Python: It Fits Your Brain