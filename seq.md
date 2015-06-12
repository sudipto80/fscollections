


add
--------------
Returns a new set with an element added to the set. No exception is raised if the set already contains the given element.
```
: 'T -> Set<'T> -> Set<'T>
```
Example


Output
```

// Signature:
Set.add : 'T -> Set  -> Set  (requires comparison)

// Usage:
Set.add value set
 
```

 
contains
--------------
Evaluates to  true  if the given element is in the given set.
```
: 'T -> Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.contains : 'T -> Set  -> bool (requires comparison)

// Usage:
Set.contains element set
 
```

 
count
--------------
Returns the number of elements in the set.
```
: Set<'T> -> int
```
Example


Output
```

```

 
difference
--------------
Returns a new set with the elements of the second set removed from the first.
```
: Set<'T> -> Set<'T> -> Set<'T>
```
Example
<code>
<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 3 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 2 .. 6 ]
<span style="color:Blue;">let</span> setDiff = Set.difference set2 set1
printfn <span style="color:#A31515;">"Set.difference [2 .. 6] [1 .. 3] yields %A"</span> setDiff
</pre>
<code>
Output
```
Set.difference [2 .. 6] [1 .. 3] yields set [4; 5; 6] 
```

 
exists
--------------
Tests if any element of the collection satisfies the given predicate. If the input function is  predicate  and the elements are  i0...iN , then this function computes  predicate i0 or ... or predicate iN .
```
: ('T -> bool) -> Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.exists : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.exists predicate set
 
```

 
exists
--------------
Tests if any element of the sequence satisfies the given predicate.
```
: ('T -> bool) -> seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.exists : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.exists predicate set
 
```

 
filter
--------------
Returns a new collection containing only the elements of the collection for which the given predicate returns  true .
```
: ('T -> bool) -> Set<'T> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 10]
           |&gt; Set.filter (<span style="color:Blue;">fun</span> elem -&gt; elem % 2 = 0)
printfn <span style="color:#A31515;">"%A"</span> set1
</pre>
Output
```
set [2; 4; 6; 8; 10] 
```

 
filter
--------------
Returns a new collection containing only the elements of the collection for which the given predicate returns  true .
```
: ('T -> bool) -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 10]
           |&gt; Set.filter (<span style="color:Blue;">fun</span> elem -&gt; elem % 2 = 0)
printfn <span style="color:#A31515;">"%A"</span> set1
</pre>
Output
```
set [2; 4; 6; 8; 10] 
```

 
fold
--------------
Applies the given accumulating function to all the elements of the set
```
: ('State -> 'T -> 'State) -> 'State -> Set<'T> -> 'State
```
Example


Output
```

// Signature:
Set.fold : ('State -> 'T -> 'State) -> 'State -> Set  -> 'State (requires comparison)

// Usage:
Set.fold folder state set
 
```

 
fold
--------------
Applies a function to each element of the collection, threading an accumulator argument through the computation. If the input function is  f  and the elements are  i0...iN,  then this function computes  f (... (f s i0)...) iN .
```
: ('State -> 'T -> 'State) -> 'State -> seq<'T> -> 'State
```
Example


Output
```

// Signature:
Set.fold : ('State -> 'T -> 'State) -> 'State -> Set  -> 'State (requires comparison)

// Usage:
Set.fold folder state set
 
```

 
foldBack
--------------
Applies the given accumulating function to all the elements of the set.
```
: ('T -> 'State -> 'State) -> Set<'T> -> 'State -> 'State
```
Example


Output
```

// Signature:
Set.foldBack : ('T -> 'State -> 'State) -> Set  -> 'State -> 'State (requires comparison)

// Usage:
Set.foldBack folder set state
 
```

 
forall
--------------
Tests if all elements of the collection satisfy the given predicate. If the input function is  p  and the elements are  i0...iN,  then this function computes  p i0 &amp;&amp; ... &amp;&amp; p iN .
```
: ('T -> bool) -> Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.forall : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.forall predicate set
 
```

 
forall
--------------
Tests if all elements of the sequence satisfy the given predicate.
```
: ('T -> bool) -> seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.forall : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.forall predicate set
 
```

 
intersect
--------------
Computes the intersection of the two sets.
```
: Set<'T> -> Set<'T> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 3 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 2 .. 6 ] 
<span style="color:Blue;">let</span> setIntersect = Set.intersect set1 set2
printfn <span style="color:#A31515;">"Set.intersect [1 .. 3] [2 .. 6] yields %A"</span> setIntersect
</pre>
Output
```
Set.intersect [1 .. 3] [2 .. 6] yields set [2; 3] 
```

 
intersectMany
--------------
Computes the intersection of a sequence of sets. The sequence must be non-empty.
```
: seq<Set<'T>> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> seqOfSets =
    <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 9 <span style="color:Blue;">do</span> <span style="color:Blue;">yield</span> Set.ofList [ i .. i .. 10000 ] }  
<span style="color:Blue;">let</span> setResult = Set.intersectMany seqOfSets
printfn <span style="color:#A31515;">"Numbers between 1 and 10,000 that are divisible by "</span>
printfn <span style="color:#A31515;">"all the numbers from 1 to 9:"</span>
printfn <span style="color:#A31515;">"%A"</span> setResult
</pre>
Output
```
Numbers between 1 and 10,000 that are divisible by 
all the numbers from 1 to 9:
set [2520; 5040; 7560] 
```

 
isEmpty
--------------
Returns  true  if the set is empty.
```
: Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.isEmpty : Set  -> bool (requires comparison)

// Usage:
Set.isEmpty set
 
```

 
isEmpty
--------------
Tests whether a sequence has any elements.
```
: seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.isEmpty : Set  -> bool (requires comparison)

// Usage:
Set.isEmpty set
 
```

 
isProperSubset
--------------
Evaluates to  true  if all elements of the first set are in the second, and at least one element of the second is not in the first.
```
: Set<'T> -> Set<'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 1 .. 5 ]
<span style="color:Blue;">let</span> set3 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set4 = Set.ofList [ 5 .. 10 ]
printfn <span style="color:#A31515;">"%A is a proper subset of %A: %b"</span> set2 set1 (Set.isProperSubset set2 set1)
printfn <span style="color:#A31515;">"%A is a proper subset of %A: %b"</span> set3 set1 (Set.isProperSubset set3 set1) 
printfn <span style="color:#A31515;">"%A is a proper subset of %A: %b"</span> set4 set1 (Set.isProperSubset set4 set1) 
</pre>
Output
```
set [1; 2; 3; 4; 5] is a proper subset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a proper subset of set [1; 2; 3; 4; 5; 6]: false
set [5; 6; 7; 8; 9; 10] is a proper subset of set [1; 2; 3; 4; 5; 6]: false 
```

 
isProperSuperset
--------------
Evaluates to  true  if all elements of the second set are in the first, and at least one element of the first is not in the second.
```
: Set<'T> -> Set<'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 1 .. 9 ]
<span style="color:Blue;">let</span> set3 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set4 = Set.ofList [ 5 .. 10 ]
printfn <span style="color:#A31515;">"%A is a proper superset of %A: %b"</span> set2 set1 (Set.isProperSuperset set2 set1)
printfn <span style="color:#A31515;">"%A is a proper superset of %A: %b"</span> set3 set1 (Set.isProperSuperset set3 set1) 
printfn <span style="color:#A31515;">"%A is a proper superset of %A: %b"</span> set4 set1 (Set.isProperSuperset set4 set1) 
</pre>
Output
```
set [1; 2; 3; 4; 5; 6; 7; 8; 9] is a proper superset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a proper superset of set [1; 2; 3; 4; 5; 6]: false
set [5; 6; 7; 8; 9; 10] is a proper superset of set [1; 2; 3; 4; 5; 6]: false 
```

 
isSubset
--------------
Evaluates to  true  if all elements of the first set are in the second
```
: Set<'T> -> Set<'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 1 .. 5 ]
<span style="color:Blue;">let</span> set3 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set4 = Set.ofList [ 5 .. 10 ]
printfn <span style="color:#A31515;">"%A is a subset of %A: %b"</span> set2 set1 (Set.isSubset set2 set1)
printfn <span style="color:#A31515;">"%A is a subset of %A: %b"</span> set3 set1 (Set.isSubset set3 set1) 
printfn <span style="color:#A31515;">"%A is a subset of %A: %b"</span> set4 set1 (Set.isSubset set4 set1) 
</pre>
Output
```
set [1; 2; 3; 4; 5] is a subset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a subset of set [1; 2; 3; 4; 5; 6]: true
set [5; 6; 7; 8; 9; 10] is a subset of set [1; 2; 3; 4; 5; 6]: false 
```

 
isSuperset
--------------
Evaluates to  true  if all elements of the second set are in the first.
```
: Set<'T> -> Set<'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 1 .. 9 ]
<span style="color:Blue;">let</span> set3 = Set.ofList [ 1 .. 6 ]
<span style="color:Blue;">let</span> set4 = Set.ofList [ 5 .. 10 ]
printfn <span style="color:#A31515;">"%A is a superset of %A: %b"</span> set2 set1 (Set.isSuperset set2 set1)
printfn <span style="color:#A31515;">"%A is a superset of %A: %b"</span> set3 set1 (Set.isSuperset set3 set1) 
printfn <span style="color:#A31515;">"%A is a superset of %A: %b"</span> set4 set1 (Set.isSuperset set4 set1) 
</pre>
Output
```
set [1; 2; 3; 4; 5; 6; 7; 8; 9] is a superset of set [1; 2; 3; 4; 5; 6]: true
set [1; 2; 3; 4; 5; 6] is a superset of set [1; 2; 3; 4; 5; 6]: true
set [5; 6; 7; 8; 9; 10] is a superset of set [1; 2; 3; 4; 5; 6]: false 
```

 
iter
--------------
Applies the given function to each element of the set, in order according to the comparison function.
```
: ('T -> unit) -> Set<'T> -> unit
```
Example


