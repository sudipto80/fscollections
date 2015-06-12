

add
-------
Returns a new set with an element added to the set. No exception is raised if the set already contains the given element.

```
: 'T -> Set<'T> -> Set<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.add : 'T -> Set  -> Set  (requires comparison)

// Usage:
Set.add value set
```

contains
--------
Evaluates to true if the given element is in the given set.

```
: 'T -> Set<'T> -> bool
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.contains : 'T -> Set  -> bool (requires comparison)

// Usage:
Set.contains element set
```

count
-------
Returns the number of elements in the set.

```
: Set<'T> -> int
```

Example
```fsharp

``` 
Output


difference
----------
Returns a new set with the elements of the second set removed from the first.

: Set<'T> -> Set<'T> -> Set<'T>

Example
```fsharp

let set1 = Set.ofList [ 1 .. 3 ]
let set2 = Set.ofList [ 2 .. 6 ]
let setDiff = Set.difference set2 set1
printfn "Set.difference [2 .. 6] [1 .. 3] yields %A" setDiff

``` 
Output

```
Set.difference [2 .. 6] [1 .. 3] yields set [4; 5; 6] 
```

exists
---------
Tests if any element of the collection satisfies the given predicate. If the input function is predicate and the elements are i0...iN , then this function computes predicate i0 or ... or predicate iN .

```
: ('T -> bool) -> Set<'T> -> bool
```

Example
```fsharp

``` 
Output
```
// Signature:
Set.exists : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.exists predicate set
```

filter
------
Returns a new collection containing only the elements of the collection for which the given predicate returns true .

```
: ('T -> bool) -> Set<'T> -> Set<'T>
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 10]
           |> Set.filter (fun elem -> elem % 2 = 0)
printfn "%A" set1

``` 
Output

```
set [2; 4; 6; 8; 10] 
```

fold
-----
Applies the given accumulating function to all the elements of the set

```
: ('State -> 'T -> 'State) -> 'State -> Set<'T> -> 'State
```

Example
```fsharp

``` 
Output
```
// Signature:
Set.fold : ('State -> 'T -> 'State) -> 'State -> Set  -> 'State (requires comparison)

// Usage:
Set.fold folder state set
```

foldBack
--------
Applies the given accumulating function to all the elements of the set.

```
: ('T -> 'State -> 'State) -> Set<'T> -> 'State -> 'State
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.foldBack : ('T -> 'State -> 'State) -> Set  -> 'State -> 'State (requires comparison)

// Usage:
Set.foldBack folder set state
```

forall
---------
Tests if all elements of the collection satisfy the given predicate. If the input function is p and the elements are i0...iN, then this function computes p i0 && ... && p iN .

```
: ('T -> bool) -> Set<'T> -> bool
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.forall : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.forall predicate set
```

intersect
-----------
Computes the intersection of the two sets.

```
: Set<'T> -> Set<'T> -> Set<'T>
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 3 ]
let set2 = Set.ofList [ 2 .. 6 ] 
let setIntersect = Set.intersect set1 set2
printfn "Set.intersect [1 .. 3] [2 .. 6] yields %A" setIntersect

``` 
Output

```
Set.intersect [1 .. 3] [2 .. 6] yields set [2; 3] 
```

intersectMany
---------------
Computes the intersection of a sequence of sets. The sequence must be non-empty.

```
: seq<Set<'T>> -> Set<'T>
```

Example
```fsharp

let seqOfSets =
    seq { for i in 1 .. 9 do yield Set.ofList [ i .. i .. 10000 ] }  
let setResult = Set.intersectMany seqOfSets
printfn "Numbers between 1 and 10,000 that are divisible by "
printfn "all the numbers from 1 to 9:"
printfn "%A" setResult

``` 
Output

```
Numbers between 1 and 10,000 that are divisible by 
all the numbers from 1 to 9:
set [2520; 5040; 7560] 
```

isEmpty
------------
Returns true if the set is empty.

