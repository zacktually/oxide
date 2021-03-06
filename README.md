# Oxide Programming Language v0.5a
An interpreter and compiler for the oxide programming language.

### Table of Contents
1. [Introduction](#introduction)
2. [Syntax](#syntax)
3. [Comments](#comments)
4. [Primitives](#primitives)
5. [Collections](#collections)
6. [Structures](#structures)
7. [Symbol Binding](#symbol-binding)
8. [Indexing](#indexing)
9. [Expressions](#expressions)
10. [Conditionals](#conditionals)
11. [Loops](#loops)
12. [Functions](#functions)
13. [Sample Program](#sample-program)

### Introduction
Oxide is built with simplicity, power and efficiency in mind.
We've tried to create a language that incorporates the best functionality combined with a simple, less verbose syntax.

The Oxide interpreter and compiler is written in Rust.

### Syntax
*Oxide does not use semicolons at the end of a line of code*

### Comments
```
# This is a comment
```

### Primitives
Oxide has only 3 basic primitive types: *Numbers*, *Characters* and *Booleans*

**Numbers**: Oxide uses a single type to represent a number. The interpreter/compiler will determine the underlying representation (int, float, double...etc.) based on the context and will perform any casts automatically.
```
5
-72
5.3
```

**Characters**: Characters are represented with single quotes and are formatted in UTF-8. Putting more than one character between single quotes will result in an error.
```
' '
'a'
'0'
```

**Booleans**:
```
true
false
```

### Collections

**Vectors**: are a collection of *same-type* elements
```
[]                  # An empty vector
[1 2 3 4 5]         # A vector of length 5
```

**Tuples**: are a collection of *any-type* elements
```
()                  # An empty tuple
(1 'c' true)        # A tuple of length 3
```

**Strings**: are a collection of characters
```
""                  # An empty string
"a"                 # A string of length 1
"Hello"             # A string of length 5
```

### Structures
```
{ a:1 b:"123" }
```

### Symbol Binding

##### Mutable Variables
```
var x = 5

x = 3
@print("/x")                  # 3
```

**Static Typing** Oxide is statically-typed. Once you bind a symbol, you cannot assign a value of a different type to that symbol.
```
var x = 5

x = 'c'                       # Error: Cannot re-assign to variable of a differnt type.
@print("/x")                  # 5
```

##### Immutable Values
```
val y = 5

x = 3                         # Error: Cannot re-assign to immutable value.
@print("/x")                  # 5
```

### Indexing
We've made the rather controversial choice to start collection indexes at 1 instead of 0. For more information on why we made this choice, please read *this article*.
```
val x = [1 2 3 4 5 6 7]

x[1]              # 1
x[3]              # 3
```
Negative indexes start from the end of the collections.
```
x[-1]             # 7
```
You can get a subset of a collection by using a range.
```
x[3..5]           # (3 4 5)
```
```
x[-1..1]          # (7 6 5 4 3 2 1)
```
The same can be done with strings or other collections
```
val s = "olleh"

x[1]              # "o"
x[-1]             # "h"
x[-1:1]           # "hello"
```

### Expressions
Expressions are built-in functions
```
+     - Addition
-     - Subtraction
*     - Multiplication
/     - Division
^     - Exponentiation
%     - Modulo
```
*Evaluating expressions*: Oxide uses a unique form of prefix notation when calling functions.
This allows us to simplify this...
```
1 + 2 + 3 + 4
```
...into this.
```
+(1 2 3 4)                   # 10
```
When dealing with data in programming, this is incredibly useful. It allows us to use defined collections as parameters to functions.
```
val x = [10 10 10 10]
+{x}                         # 40
```

##### Comparators
Comparators are simply functions that compare values and return a Boolean value.
```
=      - Is Equal
!=     - Is Not Equal
>      - Is Greater Than
>=     - Is Greater Than or Equal
<      - Is Less Than
<=     - Is Less Than or Equal
```
```
=(1 1)          # true
>=(1 3)         # false
```

Using prefix notation, we can replace this...
```
((x > 5) && (x < 10))
```
...with this less verbose and easier to visualize alternative.
```
>(5 x 10)
```

Using prefix notation also allows many operations to be simplified. For example, checking if a list is sorted...
```
<=(1 2 2 3 4)                   # true
>(1 2 3 4 3)                    # false

var x = ('a' 'b' 'c' 'd')
<={x}                           # true
```

##### Boolean Operations
```
!     - Logical NOT
&     - Logical AND
|     - Logical OR
```
```
!(true)                     # false
!(true false)               # (false true)
&(true true)                # true
&(1 1 0 1)                  # false
|(0 0 1 0)                  # true
&(=(1 1) =('c' 'c'))        # true
```

##### Bitwise Operations
```
~! - Bitwise NOT
~& - Bitwise AND
~| - Bitwise OR
```
```
~!(1)
```

### Control Statements

##### Conditionals
```
<match ==(x 3)>
  true => @print("true")
  false => @print("false")
</match>
```

```
val c = 'd'

var c = <match c>
    'a' => 1
    'b' => 2
    'c' => 3
    else => 0
</match>

@print("/x")                     # 0
```

##### Functions
```
<fn run x:NUM y:STR>
    # CODE GOES HERE
</fn>
```

**Calling Functions**
```
run(5, "hello")
```

**Default Parameters** allow us to implement function overloading with only one function definition
```
<fn run x:0 y:"">
    # CODE GOES HERE
</fn>

run("test")                  # x is 0 and y is "test"
run(3)                       # x is 3 and y is ""
run(1 "test")                # x is 1 and y is "test"
```

##### Lambda Expressions
```
var add1 = fn(y) => +(y 1)
add1(2)                          # 3
```

##### Function Currying with Lambdas
```
var add = fn(a) => fn(b) => +(a b)
add(3)(4)                                   # 7

var add3 = add(3)                           # fn(3)(b)
add3(4)                                     # 7
```

### Implementation on Structs

##### Traits

### Sample Program
```
struct Product = { cost:NUM }
struct Vehicle = { miles:NUM color:STR }
struct Car:(Vehicle Product Drivable) = {}

# CAR METHODS
<fn Car::new:Car color:STR cost:NUM>
    { miles:0 color:color cost:cost }
</fn>

# DRIVABLE TRAIT
<fn Drivable::drive miles:NUM>
    +=(self.miles miles)
</fn>

<fn Drivable::printStatus>
    <match self.miles>
        0 => @print("NEW")
        else => @print("USED")
    </match>
</fn>

# MAIN FUNCTION
<fn main>
   var my_car = Car::new()
   my_car.printStatus()         # NEW
   my_car.drive(10)
   my_car.printStatus()         # USED
</fn>
```