Output
```

// Signature:
Set.iter : ('T -> unit) -> Set  -> unit (requires comparison)

// Usage:
Set.iter action set
 
```

 
iter
--------------
Applies the given function to each element of the collection.
```
: ('T -> unit) -> seq<'T> -> unit
```
Example


Output
```

// Signature:
Set.iter : ('T -> unit) -> Set  -> unit (requires comparison)

// Usage:
Set.iter action set
 
```

 
map
--------------
Returns a new collection containing the results of applying the given function to each element of the input set.
```
: ('T -> 'U) -> Set<'T> -> Set<'U>
```
Example


Output
```

// Signature:
Set.map : ('T -> 'U) -> Set  -> Set  (requires comparison and comparison)

// Usage:
Set.map mapping set
 
```

 
map
--------------
Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The given function will be applied as elements are demanded using the  MoveNext  method on enumerators retrieved from the object.
```
: ('T -> 'U) -> seq<'T> -> seq<'U>
```
Example


Output
```

// Signature:
Set.map : ('T -> 'U) -> Set  -> Set  (requires comparison and comparison)

// Usage:
Set.map mapping set
 
```

 
maxElement
--------------
Returns the highest element in the set according to the ordering being used for the set.
```
: Set<'T> -> 'T
```
Example


Output
```

// Signature:
Set.maxElement : Set  -> 'T (requires comparison)

// Usage:
Set.maxElement set
 
```

 
minElement
--------------
Returns the lowest element in the set according to the ordering being used for the set.
```
: Set<'T> -> 'T
```
Example


Output
```

// Signature:
Set.minElement : Set  -> 'T (requires comparison)

// Usage:
Set.minElement set
 
```

 
ofArray
--------------
Creates a set that contains the same elements as the given array.
```
: 'T array -> Set<'T>
```
Example


Output
```

// Signature:
Set.ofArray : 'T array -> Set  (requires comparison)

// Usage:
Set.ofArray array
 
```

 
ofArray
--------------
Views the given array as a sequence.
```
: 'T array -> seq<'T>
```
Example


Output
```

// Signature:
Set.ofArray : 'T array -> Set  (requires comparison)

// Usage:
Set.ofArray array
 
```

 
ofList
--------------
Creates a set that contains the same elements as the given list.
```
: 'T list -> Set<'T>
```
Example


Output
```

// Signature:
Set.ofList : 'T list -> Set  (requires comparison)

// Usage:
Set.ofList elements
 
```

 
ofList
--------------
Views the given list as a sequence.
```
: 'T list -> seq<'T>
```
Example


Output
```

// Signature:
Set.ofList : 'T list -> Set  (requires comparison)

// Usage:
Set.ofList elements
 
```

 
ofSeq
--------------
Creates a new collection from the given enumerable object.
```
: seq<'T> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> data = <span style="color:#A31515;">"The quick brown fox jumps over the lazy dog"</span>  
<span style="color:Blue;">let</span> set = 
    data.ToCharArray()
    |&gt; Set.ofSeq
<span style="color:Blue;">for</span> c <span style="color:Blue;">in</span> set <span style="color:Blue;">do</span> 
    printf <span style="color:#A31515;">"'%c' "</span> c 
printfn <span style="color:#A31515;">""</span>
</pre>
Output
```
' ' 'T' 'a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j' 'k' 'l' 'm' 'n' 'o' 'p' 'q' 'r' 's' 't' 'u' 'v' 'w' 'x' 'y' 'z'  
```

 
partition
--------------
Splits the set into two sets containing the elements for which the given predicate returns true and false respectively.
```
: ('T -> bool) -> Set<'T> -> Set<'T> * Set<'T>
```
Example


Output
```

// Signature:
Set.partition : ('T -> bool) -> Set  -> Set  * Set  (requires comparison)

// Usage:
Set.partition predicate set
 
```

 
remove
--------------
Returns a new set with the given element removed. No exception is raised if the set doesn't contain the given element.
```
: 'T -> Set<'T> -> Set<'T>
```
Example


Output
```

// Signature:
Set.remove : 'T -> Set  -> Set  (requires comparison)

// Usage:
Set.remove value set
 
```

 
singleton
--------------
The set containing the given element.
```
: 'T -> Set<'T>
```
Example


Output
```

// Signature:
Set.singleton : 'T -> Set  (requires comparison)

// Usage:
Set.singleton value
 
```

 
singleton
--------------
Returns a sequence that yields one item only.
```
: 'T -> seq<'T>
```
Example


Output
```

// Signature:
Set.singleton : 'T -> Set  (requires comparison)

// Usage:
Set.singleton value
 
```

 
toArray
--------------
Creates an array that contains the elements of the set in order.
```
: Set<'T> -> 'T array
```
Example


Output
```

// Signature:
Set.toArray : Set  -> 'T array (requires comparison)

// Usage:
Set.toArray set
 
```

 
toArray
--------------
Creates an array from the given collection.
```
: seq<'T> -> 'T []
```
Example


Output
```

// Signature:
Set.toArray : Set  -> 'T array (requires comparison)

// Usage:
Set.toArray set
 
```

 
toList
--------------
Creates a list from the given collection.
```
: seq<'T> -> 'T list
```
Example


Output
```

// Signature:
Set.toList : Set  -> 'T list (requires comparison)

// Usage:
Set.toList set
 
```

 
toSeq
--------------
Returns an ordered view of the collection as an enumerable object.
```
: Set<'T> -> seq<'T>
```
Example


Output
```

// Signature:
Set.toSeq : Set  -> seq  (requires comparison)

// Usage:
Set.toSeq set
 
```

 
union
--------------
Computes the union of the two sets.
```
: Set<'T> -> Set<'T> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 2 .. 2 .. 8 ]
<span style="color:Blue;">let</span> set2 = Set.ofList [ 1 .. 2 .. 9 ]
<span style="color:Blue;">let</span> set3 = Set.union set1 set2
printfn <span style="color:#A31515;">"%A union %A yields %A"</span> set1 set2 set3
</pre>
Output
```
set [2; 4; 6; 8] union set [1; 3; 5; 7; 9] yields set [1; 2; 3; 4; 5; 6; 7; 8; 9] 
```

 
unionMany
--------------
Computes the union of a sequence of sets.
```
: seq<Set<'T>> -> Set<'T>
```
Example

<pre>    <span style="color:Blue;">let</span> seqOfSets =
        <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 2 .. 5 <span style="color:Blue;">do</span> <span style="color:Blue;">yield</span> Set.ofList [ i .. i .. 40 ] }  
    <span style="color:Blue;">let</span> setResult = Set.unionMany seqOfSets
    printfn <span style="color:#A31515;">"Numbers up to 40 that are multiples of numbers from 2 to 5:"</span>
    Set.iter (<span style="color:Blue;">fun</span> elem -&gt; printf <span style="color:#A31515;">"%d "</span> elem) setResult
