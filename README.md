# Oxide Programming Language v0.5a
A compiler for the oxide programming language.

### Table of Contents
1. [Introduction](#introduction)
2. [Data Types](#data-types)
3. [Symbol Binding](#symbol-binding)
4. [Indexing](#indexing)
5. [Expressions](#expressions)
6. [Control Statements](#control-statements)

<br />
### Data Types

##### Numbers
```
5
-72
5.3
```

##### Booleans
```
true
false
```

##### Strings
```
"a"
"Hello"
```

##### Vectors
```
[1 2 3 4 5]
```

##### Lists
```
(1 2 3)
```

##### Structures
```
{}
```

<br />
### Symbol Binding

##### Mutable Variables
```
var x = 5
```

##### Immutable Values
```
val y = 3
```

### Indexing
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
