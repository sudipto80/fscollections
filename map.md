add
--------------
Returns a new map with the binding added to the given map.
```
: 'Key -> 'T -> Map<'Key,'T> -> Map<'Key,'T>
```
Example

<pre>Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
|&gt; Map.add(0) <span style="color:#A31515;">"zero"</span>
|&gt; Map.iter (<span style="color:Blue;">fun</span> key value -&gt; printfn <span style="color:#A31515;">"key: %d value: %s"</span> key value)
</pre>
Output
```
key: 0 value: zero
key: 1 value: one
key: 2 value: two
key: 3 value: three 
```

 
containsKey
--------------
Tests if an element is in the domain of the map.
```
: 'Key -> Map<'Key,'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Blue;">let</span> findKeyAndPrint key map =
    <span style="color:Blue;">if</span> (Map.containsKey key map) <span style="color:Blue;">then</span>
        printfn <span style="color:#A31515;">"The specified map contains the key %d."</span> key
    <span style="color:Blue;">else</span>
        printfn <span style="color:#A31515;">"The specified map does not contain the key %d."</span> key
findKeyAndPrint 1 map1
findKeyAndPrint 0 map1
</pre>
Output
```
The specified map contains the key 1.
The specified map does not contain the key 0. 
```

 
exists
--------------
Returns  true  if the given predicate returns true for one of the bindings in the map.
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> bool
```
Example


Output
```

// Signature:
Map.exists : ('Key -> 'T -> bool) -> Map  -> bool (requires comparison)

// Usage:
Map.exists predicate table
 
```

 
filter
--------------
Creates a new map containing only the bindings for which the given predicate returns  true .
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> Map<'Key,'T>
```
Example

<pre>printfn <span style="color:#A31515;">"Even numbers and their squares."</span> 
<span style="color:Blue;">let</span> map1 = Map.ofList [<span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; (i, i*i)]
           |&gt; Map.filter (<span style="color:Blue;">fun</span> key _ -&gt; key % 2 = 0)
           |&gt; Map.iter (<span style="color:Blue;">fun</span> key value -&gt; printf <span style="color:#A31515;">"(%d, %d) "</span> key value)
printfn <span style="color:#A31515;">""</span>
</pre>
Output
```
Even numbers and their squares.
(2, 4) (4, 16) (6, 36) (8, 64) (10, 100)  
```

 
find
--------------
Looks up an element in the map.
```
: 'Key -> Map<'Key,'T> -> 'T
```
Example


Output
```

```

 
findKey
--------------
Evaluates the function on each mapping in the collection. Returns the key for the first mapping where the function returns  true .
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> 'Key
```
Example

<pre><span style="color:Blue;">let</span> findKeyFromValue findValue map =
    printfn <span style="color:#A31515;">"With value %A, found key %A."</span> findValue (Map.findKey (<span style="color:Blue;">fun</span> key value -&gt; value = findValue) map)
<span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Blue;">let</span> map2 = Map.ofList [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 10 -&gt; (i, i*i) ]
<span style="color:Blue;">try</span>
    findKeyFromValue <span style="color:#A31515;">"one"</span> map1
    findKeyFromValue <span style="color:#A31515;">"two"</span> map1
    findKeyFromValue 9 map2
    findKeyFromValue 25 map2
    <span style="color:Green;">// The key is not in the map, so the following line throws an exception.</span>
    findKeyFromValue 0 map2
<span style="color:Blue;">with</span>
     :? System.Collections.Generic.KeyNotFoundException <span style="color:Blue;">as</span> e -&gt; printfn <span style="color:#A31515;">"%s"</span> e.Message
</pre>
Output
```
With value "one", found key 1.
With value "two", found key 2.
With value 9, found key 3.
With value 25, found key 5.
Exception of type 'System.Collections.Generic.KeyNotFoundException' was thrown. 
```

 
fold
--------------
Folds over the bindings in the map
```
: ('State -> 'Key -> 'T -> 'State) -> 'State -> Map<'Key,'T> -> 'State
```
Example

<pre><span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Green;">// Sum the keys. </span>
<span style="color:Blue;">let</span> result1 = Map.fold (<span style="color:Blue;">fun</span> state key value -&gt; state + key) 0 map1
printfn <span style="color:#A31515;">"Result: %d"</span> result1
<span style="color:Green;">// Concatenate the values. </span>
<span style="color:Blue;">let</span> result2 = Map.fold (<span style="color:Blue;">fun</span> state key value -&gt; state + value + <span style="color:#A31515;">" "</span>) <span style="color:#A31515;">""</span> map1
printfn <span style="color:#A31515;">"Result: %s"</span> result2
</pre>
Output
```
Result: 6
Result: one two three  
```

 
foldBack
--------------
Folds over the bindings in the map.
```
: ('Key -> 'T -> 'State -> 'State) -> Map<'Key,'T> -> 'State -> 'State
```
Example