```
: Set<'T> ->bool
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.isEmpty : Set  -> bool (requires comparison)

// Usage:
Set.isEmpty set

isProperSubset

Evaluates to true if all elements of the first set are in the second, and at least one element of the second is not in the first.

: Set<'T> -> Set<'T> -> bool
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 6 ]
let set2 = Set.ofList [ 1 .. 5 ]
let set3 = Set.ofList [ 1 .. 6 ]
let set4 = Set.ofList [ 5 .. 10 ]
printfn "%A is a proper subset of %A: %b" set2 set1 (Set.isProperSubset set2 set1)
printfn "%A is a proper subset of %A: %b" set3 set1 (Set.isProperSubset set3 set1) 
printfn "%A is a proper subset of %A: %b" set4 set1 (Set.isProperSubset set4 set1) 

``` 
Output

```
set [1; 2; 3; 4; 5] is a proper subset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a proper subset of set [1; 2; 3; 4; 5; 6]: false
set [5; 6; 7; 8; 9; 10] is a proper subset of set [1; 2; 3; 4; 5; 6]: false 
```

isProperSuperset
---------------
Evaluates to true if all elements of the second set are in the first, and at least one element of the first is not in the second.

```
: Set<'T> -> Set<'T> -> bool
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 6 ]
let set2 = Set.ofList [ 1 .. 9 ]
let set3 = Set.ofList [ 1 .. 6 ]
let set4 = Set.ofList [ 5 .. 10 ]
printfn "%A is a proper superset of %A: %b" set2 set1 (Set.isProperSuperset set2 set1)
printfn "%A is a proper superset of %A: %b" set3 set1 (Set.isProperSuperset set3 set1) 
printfn "%A is a proper superset of %A: %b" set4 set1 (Set.isProperSuperset set4 set1) 

``` 
Output

```
set [1; 2; 3; 4; 5; 6; 7; 8; 9] is a proper superset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a proper superset of set [1; 2; 3; 4; 5; 6]: false
set [5; 6; 7; 8; 9; 10] is a proper superset of set [1; 2; 3; 4; 5; 6]: false 
```

isSubset
-----------
Evaluates to true if all elements of the first set are in the second

```
: Set<'T> -> Set<'T> -> bool
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 6 ]
let set2 = Set.ofList [ 1 .. 5 ]
let set3 = Set.ofList [ 1 .. 6 ]
let set4 = Set.ofList [ 5 .. 10 ]
printfn "%A is a subset of %A: %b" set2 set1 (Set.isSubset set2 set1)
printfn "%A is a subset of %A: %b" set3 set1 (Set.isSubset set3 set1) 
printfn "%A is a subset of %A: %b" set4 set1 (Set.isSubset set4 set1) 

``` 
Output

```
set [1; 2; 3; 4; 5] is a subset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a subset of set [1; 2; 3; 4; 5; 6]: true
set [5; 6; 7; 8; 9; 10] is a subset of set [1; 2; 3; 4; 5; 6]: false 
```

isSuperset
------------
Evaluates to true if all elements of the second set are in the first.

```
: Set<'T> -> Set<'T> -> bool
```

Example
```fsharp

let set1 = Set.ofList [ 1 .. 6 ]
let set2 = Set.ofList [ 1 .. 9 ]
let set3 = Set.ofList [ 1 .. 6 ]
let set4 = Set.ofList [ 5 .. 10 ]
printfn "%A is a superset of %A: %b" set2 set1 (Set.isSuperset set2 set1)
printfn "%A is a superset of %A: %b" set3 set1 (Set.isSuperset set3 set1) 
printfn "%A is a superset of %A: %b" set4 set1 (Set.isSuperset set4 set1) 

``` 
Output

```
set [1; 2; 3; 4; 5; 6; 7; 8; 9] is a superset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a superset of set [1; 2; 3; 4; 5; 6]: true
set [5; 6; 7; 8; 9; 10] is a superset of set [1; 2; 3; 4; 5; 6]: false 
```

iter
--------
Applies the given function to each element of the set, in order according to the comparison function.

```
: ('T -> unit) -> Set<'T> -> unit
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.iter : ('T -> unit) -> Set  -> unit (requires comparison)

// Usage:
Set.iter action set
```

map
---------
Returns a new collection containing the results of applying the given function to each element of the input set.

