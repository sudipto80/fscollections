F# Collections
--------------

[array](https://github.com/sudipto80/fscollections/blob/master/array.md)

[list](https://github.com/sudipto80/fscollections/blob/master/list.md)

[seq](https://github.com/sudipto80/fscollections/blob/master/seq.md)

[map](https://github.com/sudipto80/fscollections/blob/master/map.md)
|Function|Description|
|--------|-----------|
|add|Returns a new map with the binding added to the given map.|
|containsKey|Tests if an element is in the domain of the map.|
|exists|Returns  true  if the given predicate returns true for one of the bindings in the map.|
|filter|Creates a new map containing only the bindings for which the given predicate returns  true .|
|find|Looks up an element in the map.|
|findKey|Evaluates the function on each mapping in the collection. Returns the key for the first mapping where the function returns  true .|
|fold|Folds over the bindings in the map|
|foldBack|Folds over the bindings in the map.|
|forall|Returns true if the given predicate returns true for all of the bindings in the map.|
|isEmpty|Tests whether the map has any bindings.|
|iter|Applies the given function to each binding in the dictionary|
|map|Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The key passed to the function indicates the key of element being transformed.|
|ofArray|Returns a new map made from the given bindings.|
|ofList|Returns a new map made from the given bindings.|
|ofSeq|Returns a new map made from the given bindings.|
|partition|Creates two new maps, one containing the bindings for which the given predicate returns  true , and the other the remaining bindings.|
|pick|Searches the map looking for the first element where the given function returns a  Some  value|
|remove|Removes an element from the domain of the map. No exception is raised if the element is not present.|
|toArray|Returns an array of all key/value pairs in the mapping. The array will be ordered by the keys of the map.|
|toList|Returns a list of all key/value pairs in the mapping. The list will be ordered by the keys of the map.|
|toSeq|Views the collection as an enumerable sequence of pairs. The sequence will be ordered by the keys of the map.|
|tryFind|Looks up an element in the map, returning a  Some  value if the element is in the domain of the map, or  None  if not.|
|tryFindKey|Returns the key of the first mapping in the collection that satisfies the given predicate, or returns  None  if no such element exists.|
|tryPick|Searches the map looking for the first element where the given function returns a  Some  value.|

[set](https://github.com/sudipto80/fscollections/blob/master/set.md)