<pre><span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Green;">// Sum the keys. </span>
<span style="color:Blue;">let</span> result1 = Map.foldBack (<span style="color:Blue;">fun</span> key value state -&gt; state + key) map1 0
printfn <span style="color:#A31515;">"Result: %d"</span> result1
<span style="color:Green;">// Concatenate the values. </span>
<span style="color:Blue;">let</span> result2 = Map.foldBack (<span style="color:Blue;">fun</span> key value state -&gt; state + value + <span style="color:#A31515;">" "</span>) map1 <span style="color:#A31515;">""</span>
printfn <span style="color:#A31515;">"Result: %s"</span> result2 
</pre>
Output
```
Result: 6
Result: three two one 
```

 
forall
--------------
Returns true if the given predicate returns true for all of the bindings in the map.
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> bool
```
Example

<pre><span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Blue;">let</span> map2 = Map.ofList [ (-1, <span style="color:#A31515;">"negative one"</span>); (2, <span style="color:#A31515;">"two"</span>); (3, <span style="color:#A31515;">"three"</span>) ]
<span style="color:Blue;">let</span> allPositive = Map.forall (<span style="color:Blue;">fun</span> key value -&gt; key &gt; 0)
printfn <span style="color:#A31515;">"%b %b"</span> (allPositive map1) (allPositive map2)
</pre>
Output
```
true false 
```

 
isEmpty
--------------
Tests whether the map has any bindings.
```
: Map<'Key,'T> -> bool
```
Example


Output
```

// Signature:
Map.isEmpty : Map  -> bool (requires comparison)

// Usage:
Map.isEmpty table
 
```

 
iter
--------------
Applies the given function to each binding in the dictionary
```
: ('Key -> 'T -> unit) -> Map<'Key,'T> -> unit
```
Example


Output
```

// Signature:
Map.iter : ('Key -> 'T -> unit) -> Map  -> unit (requires comparison)

// Usage:
Map.iter action table
 