</pre>
Output
```
Numbers up to 40 that are multiples of numbers from 2 to 5:
2 3 4 5 6 8 9 10 12 14 15 16 18 20 21 22 24 25 26 27 28 30 32 33 34 35 36 38 39 40  
```

 
append
--------------
Wraps the two given enumerations as a single concatenated enumeration.
```
: seq<'T> -> seq<'T> -> seq<'T>
```
Example

<pre>printfn <span style="color:#A31515;">"%A"</span> (Seq.append [| 1; 2; 3|] [ 4; 5; 6])
</pre>
Output
```
seq [1; 2; 3; 4; ...] 
```

 
average
--------------
Returns the average of the elements in the sequence.
```
: seq<^T> -> ^T
```
Example

<pre><span style="color:Green;">// You can use Seq.average to average elements of a list, array, or sequence. </span>
<span style="color:Blue;">let</span> average1 = Seq.average [ 1.0 .. 10.0 ]
printfn <span style="color:#A31515;">"Average: %f"</span> average1
<span style="color:Green;">// To average a sequence of integers, use Seq.averageBy to convert to float. </span>
<span style="color:Blue;">let</span> average2 = Seq.averageBy (<span style="color:Blue;">fun</span> elem -&gt; <span style="color:Blue;">float</span> elem) (<span style="color:Blue;">seq</span> { 1 .. 10 })
printfn <span style="color:#A31515;">"Average: %f"</span> average2
</pre>
Output
```
Average: 5.500000
Average: 5.500000 
```

 
averageBy
--------------
Returns the average of the results generated by applying the function to each element of the sequence.
```
: ('T -> ^U) -> seq<'T> -> ^U
```
Example

<pre><span style="color:Green;">// You can use Seq.average to average elements of a list, array, or sequence. </span>
<span style="color:Blue;">let</span> average1 = Seq.average [ 1.0 .. 10.0 ]
printfn <span style="color:#A31515;">"Average: %f"</span> average1
<span style="color:Green;">// To average a sequence of integers, use Seq.averageBy to convert to float. </span>
<span style="color:Blue;">let</span> average2 = Seq.averageBy (<span style="color:Blue;">fun</span> elem -&gt; <span style="color:Blue;">float</span> elem) (<span style="color:Blue;">seq</span> { 1 .. 10 })
printfn <span style="color:#A31515;">"Average: %f"</span> average2
</pre>
Output
```
Average: 5.500000
Average: 5.500000 
```

 
cache
--------------
Returns a sequence that corresponds to a cached version of the input sequence.
```
: seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Green;">// Recursive isprime function. </span>
<span style="color:Blue;">let</span> isPrime n =
    <span style="color:Blue;">let</span> <span style="color:Blue;">rec</span> check i =
        i &gt; n/2 || (n % i &lt;&gt; 0 &amp;&amp; check (i + 1))
    check 2

<span style="color:Blue;">let</span> seqPrimes = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> n <span style="color:Blue;">in</span> 2 .. 10000 <span style="color:Blue;">do</span> <span style="color:Blue;">if</span> isPrime n <span style="color:Blue;">then</span> <span style="color:Blue;">yield</span> n }
<span style="color:Green;">// Cache the sequence to avoid recomputing the sequence elements. </span>
<span style="color:Blue;">let</span> cachedSeq = Seq.cache seqPrimes
<span style="color:Blue;">for</span> index <span style="color:Blue;">in</span> 1..5 <span style="color:Blue;">do</span>
    printfn <span style="color:#A31515;">"%d is prime."</span> (Seq.nth (Seq.length cachedSeq - index) cachedSeq)
</pre>
Output
```
9973 is prime.
9967 is prime.
9949 is prime.
9941 is prime.
9931 is prime. 
```

 
cast
--------------
Wraps a loosely-typed  System.Collections  sequence as a typed sequence.
```
: IEnumerable -> seq<'T>
```
Example

<pre><span style="color:Blue;">open</span> System
<span style="color:Blue;">let</span> <span style="color:Blue;">mutable</span> arrayList1 = <span style="color:Blue;">new</span> System.Collections.ArrayList(10)
<span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 <span style="color:Blue;">do</span> arrayList1.Add(10) |&gt; ignore
<span style="color:Blue;">let</span> seqCast : <span style="color:Blue;">seq</span>&lt;<span style="color:Blue;">int</span>&gt; = Seq.cast arrayList1
</pre>
Output
```

 open  System
 let   mutable  arrayList1 =  new  System.Collections.ArrayList(10)
 for  i  in  1 .. 10  do  arrayList1.Add(10) |> ignore
 let  seqCast :  seq int > = Seq.cast arrayList1
 
```

 
choose
--------------
Applies the given function to each element of the list. Return the list comprised of the results for each element where the function returns  Some .
```
: ('T -> 'U option) -> seq<'T> -> seq<'U>
```
Example

<pre><span style="color:Blue;">let</span> numbers = <span style="color:Blue;">seq</span> {1..20}
<span style="color:Blue;">let</span> evens = Seq.choose(<span style="color:Blue;">fun</span> x -&gt; 
                            <span style="color:Blue;">match</span> x <span style="color:Blue;">with</span>
                            | x <span style="color:Blue;">when</span> x%2=0 -&gt; Some(x)
                            | _ -&gt; None ) numbers
printfn <span style="color:#A31515;">"numbers = %A\n"</span> numbers
printfn <span style="color:#A31515;">"evens = %A"</span> evens
</pre>
Output
```
numbers = seq [1; 2; 3; 4; ...]

evens = seq [2; 4; 6; 8; ...] 
```

 
collect
--------------
Applies the given function to each element of the sequence and concatenates all the results.
```
: ('T -> 'Collection) -> seq<'T> -> seq<'U>
```
Example


Output
```

