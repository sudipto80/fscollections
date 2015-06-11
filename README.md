F# Collections
--------------

[array](https://github.com/sudipto80/fscollections/blob/master/array.md)

[list](https://github.com/sudipto80/fscollections/blob/master/list.md)

[seq](https://github.com/sudipto80/fscollections/blob/master/seq.md)

[map](https://github.com/sudipto80/fscollections/blob/master/map.md)


|Function|Description|
|:--------|:-----------|
|[add](https://github.com/sudipto80/fscollections/blob/master/map.md#add)|Returns a new map with the binding added to the given map.|
|[containsKey](https://github.com/sudipto80/fscollections/blob/master/map.md#containsKey)|Tests if an element is in the domain of the map.|
|[exists](https://github.com/sudipto80/fscollections/blob/master/map.md#exists)|Returns  true  if the given predicate returns true for one of the bindings in the map.|
|[filter](https://github.com/sudipto80/fscollections/blob/master/map.md#filter)|Creates a new map containing only the bindings for which the given predicate returns  true .|
|[find](https://github.com/sudipto80/fscollections/blob/master/map.md#find)|Looks up an element in the map.|
|[findKey](https://github.com/sudipto80/fscollections/blob/master/map.md#findKey)|Evaluates the function on each mapping in the collection. Returns the key for the first mapping where the function returns  true .|
|[fold](https://github.com/sudipto80/fscollections/blob/master/map.md#fold)|Folds over the bindings in the map|
|[foldBack](https://github.com/sudipto80/fscollections/blob/master/map.md#foldBack)|Folds over the bindings in the map.|
|[forall](https://github.com/sudipto80/fscollections/blob/master/map.md#forall)|Returns true if the given predicate returns true for all of the bindings in the map.|
|[isEmpty](https://github.com/sudipto80/fscollections/blob/master/map.md#isEmpty)|Tests whether the map has any bindings.|
|[iter](https://github.com/sudipto80/fscollections/blob/master/map.md#iter)|Applies the given function to each binding in the dictionary|
|[map](https://github.com/sudipto80/fscollections/blob/master/map.md#map)|Creates a new collection whose elements are the results of applying the given function to each of the elements of the collection. The key passed to the function indicates the key of element being transformed.|
|[ofArray](https://github.com/sudipto80/fscollections/blob/master/map.md#ofArray)|Returns a new map made from the given bindings.|
|[ofList](https://github.com/sudipto80/fscollections/blob/master/map.md#ofList)|Returns a new map made from the given bindings.|
|[ofSeq](https://github.com/sudipto80/fscollections/blob/master/map.md#ofSeq)|Returns a new map made from the given bindings.|
|[partition](https://github.com/sudipto80/fscollections/blob/master/map.md#partition)|Creates two new maps, one containing the bindings for which the given predicate returns  true , and the other the remaining bindings.|
|[pick](https://github.com/sudipto80/fscollections/blob/master/map.md#pick)|Searches the map looking for the first element where the given function returns a  Some  value|
|[remove](https://github.com/sudipto80/fscollections/blob/master/map.md#remove)|Removes an element from the domain of the map. No exception is raised if the element is not present.|
|[toArray](https://github.com/sudipto80/fscollections/blob/master/map.md#toArray)|Returns an array of all key/value pairs in the mapping. The array will be ordered by the keys of the map.|
|[toList](https://github.com/sudipto80/fscollections/blob/master/map.md#toList)|Returns a list of all key/value pairs in the mapping. The list will be ordered by the keys of the map.|
|[toSeq](https://github.com/sudipto80/fscollections/blob/master/map.md#toSeq)|Views the collection as an enumerable sequence of pairs. The sequence will be ordered by the keys of the map.|
|[tryFind](https://github.com/sudipto80/fscollections/blob/master/map.md#tryFind)|Looks up an element in the map, returning a  Some  value if the element is in the domain of the map, or  None  if not.|
|[tryFindKey](https://github.com/sudipto80/fscollections/blob/master/map.md#tryFindKey)|Returns the key of the first mapping in the collection that satisfies the given predicate, or returns  None  if no such element exists.|
|[tryPick](https://github.com/sudipto80/fscollections/blob/master/map.md#tryPick)|Searches the map looking for the first element where the given function returns a  Some  value.|

[set](https://github.com/sudipto80/fscollections/blob/master/set.md)
