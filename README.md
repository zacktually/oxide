# Oxide Programming Language v0.5a
An interpreter and compiler for the oxide programming language.

### Table of Contents
1. [Introduction](#introduction)
2. [Data Types](#data-types)
3. [Symbol Binding](#symbol-binding)
4. [Indexing](#indexing)
5. [Expressions](#expressions)
6. [Conditionals](#conditionals)
7. [Loops](#loops)
8. [Functions](#functions)

### Introduction
Oxide is built with simplicity, power and efficiency in mind.
We've tried to create a language that incorporates the best functionality combined with a simple, less verbose syntax.

The Oxide interpreter and compiler is written in Rust.

##### Syntax
**Oxide does not use semicolons at the end of a line of code**

### Data Types

##### Primitives
Oxide has only 3 basic primitive types: Numbers, Booleans and Strings

Numbers: Oxide uses a single type to represent a number. The interpreter/compiler will determine the underlying representation (int, float, double...etc.) based on the context and will perform any casts automatically.
```
5
-72
5.3
```

Booleans:
```
true
false
```

Strings:
```
""          // The empty string
"a"         // A string of length 1
"Hello"     // A string of length 5
```

##### Collections
Vectors
```
[1 2 3 4 5]
```

Lists
```
(1 2 3)
```

Structures
```
{}
```

### Symbol Binding
- Oxide is statically-typed. Once you bind a symbol, you cannot assign a value of a different type to that symbol.

##### Mutable Variables
```
var x = 5
```

##### Immutable Values
```
val y = 3
```

### Indexing
We've made a rather controversial choice to start collection indexes at 1 instead of 0.
```
val x = (1 2 3 4 5 6 7)

x[1]   // 1
x[3]   // 3
```
Negative indexes start from the end of the collections.
```
x[-1]   // 7
```
You can get a subset of a collection by using a range.
```
x[3:5]   // (3 4 5)
```

```
x[-1:1]   // (7 6 5 4 3 2 1)
```
The same can be done with strings or other collections
```
val s = "olleh"

x[1]      // "o"
x[-1]     // "h"
x[-1:1]   // "hello"
```

### Expressions
```
+ - * / ^ %
```
Evaluating expressions
```
+(1 2 3 4)   // 10
-(10 3)      // 7

```

##### Comparators
```
== != > >= < <=
```
```
==(1 1)   // true
>=(1 3)   // false
```
```
<=(1 2 2 3 4)   // true
<=(1 2 3 4 3)   // false
```

##### Boolean
```
! && ||
```
```
&&(1 1 1 1)   // true
||(0 0 1 0)   // true
```

##### Bitwise
```
~ & | ~& ~|
```
```
~(1)   //
```

### Control Statements

##### Conditionals
```
<if ==(x 3)>
</if>
```

##### Loops
```
<loop>
</loop>
```

```
<while >=(x 0)>
</while>
```

```
<for item in items>
</for>

<for i in (1:10)>
</for>
```

##### Functions
```
<func x:Int y:String>
</func>
```