```
: ('T -> 'U) -> Set<'T> -> Set<'U>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.map : ('T -> 'U) -> Set  -> Set  (requires comparison and comparison)

// Usage:
Set.map mapping set
```

maxElement
-------------
Returns the highest element in the set according to the ordering being used for the set.

```
: Set<'T> -> 'T
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.maxElement : Set  -> 'T (requires comparison)

// Usage:
Set.maxElement set
```

minElement
------------
Returns the lowest element in the set according to the ordering being used for the set.

```
: Set<'T> -> 'T
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.minElement : Set  -> 'T (requires comparison)

// Usage:
Set.minElement set
```

ofArray
-------------
Creates a set that contains the same elements as the given array.

```
: 'T array -> Set<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.ofArray : 'T array -> Set  (requires comparison)

// Usage:
Set.ofArray array
```

ofList
----------
Creates a set that contains the same elements as the given list.

```
: 'T list -> Set<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.ofList : 'T list -> Set  (requires comparison)

// Usage:
Set.ofList elements
```

ofSeq
-----------
Creates a new collection from the given enumerable object.

```
: seq<'T> -> Set<'T>
```

Example
```fsharp

let data = "The quick brown fox jumps over the lazy dog"  
let set = 
    data.ToCharArray()
    |> Set.ofSeq
for c in set do 
    printf "'%c' " c 
printfn ""

``` 
Output

```
' ' 'T' 'a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j' 'k' 'l' 'm' 'n' 'o' 'p' 'q' 'r' 's' 't' 'u' 'v' 'w' 'x' 'y' 'z'  
```

partition
-----------
Splits the set into two sets containing the elements for which the given predicate returns true and false respectively.

```
: ('T -> bool) -> Set<'T> -> Set<'T> * Set<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.partition : ('T -> bool) -> Set  -> Set  * Set  (requires comparison)

// Usage:
Set.partition predicate set
```

remove
-----------
Returns a new set with the given element removed. No exception is raised if the set doesn't contain the given element.

: 'T -> Set<'T> -> Set<'T>

Example
```fsharp

``` 
Output

```
// Signature:
Set.remove : 'T -> Set  -> Set  (requires comparison)

// Usage:
Set.remove value set
```

singleton
----------
The set containing the given element.

```
: 'T -> Set<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.singleton : 'T -> Set  (requires comparison)

// Usage:
Set.singleton value
```

toArray
---------
Creates an array that contains the elements of the set in order.

: Set<'T> -> 'T array

Example
```fsharp

``` 
Output

```
// Signature:
Set.toArray : Set  -> 'T array (requires comparison)

// Usage:
Set.toArray set
```

toSeq
---------
Returns an ordered view of the collection as an enumerable object.

```
: Set<'T> -> seq<'T>
```

Example
```fsharp

``` 
Output

```
// Signature:
Set.toSeq : Set  -> seq  (requires comparison)

// Usage:
Set.toSeq set
```

union
--------
Computes the union of the two sets.

```
: Set<'T> -> Set<'T> -> Set<'T>
```

Example
```fsharp

let set1 = Set.ofList [ 2 .. 2 .. 8 ]
let set2 = Set.ofList [ 1 .. 2 .. 9 ]
let set3 = Set.union set1 set2
printfn "%A union %A yields %A" set1 set2 set3

``` 
Output

```
set [2; 4; 6; 8] union set [1; 3; 5; 7; 9] yields set [1; 2; 3; 4; 5; 6; 7; 8; 9] 
```

unionMany
------------
Computes the union of a sequence of sets.

```
: seq<Set<'T>> -> Set<'T>
```

Example
```fsharp

    let seqOfSets =
        seq { for i in 2 .. 5 do yield Set.ofList [ i .. i .. 40 ] }  
    let setResult = Set.unionMany seqOfSets
    printfn "Numbers up to 40 that are multiples of numbers from 2 to 5:"
    Set.iter (fun elem -> printf "%d " elem) setResult

``` 
Output

```
Numbers up to 40 that are multiples of numbers from 2 to 5:
2 3 4 5 6 8 9 10 12 14 15 16 18 20 21 22 24 25 26 27 28 30 32 33 34 35 36 38 39 40  
```