```

 
map
--------------
Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The key passed to the function indicates the key of element being transformed.
```
: ('Key -> 'T -> 'U) -> Map<'Key,'T> -> Map<'Key,'U>
```
Example

<pre><span style="color:Blue;">let</span> map1 = Map.ofList [ (1, <span style="color:#A31515;">"One"</span>); (2, <span style="color:#A31515;">"Two"</span>); (3, <span style="color:#A31515;">"Three"</span>) ]
<span style="color:Blue;">let</span> map2 = map1 |&gt; Map.map (<span style="color:Blue;">fun</span> key value -&gt; value.ToUpper())
<span style="color:Blue;">let</span> map3 = map1 |&gt; Map.map (<span style="color:Blue;">fun</span> key value -&gt; value.ToLower())
printfn <span style="color:#A31515;">"%A"</span> map1
printfn <span style="color:#A31515;">"%A"</span> map2
printfn <span style="color:#A31515;">"%A"</span> map3
</pre>
Output
```
map [(1, "One"); (2, "Two"); (3, "Three")]
map [(1, "ONE"); (2, "TWO"); (3, "THREE")]
map [(1, "one"); (2, "two"); (3, "three")] 
```

 
ofArray
--------------
Returns a new map made from the given bindings.
```
: ('Key * 'T) [] -> Map<'Key,'T>
```
Example


Output
```

// Signature:
Map.ofArray : ('Key * 'T) [] -> Map  (requires comparison)

// Usage:
Map.ofArray elements
 
```

 
ofList
--------------
Returns a new map made from the given bindings.
```
: 'Key * 'T list -> Map<'Key,'T>
```
Example


Output
```

// Signature:
Map.ofList : 'Key * 'T list -> Map  (requires comparison)

// Usage:
Map.ofList elements
 
```

 
ofSeq
--------------
Returns a new map made from the given bindings.
```
: seq<'Key * 'T> -> Map<'Key,'T>
```
Example


Output
```

// Signature:
Map.ofSeq : seq  -> Map  (requires comparison)

// Usage:
Map.ofSeq elements
 
```

 
partition
--------------
Creates two new maps, one containing the bindings for which the given predicate returns  true , and the other the remaining bindings.
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> Map<'Key,'T> * Map<'Key,'T>
```
Example

<pre><span style="color:Blue;">let</span> map1 = [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1..10 -&gt; (i, i*i)] |&gt; Map.ofList
<span style="color:Blue;">let</span> (mapEven, mapOdd) = Map.partition (<span style="color:Blue;">fun</span> key value -&gt; key % 2 = 0) map1
printfn <span style="color:#A31515;">"Evens: %A"</span> mapEven
printfn <span style="color:#A31515;">"Odds: %A"</span> mapOdd
</pre>
Output
```
Evens: map [(2, 4); (4, 16); (6, 36); (8, 64); (10, 100)]
Odds: map [(1, 1); (3, 9); (5, 25); (7, 49); (9, 81)] 
```

 
pick
--------------
Searches the map looking for the first element where the given function returns a  Some  value
```
: ('Key -> 'T -> 'U option) -> Map<'Key,'T> -> 'U
```
Example

<pre><span style="color:Blue;">let</span> map1 = [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 100 -&gt; (i, 100 - i) ] |&gt; Map.ofList
<span style="color:Blue;">let</span> result = Map.pick (<span style="color:Blue;">fun</span> key value -&gt; <span style="color:Blue;">if</span> key = value <span style="color:Blue;">then</span> Some(key) <span style="color:Blue;">else</span> None) map1
printfn <span style="color:#A31515;">"Result where key and value are the same: %d"</span> result
</pre>
Output
```
Result where key and value are the same: 50 
```

 
remove
--------------
Removes an element from the domain of the map. No exception is raised if the element is not present.
```
: 'Key -> Map<'Key,'T> -> Map<'Key,'T>
```
Example


Output
```

// Signature:
Map.remove : 'Key -> Map  -> Map  (requires comparison)

// Usage:
Map.remove key table
 
```

 
toArray
--------------
Returns an array of all key/value pairs in the mapping. The array will be ordered by the keys of the map.
```
: Map<'Key,'T> -> ('Key * 'T) []
```
Example


Output
```

// Signature:
Map.toArray : Map  -> ('Key * 'T) [] (requires comparison)

// Usage:
Map.toArray table
 
```

 
toList
--------------
Returns a list of all key/value pairs in the mapping. The list will be ordered by the keys of the map.
```
: Map<'Key,'T> -> ('Key * 'T) list
```
Example


Output
```

// Signature:
Map.toList : Map  -> ('Key * 'T) list (requires comparison)

// Usage:
Map.toList table
 
```

 
toSeq
--------------
Views the collection as an enumerable sequence of pairs. The sequence will be ordered by the keys of the map.
```
: Map<'Key,'T> -> seq<'Key * 'T>
```
Example


Output
```

// Signature:
Map.toSeq : Map  -> seq  (requires comparison)

// Usage:
Map.toSeq table
 
```

 
tryFind
--------------
Looks up an element in the map, returning a  Some  value if the element is in the domain of the map, or  None  if not.
```
: 'Key -> Map<'Key,'T> -> 'T option
```
Example

<pre><span style="color:Blue;">let</span> map1 = [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 100 -&gt; (i, i*i) ] |&gt; Map.ofList
<span style="color:Blue;">let</span> result = Map.tryFind 50 map1
<span style="color:Blue;">match</span> result <span style="color:Blue;">with</span>
| Some x -&gt; printfn <span style="color:#A31515;">"Found %d."</span> x
| None -&gt; printfn <span style="color:#A31515;">"Did not find the specified value."</span>
</pre>
Output
```
Found 2500. 
```

 
tryFindKey
--------------
Returns the key of the first mapping in the collection that satisfies the given predicate, or returns  None  if no such element exists.
```
: ('Key -> 'T -> bool) -> Map<'Key,'T> -> 'Key option
```
Example

<pre><span style="color:Blue;">let</span> map1 = [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 100 -&gt; (i, i*i) ] |&gt; Map.ofList
<span style="color:Blue;">let</span> result = Map.tryFindKey (<span style="color:Blue;">fun</span> key value -&gt; key = value) map1
<span style="color:Blue;">match</span> result <span style="color:Blue;">with</span>
| Some key -&gt; printfn <span style="color:#A31515;">"Found element with key %d."</span> key
| None -&gt; printfn <span style="color:#A31515;">"Did not find any element that matches the condition."</span>
</pre>
Output
```
Found element with key 1. 
```

 
tryPick
--------------
Searches the map looking for the first element where the given function returns a  Some  value.
```
: ('Key -> 'T -> 'U option) -> Map<'Key,'T> -> 'U option
```
Example

<pre><span style="color:Blue;">let</span> map1 = [ <span style="color:Blue;">for</span> i <span style="color:Blue;">in</span> 1 .. 100 -&gt; (i, 100 - i) ] |&gt; Map.ofList
<span style="color:Blue;">let</span> result = Map.tryPick (<span style="color:Blue;">fun</span> key value -&gt; <span style="color:Blue;">if</span> key = value <span style="color:Blue;">then</span> Some(key) <span style="color:Blue;">else</span> None) map1
<span style="color:Blue;">match</span> result <span style="color:Blue;">with</span>
| Some x -&gt; printfn <span style="color:#A31515;">"Result where key and value are the same: %d"</span> x
| None -&gt; printfn <span style="color:#A31515;">"No result satisifies the condition."</span>
</pre>
Output
```
Result where key and value are the same: 50 
```
 