```

 
compareWith
--------------
Compares two sequences using the given comparison function, element by element.
```
: ('T -> 'T -> int) -> seq<'T> -> seq<'T> -> int
```
Example

<pre><span style="color:Blue;">let</span> sequence1 = <span style="color:Blue;">seq</span> { 1 .. 10 }
<span style="color:Blue;">let</span> sequence2 = <span style="color:Blue;">seq</span> { 10 .. -1 .. 1 }

<span style="color:Green;">// Compare two sequences element by element. </span>
<span style="color:Blue;">let</span> compareSequences = Seq.compareWith (<span style="color:Blue;">fun</span> elem1 elem2 -&gt;
    <span style="color:Blue;">if</span> elem1 &gt; elem2 <span style="color:Blue;">then</span> 1
    <span style="color:Blue;">elif</span> elem1 &lt; elem2 <span style="color:Blue;">then</span> -1
    <span style="color:Blue;">else</span> 0) 

<span style="color:Blue;">let</span> compareResult1 = compareSequences sequence1 sequence2
<span style="color:Blue;">match</span> compareResult1 <span style="color:Blue;">with</span>
| 1 -&gt; printfn <span style="color:#A31515;">"Sequence1 is greater than sequence2."</span>
| -1 -&gt; printfn <span style="color:#A31515;">"Sequence1 is less than sequence2."</span>
| 0 -&gt; printfn <span style="color:#A31515;">"Sequence1 is equal to sequence2."</span>
| _ -&gt; failwith(<span style="color:#A31515;">"Invalid comparison result."</span>)
</pre>
Output
```
Sequence1 is less than sequence2. 
```

 
concat
--------------
Combines the given enumeration-of-enumerations as a single concatenated enumeration.
```
: seq<'Collection> -> seq<'T>
```
Example

<pre><span style="color:Green;">// Using Seq.append to append an array to a list. </span>
<span style="color:Blue;">let</span> seq1to10 = Seq.append [1; 2; 3] [| 4; 5; 6; 7; 8; 9; 10 |]
<span style="color:Green;">// Using Seq.concat to concatenate a list of arrays. </span>
<span style="color:Blue;">let</span> seqResult = Seq.concat [ [| 1; 2; 3 |]; [| 4; 5; 6 |]; [|7; 8; 9|] ]
Seq.iter (<span style="color:Blue;">fun</span> elem -&gt; printf <span style="color:#A31515;">"%d "</span> elem) seq1to10
printfn <span style="color:#A31515;">""</span>
Seq.iter (<span style="color:Blue;">fun</span> elem -&gt; printf <span style="color:#A31515;">"%d "</span> elem) seqResult
</pre>
Output
```
1 2 3 4 5 6 7 8 9 10 
1 2 3 4 5 6 7 8 9  
```

 
countBy
--------------
Applies a key-generating function to each element of a sequence and return a sequence yielding unique keys and their number of occurrences in the original sequence.
```
: ('T -> 'Key) -> seq<'T> -> seq<'Key * int>
```
Example

<pre><span style="color:Blue;">let</span> mySeq1 = <span style="color:Blue;">seq</span> { 1.. 100 }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> seqResult = Seq.countBy (<span style="color:Blue;">fun</span> elem -&gt;
    <span style="color:Blue;">if</span> (elem % 2 = 0) <span style="color:Blue;">then</span> 0 <span style="color:Blue;">else</span> 1) mySeq1

printSeq seqResult
</pre>
Output
```
(1, 50) (0, 50) 
  
