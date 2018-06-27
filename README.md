# Oxide Programming Language v0.5a
A compiler for the oxide programming language.

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

### Symbol Binding

### Mutable Variables
```
var x = 5
```

### Immutable Values
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