```

 
delay
--------------
Returns a sequence that is built from the given delayed specification of a sequence.
```
: (unit -> seq<'T>) -> seq<'T>
```
Example

<pre><span style="color:Green;">// Normally sequences are evaluated lazily.  In this case, </span>
<span style="color:Green;">// the sequence is created from a list, which is not evaluated </span>
<span style="color:Green;">// lazily. Therefore, without Seq.delay, the elements would be </span>
<span style="color:Green;">// evaluated at the time of the call to makeSequence. </span>
<span style="color:Blue;">let</span> makeSequence function1 maxNumber = Seq.delay (<span style="color:Blue;">fun</span> () -&gt;
    <span style="color:Blue;">let</span> <span style="color:Blue;">rec</span> loop n acc =
        printfn <span style="color:#A31515;">"Evaluating %d."</span> n
        <span style="color:Blue;">match</span> n <span style="color:Blue;">with</span>
        | 0 -&gt; acc
        | n -&gt; (function1 n) :: loop (n - 1) acc
    loop maxNumber []
    |&gt; Seq.ofList)
printfn <span style="color:#A31515;">"Calling makeSequence."</span> 
<span style="color:Blue;">let</span> seqSquares = makeSequence (<span style="color:Blue;">fun</span> x -&gt; x * x) 4          
<span style="color:Blue;">let</span> seqCubes = makeSequence (<span style="color:Blue;">fun</span> x -&gt; x * x * x) 4
printfn <span style="color:#A31515;">"Printing sequences."</span>
printfn <span style="color:#A31515;">"Squares:"</span>
seqSquares |&gt; Seq.iter (<span style="color:Blue;">fun</span> x -&gt; printf <span style="color:#A31515;">"%d "</span> x)
printfn <span style="color:#A31515;">"\nCubes:"</span>
seqCubes |&gt; Seq.iter (<span style="color:Blue;">fun</span> x -&gt; printf <span style="color:#A31515;">"%d "</span> x)                       
</pre>
Output
```
Calling makeSequence.
Evaluating 4.
Evaluating 3.
Evaluating 2.
Evaluating 1.
Evaluating 0.
Evaluating 4.
Evaluating 3.
Evaluating 2.
Evaluating 1.
Evaluating 0.
Printing sequences.
Squares:
16 9 4 1 
Cubes:
64 27 8 1  
```

 
distinct
--------------
Returns a sequence that contains no duplicate entries according to generic hash and equality comparisons on the entries. If an element occurs multiple times in the sequence then the later occurrences are discarded.
```
: seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> binary n =
    <span style="color:Blue;">let</span> <span style="color:Blue;">rec</span> generateBinary n =
        <span style="color:Blue;">if</span> (n / 2 = 0) <span style="color:Blue;">then</span> [n]
        <span style="color:Blue;">else</span> (n % 2) :: generateBinary (n / 2)
    generateBinary n |&gt; List.rev |&gt; Seq.ofList

printfn <span style="color:#A31515;">"%A"</span> (binary 1024)

<span style="color:Blue;">let</span> resultSequence = Seq.distinct (binary 1024)
printfn <span style="color:#A31515;">"%A"</span> resultSequence
</pre>
Output
```
[1; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0]
seq [1; 0] 
```

 
distinctBy
--------------
Returns a sequence that contains no duplicate entries according to the generic hash and equality comparisons on the keys returned by the given key-generating function. If an element occurs multiple times in the sequence then the later occurrences are discarded.
```
: ('T -> 'Key) -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> inputSequence = { -5 .. 10 }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span>
printfn <span style="color:#A31515;">"Original sequence: "</span>
printSeq inputSequence
printfn <span style="color:#A31515;">"\nSequence with distinct absolute values: "</span> 
<span style="color:Blue;">let</span> seqDistinctAbsoluteValue = Seq.distinctBy (<span style="color:Blue;">fun</span> elem -&gt; abs elem) inputSequence
seqDistinctAbsoluteValue |&gt; printSeq
</pre>
Output
```
Original sequence: 
-5 -4 -3 -2 -1 0 1 2 3 4 5 6 7 8 9 10 

Sequence with distinct absolute values: 
-5 -4 -3 -2 -1 0 6 7 8 9 10  
```

 
exactlyOne
--------------
Returns the only element of the sequence.
```
: seq<'T> -> 'T
```
Example


Output
```

// Signature:
exactlyOne : seq  -> 'T
// Usage:
Seq.exactlyOne source
 
```

 
exists
--------------
Tests if any element of the collection satisfies the given predicate. If the input function is  predicate  and the elements are  i0...iN , then this function computes  predicate i0 or ... or predicate iN .
```
: ('T -> bool) -> Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.exists : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.exists predicate set
 
```

 
exists
--------------
Tests if any element of the sequence satisfies the given predicate.
```
: ('T -> bool) -> seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.exists : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.exists predicate set
 
```

 
exists2
--------------
Tests if any pair of corresponding elements of the input sequences satisfies the given predicate.
```
: ('T1 -> 'T2 -> bool) -> seq<'T1> -> seq<'T2> -> bool
```
Example

<pre><span style="color:Green;">// Use Seq.exists2 to compare elements in two sequences. </span>
<span style="color:Green;">// isEqualElement returns true if any elements at the same position in two supplied </span>
<span style="color:Green;">// sequences match. </span>
<span style="color:Blue;">let</span> isEqualElement seq1 seq2 = Seq.exists2 (<span style="color:Blue;">fun</span> elem1 elem2 -&gt; elem1 = elem2) seq1 seq2
<span style="color:Blue;">let</span> seq1to5 = <span style="color:Blue;">seq</span> { 1 .. 5 }
<span style="color:Blue;">let</span> seq5to1 = <span style="color:Blue;">seq</span> { 5 .. -1 .. 1 }
<span style="color:Blue;">if</span> (isEqualElement seq1to5 seq5to1) <span style="color:Blue;">then</span>
    printfn <span style="color:#A31515;">"Sequences %A and %A have at least one equal element at the same position."</span> seq1to5 seq5to1
<span style="color:Blue;">else</span>
    printfn <span style="color:#A31515;">"Sequences %A and %A do not have any equal elements that are at the same position."</span> seq1to5 seq5to1
</pre>
Output
```
Sequences seq [1; 2; 3; 4; ...] and seq [5; 4; 3; 2; ...] have at least one equal element at the same position. 
```

 
filter
--------------
Returns a new collection containing only the elements of the collection for which the given predicate returns  true .
```
: ('T -> bool) -> Set<'T> -> Set<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 10]
           |&gt; Set.filter (<span style="color:Blue;">fun</span> elem -&gt; elem % 2 = 0)
printfn <span style="color:#A31515;">"%A"</span> set1
</pre>
Output
```
set [2; 4; 6; 8; 10] 
```

 
filter
--------------
Returns a new collection containing only the elements of the collection for which the given predicate returns  true .
```
: ('T -> bool) -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> set1 = Set.ofList [ 1 .. 10]
           |&gt; Set.filter (<span style="color:Blue;">fun</span> elem -&gt; elem % 2 = 0)
printfn <span style="color:#A31515;">"%A"</span> set1
</pre>
Output
```
set [2; 4; 6; 8; 10] 
```

 
find
--------------
Returns the first element for which the given function returns  true .
```
: ('T -> bool) -> seq<'T> -> 'T
```
Example


Output
```

```

 
findIndex
--------------
Returns the index of the first element for which the given function returns  true .
```
: ('T -> bool) -> seq<'T> -> int
```
Example

<pre><span style="color:Blue;">let</span> seqA = [| 2 .. 100 |]
<span style="color:Blue;">let</span> delta = 1.0e-10
<span style="color:Blue;">let</span> isPerfectSquare (x:<span style="color:Blue;">int</span>) =
    <span style="color:Blue;">let</span> y = sqrt (<span style="color:Blue;">float</span> x)
    abs(y - round y) &lt; delta
<span style="color:Blue;">let</span> isPerfectCube (x:<span style="color:Blue;">int</span>) =
    <span style="color:Blue;">let</span> y = System.Math.Pow(<span style="color:Blue;">float</span> x, 1.0/3.0)
    abs(y - round y) &lt; delta
<span style="color:Blue;">let</span> element = Seq.find (<span style="color:Blue;">fun</span> elem -&gt; isPerfectSquare elem &amp;&amp; isPerfectCube elem) seqA
<span style="color:Blue;">let</span> index = Seq.findIndex (<span style="color:Blue;">fun</span> elem -&gt; isPerfectSquare elem &amp;&amp; isPerfectCube elem) seqA
printfn <span style="color:#A31515;">"The first element that is both a square and a cube is %d and its index is %d."</span> element index
</pre>
Output
```
The first element that is both a square and a cube is 64 and its index is 62. 
```

 
fold
--------------
Applies the given accumulating function to all the elements of the set
```
: ('State -> 'T -> 'State) -> 'State -> Set<'T> -> 'State
```
Example


Output
```

// Signature:
Set.fold : ('State -> 'T -> 'State) -> 'State -> Set  -> 'State (requires comparison)

// Usage:
Set.fold folder state set
 
```

 
fold
--------------
Applies a function to each element of the collection, threading an accumulator argument through the computation. If the input function is  f  and the elements are  i0...iN,  then this function computes  f (... (f s i0)...) iN .
```
: ('State -> 'T -> 'State) -> 'State -> seq<'T> -> 'State
```
Example


Output
```

// Signature:
Set.fold : ('State -> 'T -> 'State) -> 'State -> Set  -> 'State (requires comparison)

// Usage:
Set.fold folder state set
 
```

 
forall
--------------
Tests if all elements of the collection satisfy the given predicate. If the input function is  p  and the elements are  i0...iN,  then this function computes  p i0 &amp;&amp; ... &amp;&amp; p iN .
```
: ('T -> bool) -> Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.forall : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.forall predicate set
 
```

 
forall
--------------
Tests if all elements of the sequence satisfy the given predicate.
```
: ('T -> bool) -> seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.forall : ('T -> bool) -> Set  -> bool (requires comparison)

// Usage:
Set.forall predicate set
 
```

 
forall2
--------------
Tests the all pairs of elements drawn from the two sequences satisfy the given predicate. If one sequence is shorter than the other then the remaining elements of the longer sequence are ignored.
```
: ('T1 -> 'T2 -> bool) -> seq<'T1> -> seq<'T2> -> bool
```
Example

<pre><span style="color:Green;">// This function can be used on any sequence, so the same function </span>
<span style="color:Green;">// works with both lists and arrays. </span>
<span style="color:Blue;">let</span> allEqual coll = Seq.forall2 (<span style="color:Blue;">fun</span> elem1 elem2 -&gt; elem1 = elem2) coll
printfn <span style="color:#A31515;">"%A"</span> (allEqual [| 1; 2 |] [| 1; 2 |])
printfn <span style="color:#A31515;">"%A"</span> (allEqual [ 1; 2 ] [ 2; 1 ])
</pre>
Output
```
true
false 
```

 
groupBy
--------------
Applies a key-generating function to each element of a sequence and yields a sequence of unique keys. Each unique key has also contains a sequence of all elements that match to this key.
```
: ('T -> 'Key) -> seq<'T> -> seq<'Key * seq<'T>>
```
Example

<pre><span style="color:Blue;">let</span> sequence = <span style="color:Blue;">seq</span> { 1 .. 100 }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> sequences3 = Seq.groupBy (<span style="color:Blue;">fun</span> index -&gt;
    <span style="color:Blue;">if</span> (index % 2 = 0) <span style="color:Blue;">then</span> 0 <span style="color:Blue;">else</span> 1) sequence
sequences3 |&gt; printSeq
</pre>
Output
```
(1, seq [1; 3; 5; 7; ...]) (0, seq [2; 4; 6; 8; ...])  
```

 
head
--------------
Returns the first element of the sequence.
```
: seq<'T> -> 'T
```
Example


Output
```

```

 
init
--------------
Generates a new sequence which, when iterated, returns successive elements by calling the given function, up to the given count. The results of calling the function are not saved, that is, the function is reapplied as necessary to regenerate the elements. The function is passed the index of the item being generated.
```
: int -> (int -> 'T) -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> seqFirst5MultiplesOf10 = Seq.init 5 (<span style="color:Blue;">fun</span> n -&gt; n * 10)
Seq.iter (<span style="color:Blue;">fun</span> elem -&gt; printf <span style="color:#A31515;">"%d "</span> elem) seqFirst5MultiplesOf10
</pre>
Output
```
0 10 20 30 40 
```

 
initInfinite
--------------
Generates a new sequence which, when iterated, will return successive elements by calling the given function. The results of calling the function are not saved, that is, the function will be reapplied as necessary to regenerate the elements. The function is passed the index of the item being generated.
```
: (int -> 'T) -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> seqInfinite = Seq.initInfinite (<span style="color:Blue;">fun</span> index -&gt;
    <span style="color:Blue;">let</span> n = <span style="color:Blue;">float</span>( index + 1 )
    1.0 / (n * n * (<span style="color:Blue;">if</span> ((index + 1) % 2 = 0) <span style="color:Blue;">then</span> 1.0 <span style="color:Blue;">else</span> -1.0)))
printfn <span style="color:#A31515;">"%A"</span> seqInfinite
</pre>
Output
```
seq [-1.0; 0.25; -0.1111111111; 0.0625; ...] 
```

 
isEmpty
--------------
Returns  true  if the set is empty.
```
: Set<'T> -> bool
```
Example


Output
```

// Signature:
Set.isEmpty : Set  -> bool (requires comparison)

// Usage:
Set.isEmpty set
 
```

 
isEmpty
--------------
Tests whether a sequence has any elements.
```
: seq<'T> -> bool
```
Example


Output
```

// Signature:
Set.isEmpty : Set  -> bool (requires comparison)

// Usage:
Set.isEmpty set
 
```

 
iter
--------------
Applies the given function to each element of the set, in order according to the comparison function.
```
: ('T -> unit) -> Set<'T> -> unit
```
Example


Output
```

// Signature:
Set.iter : ('T -> unit) -> Set  -> unit (requires comparison)

// Usage:
Set.iter action set
 
```

 
iter
--------------
Applies the given function to each element of the collection.
```
: ('T -> unit) -> seq<'T> -> unit
```
Example


Output
```

// Signature:
Set.iter : ('T -> unit) -> Set  -> unit (requires comparison)

// Usage:
Set.iter action set
 
```

 
iteri
--------------
Applies the given function to each element of the collection. The integer passed to the function indicates the index of element.
```
: (int -> 'T -> unit) -> seq<'T> -> unit
```
Example

<pre><span style="color:Blue;">let</span> seq1 = [1; 2; 3]
<span style="color:Blue;">let</span> seq2 = [4; 5; 6]
Seq.iter (<span style="color:Blue;">fun</span> x -&gt; printfn <span style="color:#A31515;">"Seq.iter: element is %d"</span> x) seq1
Seq.iteri(<span style="color:Blue;">fun</span> i x -&gt; printfn <span style="color:#A31515;">"Seq.iteri: element %d is %d"</span> i x) seq1
Seq.iter2 (<span style="color:Blue;">fun</span> x y -&gt; printfn <span style="color:#A31515;">"Seq.iter2: elements are %d %d"</span> x y) seq1 seq2
</pre>
Output
```
Seq.iter: element is 1
Seq.iter: element is 2
Seq.iter: element is 3
Seq.iteri: element 0 is 1
Seq.iteri: element 1 is 2
Seq.iteri: element 2 is 3
Seq.iter2: elements are 1 4
Seq.iter2: elements are 2 5
Seq.iter2: elements are 3 6 
```

 
iter2
--------------
Applies the given function to two collections simultaneously. If one sequence is shorter than the other then the remaining elements of the longer sequence are ignored.
```
: ('T1 -> 'T2 -> unit) -> seq<'T1> -> seq<'T2> -> unit
```
Example

<pre><span style="color:Blue;">let</span> seq1 = [1; 2; 3]
<span style="color:Blue;">let</span> seq2 = [4; 5; 6]
Seq.iter (<span style="color:Blue;">fun</span> x -&gt; printfn <span style="color:#A31515;">"Seq.iter: element is %d"</span> x) seq1
Seq.iteri(<span style="color:Blue;">fun</span> i x -&gt; printfn <span style="color:#A31515;">"Seq.iteri: element %d is %d"</span> i x) seq1
Seq.iter2 (<span style="color:Blue;">fun</span> x y -&gt; printfn <span style="color:#A31515;">"Seq.iter2: elements are %d %d"</span> x y) seq1 seq2
</pre>
Output
```
Seq.iter: element is 1
Seq.iter: element is 2
Seq.iter: element is 3
Seq.iteri: element 0 is 1
Seq.iteri: element 1 is 2
Seq.iteri: element 2 is 3
Seq.iter2: elements are 1 4
Seq.iter2: elements are 2 5
Seq.iter2: elements are 3 6 
```

 
last
--------------
Returns the last element of the sequence.
```
: seq<'T> -> 'T
```
Example


Output
```

// Signature:
last : seq  -> 'T
// Usage:
Seq.last source
 
```

 
length
--------------
Returns the length of the sequence.
```
: seq<'T> -> int
```
Example


Output
```

```

 
map
--------------
Returns a new collection containing the results of applying the given function to each element of the input set.
```
: ('T -> 'U) -> Set<'T> -> Set<'U>
```
Example


Output
```

// Signature:
Set.map : ('T -> 'U) -> Set  -> Set  (requires comparison and comparison)

// Usage:
Set.map mapping set
 
```

 
map
--------------
Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The given function will be applied as elements are demanded using the  MoveNext  method on enumerators retrieved from the object.
```
: ('T -> 'U) -> seq<'T> -> seq<'U>
```
Example


Output
```

// Signature:
Set.map : ('T -> 'U) -> Set  -> Set  (requires comparison and comparison)

// Usage:
Set.map mapping set
 
```

 
mapi
--------------
Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The integer index passed to the function indicates the index (from 0) of element being transformed.
```
: (int -> 'T -> 'U) -> seq<'T> -> seq<'U>
```
Example


Output
```

// Signature:
Seq.mapi : (int -> 'T -> 'U) -> seq  -> seq 

// Usage:
Seq.mapi mapping source
 
```

 
map2
--------------
Creates a new collection whose elements are the results of applying the given function to the corresponding pairs of elements from the two sequences. If one input sequence is shorter than the other then the remaining elements of the longer sequence are ignored.
```
: ('T1 -> 'T2 -> 'U) -> seq<'T1> -> seq<'T2> -> seq<'U>
```
Example


Output
```

// Signature:
Seq.map2 : ('T1 -> 'T2 -> 'U) -> seq  -> seq  -> seq 

// Usage:
Seq.map2 mapping source1 source2
 
```

 
max
--------------
Returns the greatest of all elements of the sequence, compared by using  Operators.max .
```
: seq<'T> -> 'T
```
Example


Output
```

```

 
maxBy
--------------
Returns the greatest of all elements of the sequence, compared by using  Operators.max  on the function result.
```
: ('T -> 'U) -> seq<'T> -> 'T
```
Example


Output
```

// Signature:
Seq.maxBy : ('T -> 'U) -> seq  -> 'T (requires comparison)

// Usage:
Seq.maxBy projection source
 
```

 
min
--------------
Returns the lowest of all elements of the sequence, compared by using  Operators.min .
```
: seq<'T> -> 'T
```
Example


Output
```

module Set
 
```

 
minBy
--------------
Returns the lowest of all elements of the sequence, compared by using  Operators.min  on the function result.
```
: ('T -> 'U) -> seq<'T> -> 'T
```
Example


Output
```

// Signature:
Seq.minBy : ('T -> 'U) -> seq  -> 'T (requires comparison)

// Usage:
Seq.minBy projection source
 
```

 
nth
--------------
Computes the  nth  element in the collection.
```
: int -> seq<'T> -> 'T
```
Example


Output
```

// Signature:
Seq.nth : int -> seq  -> 'T

// Usage:
Seq.nth index source
 
```

 
ofArray
--------------
Creates a set that contains the same elements as the given array.
```
: 'T array -> Set<'T>
```
Example


Output
```

// Signature:
Set.ofArray : 'T array -> Set  (requires comparison)

// Usage:
Set.ofArray array
 
```

 
ofArray
--------------
Views the given array as a sequence.
```
: 'T array -> seq<'T>
```
Example


Output
```

// Signature:
Set.ofArray : 'T array -> Set  (requires comparison)

// Usage:
Set.ofArray array
 
```

 
ofList
--------------
Creates a set that contains the same elements as the given list.
```
: 'T list -> Set<'T>
```
Example


Output
```

// Signature:
Set.ofList : 'T list -> Set  (requires comparison)

// Usage:
Set.ofList elements
 
```

 
ofList
--------------
Views the given list as a sequence.
```
: 'T list -> seq<'T>
```
Example


Output
```

// Signature:
Set.ofList : 'T list -> Set  (requires comparison)

// Usage:
Set.ofList elements
 
```

 
pairwise
--------------
Returns a sequence of each element in the input sequence and its predecessor, with the exception of the first element which is only returned as the predecessor of the second element.
```
: seq<'T> -> seq<'T * 'T>
```
Example

<pre><span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> seqPairwise = Seq.pairwise (<span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i })
printSeq seqPairwise

printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> seqDelta = Seq.map (<span style="color:Blue;">fun</span> elem -&gt; snd elem - fst elem) seqPairwise
printSeq seqDelta
</pre>
Output
```
(1, 4) (4, 9) (9, 16) (16, 25) (25, 36) (36, 49) (49, 64) (64, 81) (81, 100) 

3 5 7 9 11 13 15 17 19 
```

 
pick
--------------
Applies the given function to successive elements, returning the first value where the function returns a  Some  value.
```
: ('T -> 'U option) -> seq<'T> -> 'U
```
Example


Output
```

// Signature:
Seq.pick : ('T -> 'U option) -> seq  -> 'U

// Usage:
Seq.pick chooser source
 
```

 
readonly
--------------
Creates a new sequence object that delegates to the given sequence object. This ensures the original sequence cannot be rediscovered and mutated by a type cast. For example, if given an array the returned sequence will return the elements of the array, but you cannot cast the returned sequence object to an array.
```
: seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">type</span> ArrayContainer(start, finish) =
    <span style="color:Blue;">let</span> internalArray = [| start .. finish |]
    <span style="color:Blue;">member</span> this.RangeSeq = Seq.readonly internalArray
    <span style="color:Blue;">member</span> this.RangeArray = internalArray

<span style="color:Blue;">let</span> newArray = <span style="color:Blue;">new</span> ArrayContainer(1, 10)
<span style="color:Blue;">let</span> rangeSeq = newArray.RangeSeq
<span style="color:Blue;">let</span> rangeArray = newArray.RangeArray
<span style="color:Green;">// These lines produce an error:  </span>
<span style="color:Green;">//let myArray = rangeSeq :&gt; int array </span>
<span style="color:Green;">//myArray.[0] &lt;- 0 </span>
<span style="color:Green;">// The following line does not produce an error.  </span>
<span style="color:Green;">// It does not preserve encapsulation.</span>
rangeArray.[0] &lt;- 0
</pre>
Output
```

```

 
reduce
--------------
Applies a function to each element of the sequence, threading an accumulator argument through the computation. Begin by applying the function to the first two elements. Then feed this result into the function along with the third element and so on. Return the final result.
```
: ('T -> 'T -> 'T) -> seq<'T> -> 'T
```
Example


Output
```

// Signature:
Seq.reduce : ('T -> 'T -> 'T) -> seq  -> 'T

// Usage:
Seq.reduce reduction source
 
```

 
scan
--------------
Like  Seq.fold , but computes on-demand and returns the sequence of intermediary and final results.
```
: ('State -> 'T -> 'State) -> 'State -> seq<'T> -> seq<'State>
```
Example


Output
```

// Signature:
Seq.scan : ('State -> 'T -> 'State) -> 'State -> seq  -> seq 

// Usage:
Seq.scan folder state source
 
```

 
singleton
--------------
The set containing the given element.
```
: 'T -> Set<'T>
```
Example


Output
```

// Signature:
Set.singleton : 'T -> Set  (requires comparison)

// Usage:
Set.singleton value
 
```

 
singleton
--------------
Returns a sequence that yields one item only.
```
: 'T -> seq<'T>
```
Example


Output
```

// Signature:
Set.singleton : 'T -> Set  (requires comparison)

// Usage:
Set.singleton value
 
```

 
skip
--------------
Returns a sequence that skips a specified number of elements of the underlying sequence and then yields the remaining elements of the sequence.
```
: int -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> mySeq = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> mySeqSkipFirst5 = Seq.skip 5 mySeq
mySeqSkipFirst5 |&gt; printSeq
</pre>
Output
```
36 49 64 81 100  
```

 
skipWhile
--------------
Returns a sequence that, when iterated, skips elements of the underlying sequence while the given predicate returns  true , and then yields the remaining elements of the sequence.
```
: ('T -> bool) -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> mySeq = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> mySeqSkipWhileLessThan10 = Seq.skipWhile (<span style="color:Blue;">fun</span> elem -&gt; elem &lt; 10) mySeq
mySeqSkipWhileLessThan10 |&gt; printSeq
</pre>
Output
```
16 25 36 49 64 81 100  
```

 
sort
--------------
Yields a sequence ordered by keys.
```
: seq<'T> -> seq<'T>
```
Example


Output
```

```

 
sum
--------------
Returns the sum of the elements in the sequence.
```
: seq<^T> -> ^T
```
Example


Output
```

// Signature:
Seq.sum : seq  -> ^T (requires ^T with static member (+) and ^T with static member Zero)

// Usage:
Seq.sum source
 
```

 
sumBy
--------------
take
```
Returns the sum of the results generated by applying the function to each element of the sequence.
```
Example


Output
```

// Signature:
Seq.sumBy : ('T -> ^U) -> seq  -> ^U (requires ^U with static member (+) and ^U with static member Zero)

// Usage:
Seq.sumBy projection source
 
```

 
take
--------------
Returns the first elements of the sequence up to a specified count.
```
: int -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> mySeq = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i }
<span style="color:Blue;">let</span> truncatedSeq = Seq.truncate 5 mySeq
<span style="color:Blue;">let</span> takenSeq = Seq.take 5 mySeq

<span style="color:Blue;">let</span> truncatedSeq2 = Seq.truncate 20 mySeq
<span style="color:Blue;">let</span> takenSeq2 = Seq.take 20 mySeq

<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 

<span style="color:Green;">// Up to this point, the sequences are not evaluated. </span>
<span style="color:Green;">// The following code causes the sequences to be evaluated.</span>
truncatedSeq |&gt; printSeq
truncatedSeq2 |&gt; printSeq
takenSeq |&gt; printSeq
<span style="color:Green;">// The following line produces a run-time error (in printSeq):</span>
takenSeq2 |&gt; printSeq
</pre>
Output
```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
```

 
takeWhile
--------------
Returns a sequence that, when iterated, yields elements of the underlying sequence while the given predicate returns  true , and then returns no further elements.
```
: ('T -> bool) -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> mySeq = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i }
<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 
<span style="color:Blue;">let</span> mySeqLessThan10 = Seq.takeWhile (<span style="color:Blue;">fun</span> elem -&gt; elem &lt; 10) mySeq
mySeqLessThan10 |&gt; printSeq
</pre>
Output
```
1 4 9 
```

 
toArray
--------------
Creates an array that contains the elements of the set in order.
```
: Set<'T> -> 'T array
```
Example


Output
```

// Signature:
Set.toArray : Set  -> 'T array (requires comparison)

// Usage:
Set.toArray set
 
```

 
toArray
--------------
Creates an array from the given collection.
```
: seq<'T> -> 'T []
```
Example


Output
```

// Signature:
Set.toArray : Set  -> 'T array (requires comparison)

// Usage:
Set.toArray set
 
```

 
toList
--------------
Creates a list from the given collection.
```
: seq<'T> -> 'T list
```
Example


Output
```

// Signature:
Set.toList : Set  -> 'T list (requires comparison)

// Usage:
Set.toList set
 
```

 
tryFind
--------------
Returns the first element for which the given function returns  true , or  None  if no such element exists.
```
: ('T -> bool) -> seq<'T> -> 'T option
```
Example


Output
```

// Signature:
Seq.tryFind : ('T -> bool) -> seq  -> 'T option

// Usage:
Seq.tryFind predicate source
 
```

 
tryFindIndex
--------------
Returns the index of the first element in the sequence that satisfies the given predicate, or  None  if no such element exists.
```
: ('T -> bool) -> seq<'T> -> int option
```
Example


Output
```

// Signature:
Seq.tryFindIndex : ('T -> bool) -> seq  -> int option

// Usage:
Seq.tryFindIndex predicate source
 
```

 
tryPick
--------------
Applies the given function to successive elements, returning the first value where the function returns a  Some  value.
```
: ('T -> 'U option) -> seq<'T> -> 'U option
```
Example


Output
```

// Signature:
Seq.tryPick : ('T -> 'U option) -> seq  -> 'U option

// Usage:
Seq.tryPick chooser source
 
```

 
truncate
--------------
Returns a sequence that when enumerated returns no more than a specified number of elements.
```
: int -> seq<'T> -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> mySeq = <span style="color:Blue;">seq</span> { <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; i*i }
<span style="color:Blue;">let</span> truncatedSeq = Seq.truncate 5 mySeq
<span style="color:Blue;">let</span> takenSeq = Seq.take 5 mySeq

<span style="color:Blue;">let</span> truncatedSeq2 = Seq.truncate 20 mySeq
<span style="color:Blue;">let</span> takenSeq2 = Seq.take 20 mySeq

<span style="color:Blue;">let</span> printSeq seq1 = Seq.iter (printf <span style="color:#A31515;">"%A "</span>) seq1; printfn <span style="color:#A31515;">""</span> 

<span style="color:Green;">// Up to this point, the sequences are not evaluated. </span>
<span style="color:Green;">// The following code causes the sequences to be evaluated.</span>
truncatedSeq |&gt; printSeq
truncatedSeq2 |&gt; printSeq
takenSeq |&gt; printSeq
<span style="color:Green;">// The following line produces a run-time error (in printSeq):</span>
takenSeq2 |&gt; printSeq
</pre>
Output
```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
```

 
unfold
--------------
Returns a sequence that contains the elements generated by the given computation.
```
: ('State -> 'T * 'State option) -> 'State -> seq<'T>
```
Example

<pre><span style="color:Blue;">let</span> seq1 = Seq.unfold (<span style="color:Blue;">fun</span> state -&gt; <span style="color:Blue;">if</span> (state &gt; 20) <span style="color:Blue;">then</span> None <span style="color:Blue;">else</span> Some(state, state + 1)) 0
printfn <span style="color:#A31515;">"The sequence seq1 contains numbers from 0 to 20."</span> 
<span style="color:Blue;">for</span> x <span style="color:Blue;">in</span> seq1 <span style="color:Blue;">do</span> printf <span style="color:#A31515;">"%d "</span> x
<span style="color:Blue;">let</span> fib = Seq.unfold (<span style="color:Blue;">fun</span> state -&gt;
    <span style="color:Blue;">if</span> (snd state &gt; 1000) <span style="color:Blue;">then</span> None
    <span style="color:Blue;">else</span> Some(fst state + snd state, (snd state, fst state + snd state))) (1,1)
printfn <span style="color:#A31515;">"\nThe sequence fib contains Fibonacci numbers."</span> 
<span style="color:Blue;">for</span> x <span style="color:Blue;">in</span> fib <span style="color:Blue;">do</span> printf <span style="color:#A31515;">"%d "</span> x
</pre>
Output
```
The sequence seq1 contains numbers from 0 to 20.
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 
The sequence fib contains Fibonacci numbers.
2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 
```

 
where
--------------
Returns a new collection containing only the elements of the collection for which the given predicate returns  true . A synonym for  Seq.filter .
```
: ('T -> bool) -> seq<'T> -> seq<'T>
```
Example


Output
```

// Signature:
where : ('T -> bool) -> seq  -> seq 
// Usage:
Seq.where predicate source
 
```

 
windowed
--------------
Returns a sequence that yields sliding windows of containing elements drawn from the input sequence. Each window is returned as a fresh array.
```
: int -> seq<'T> -> seq<'T []>
```
Example

<pre><span style="color:Blue;">let</span> seqNumbers = [ 1.0; 1.5; 2.0; 1.5; 1.0; 1.5 ] :&gt; <span style="color:Blue;">seq</span>&lt;<span style="color:Blue;">float</span>&gt;
<span style="color:Blue;">let</span> seqWindows = Seq.windowed 3 seqNumbers
<span style="color:Blue;">let</span> seqMovingAverage = Seq.map Array.average seqWindows
printfn <span style="color:#A31515;">"Initial sequence: "</span>
printSeq seqNumbers
printfn <span style="color:#A31515;">"\nWindows of length 3: "</span>
printSeq seqWindows
printfn <span style="color:#A31515;">"\nMoving average: "</span>
printSeq seqMovingAverage
</pre>
Output
```
Initial sequence: 
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333  
```

 
zip
--------------
Combines the two sequences into a list of pairs. The two sequences need not have equal lengths: when one sequence is exhausted any remaining elements in the other sequence are ignored.
```
: seq<'T1> -> seq<'T2> -> seq<'T1 * 'T2>
```
Example


Output
```

// Signature:
Seq.zip : seq  -> seq  -> seq 

// Usage:
Seq.zip source1 source2
 
```

 
zip3
--------------
Combines the three sequences into a list of triples. The sequences need not have equal lengths: when one sequence is exhausted any remaining elements in the other sequences are ignored.
```
: seq<'T1> -> seq<'T2> -> seq<'T3> -> seq<'T1 * 'T2 * 'T3>
```
Example


Output
```

// Signature:
Seq.zip3 : seq  -> seq  -> seq  -> seq 

// Usage:
Seq.zip3 source1 source2 source3
 
```

 
 
