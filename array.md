append
--------------
Creates an array that contains the elements of one array followed by the elements of another array.
```
: 'T [] -> 'T [] -> 'T []
```
Example
```fsharp
printfn  "%A"  (Array.append [| 1; 2; 3|] [| 4; 5; 6|])
 ```
Output
```
[|1; 2; 3; 4; 5; 6|] 
```

 
average
--------------
Returns the average of the elements in an array.
```
: ^T [] -> ^T
```
Example
```fsharp
let  average1 = Array.average [| 1.0 .. 10.0 |]
printfn  "Average: %f"  average1
 // To get the average of an array of integers,   
 // use Array.averageBy to convert to float.  
 let  average2 = Array.averageBy ( fun  elem ->  float  elem) [|1 .. 10 |]
printfn  "Average: %f"  average2
 ```
Output
```
Average: 5.500000
Average: 5.500000 
```

 
averageBy
--------------
Returns the average of the elements generated by applying a function to each element of an array.
```
: ('T -> ^U) -> 'T [] -> ^U
```
Example
```fsharp
let  avg2 = Array.averageBy ( fun  elem ->  float  elem) [|1 .. 10|]
printfn  "%f"  avg2
 ```
Output
```
5.500000 
```

 
blit
--------------
Reads a range of elements from one array and writes them into another.
```
: 'T [] -> int -> 'T [] -> int -> int -> unit
```
Example
```fsharp
let  array1 = [| 1 .. 10 |]
 let  array2 = Array.zeroCreate 20
 // Copy 4 elements from index 3 of array1 to index 5 of array2. 
Array.blit array1 3 array2 5 4
printfn  "%A"  array2
 ```
Output
```
[|0; 0; 0; 0; 0; 4; 5; 6; 7; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0|] 
```

 
choose
--------------
Applies a supplied function to each element of an array. Returns an array that contains the results  x  for each element for which the function returns  Some(x) .
```
: ('T ->'U option) -> 'T [] -> 'U []
```
Example
```fsharp
printfn  "%A"  (Array.choose ( fun  elem ->  if  elem % 2 = 0  then 
                                            Some( float  (elem*elem - 1))
                                         else 
                                            None) [| 1 .. 10 |])
 ```
Output
```
[|3.0; 15.0; 35.0; 63.0; 99.0|] 
```

 
collect
--------------
Applies the supplied function to each element of an array, concatenates the results, and returns the combined array.
```
: ('T -> 'U []) -> 'T [] -> 'U []
```
Example
```fsharp
printfn  "%A"  (Array.collect ( fun  elem -> [| 0 .. elem |]) [| 1; 5; 10|])
 ```
Output
```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|] 
```

 
concat
--------------
Creates an array that contains the elements of each of the supplied sequence of arrays.
```
: seq<'T []> -> 'T []
```
Example
```fsharp
let  multiplicationTable max =  seq  {  for  i  in  1 .. max -> [|  for  j  in  1 .. max -> (i, j, i*j) |] }
printfn  "%A"  (Array.concat (multiplicationTable 3))
 ```
Output
```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6);
 (3, 1, 3); (3, 2, 6); (3, 3, 9)|] 
```

 
copy
--------------
Creates an array that contains the elements of the supplied array.
```
: 'T -> 'T []
```
Example
```fsharp
let  array1 = [| 1 .. 10 |]
 let  array2 = Array.copy array1
printfn  "%A\n%A"  array1 array2
 ```
Output
```
[|1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
[|1; 2; 3; 4; 5; 6; 7; 8; 9; 10|] 
```

 
create
--------------
Creates an array whose elements are all initially the supplied value.
```
: int -> 'T -> 'T []
```
Example
```fsharp
let  array1 = Array.create 10  ""  
 for  i  in  0 .. array1.Length - 1  do 
    Array.set array1 i (i.ToString())
 for  i  in  0 .. array1.Length - 1  do 
    printf  "%s "  (Array.get array1 i)
 ```
Output
```
0 1 2 3 4 5 6 7 8 9 
```

 
exists
--------------
Tests whether any element of an array satisfies the supplied predicate.
```
: ('T -> bool) -> 'T [] -> bool
```
Example
```fsharp
let  allNegative = Array.exists ( fun  elem -> abs (elem) = elem) >>  not 
printfn  "%A"  (allNegative [| -1; -2; -3 |])
printfn  "%A"  (allNegative [| -10; -1; 5 |])
printfn  "%A"  (allNegative [| 0 |])
 ```
Output
```
true
false
false 
```

 
exists2
--------------
Tests whether any pair of corresponding elements of two arrays satisfy the supplied condition.
```
: ('T1 -> 'T2 -> bool) -> 'T1 [] -> 'T2 [] -> bool
```
Example
```fsharp
let  haveEqualElement = Array.exists2 ( fun  elem1 elem2 -> elem1 = elem2)
printfn  "%A"  (haveEqualElement [| 1; 2; 3 |] [| 3; 2; 1|])
 ```
Output
```
true 
```

 
fill
--------------
Fills a range of elements of an array with the supplied value.
```
: 'T [] -> int -> int -> 'T -> unit
```
Example
```fsharp
let  arrayFill1 = [| 1 .. 25 |]
Array.fill arrayFill1 2 20 0
printfn  "%A"  arrayFill1
 ```
Output
```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|] 
```

 
filter
--------------
Returns a collection that contains only the elements of the supplied array for which the supplied condition returns  true .
```
: ('T -> bool) -> 'T [] -> 'T []
```
Example
```fsharp
let  names = [| "Bob" ;  "Ann" ;  "Stephen" ;  "Vivek" ;  "Fred" ;  "Kim" ;  "Brian" ;  "Ling" ;  "Jane" ;  "Jonathan" |]
 let  longNames = names |> Array.filter ( fun  x -> x.Length > 4)

printfn  "names = %A\n"  names
printfn  "longNames = %A"  longNames
 ```
Output
```
names = [|"Bob"; "Ann"; "Stephen"; "Vivek"; "Fred"; "Kim"; "Brian"; "Ling"; "Jane"; "Jonathan"|]

longNames = [|"Stephen"; "Vivek"; "Brian"; "Jonathan"|] 
```

 
find
--------------
Returns the first element for which the supplied function returns  true . Raises  KeyNotFoundException  if no such element exists.
```
: ('T -> bool) -> 'T [] -> 'T
```
Example
```fsharp
let  arrayA = [| 2 .. 100 |]
 let  delta = 1.0e-10
 let  isPerfectSquare (x: int ) =
     let  y = sqrt ( float  x)
    abs(y - round y) < delta
 let  isPerfectCube (x: int ) =
     let  y = System.Math.Pow( float  x, 1.0/3.0)
    abs(y - round y) < delta
 let  element = Array.find ( fun  elem -> isPerfectSquare elem && isPerfectCube elem) arrayA
 let  index = Array.findIndex ( fun  elem -> isPerfectSquare elem && isPerfectCube elem) arrayA
printfn  "The first element that is both a square and a cube is %d and its index is %d."  element index
 ```
Output
```
The first element that is both a square and a cube is 64 and its index is 62. 
```

 
findIndex
--------------
Returns the index of the first element in an array that satisfies the supplied condition. Raises  KeyNotFoundException  if none of the elements satisfy the condition.
```
: ('T -> bool) -> 'T [] -> int
```
Example
```fsharp
let  arrayA = [| 2 .. 100 |]
 let  delta = 1.0e-10
 let  isPerfectSquare (x: int ) =
     let  y = sqrt ( float  x)
    abs(y - round y) < delta
 let  isPerfectCube (x: int ) =
     let  y = System.Math.Pow( float  x, 1.0/3.0)
    abs(y - round y) < delta
 let  element = Array.find ( fun  elem -> isPerfectSquare elem && isPerfectCube elem) arrayA
 let  index = Array.findIndex ( fun  elem -> isPerfectSquare elem && isPerfectCube elem) arrayA
printfn  "The first element that is both a square and a cube is %d and its index is %d."  element index
 ```
Output
```
The first element that is both a square and a cube is 64 and its index is 62. 
```

 
fold
--------------
Applies a function to each element of an array, threading an accumulator argument through the computation. If the input function is  f  and the array elements are  i0...iN , this function computes  f (...(f s i0)...) iN .
```
: ('State -> 'T -> 'State) -> 'State -> 'T [] -> 'State
```
Example
```fsharp
let  sumArray  array  = Array.fold ( fun  acc elem -> acc + elem) 0  array 
printfn  "Sum of the elements of array %A is %d."  [ 1 .. 3 ] (sumArray [| 1 .. 3 |])

 // The following example computes the average of a array.  
 let  averageArray  array  = (Array.fold ( fun  acc elem -> acc +  float  elem) 0.0  array  /  float   array .Length)

 // The following example computes the standard deviation of a array.  
 // The standard deviation is computed by taking the square root of the  
 // sum of the variances, which are the differences between each value  
 // and the average.  
 let  stdDevArray  array  =
     let  avg = averageArray  array 
    sqrt (Array.fold ( fun  acc elem -> acc + ( float  elem - avg) ** 2.0 ) 0.0  array  /  float   array .Length)

 let  testArray arrayTest =
    printfn  "Array %A average: %f stddev: %f"  arrayTest (averageArray arrayTest) (stdDevArray arrayTest)

testArray [|1; 1; 1|]
testArray [|1; 2; 1|]
testArray [|1; 2; 3|]

 // Array.fold is the same as to Array.iter when the accumulator is not used.  
 let  printArray  array  = Array.fold ( fun  acc elem -> printfn  "%A"  elem) ()  array 
printArray [|0.0; 1.0; 2.5; 5.1 |]
 ```
Output
```
Sum of the elements of array [1; 2; 3] is 6.
Array [|1; 1; 1|] average: 1.000000 stddev: 0.000000
Array [|1; 2; 1|] average: 1.333333 stddev: 0.471405
Array [|1; 2; 3|] average: 2.000000 stddev: 0.816497
0.0
1.0
2.5
5.1 
```

 
fold2
--------------
Applies a function to pairs of elements from two supplied arrays, left-to-right, threading an accumulator argument through the computation. The two input arrays must have the same lengths; otherwise,  ArgumentException  is raised.
```
: ('State -> 'T1 -> 'T2 -> 'State) -> 'State -> 'T1 [] -> 'T2 [] -> 'State
```
Example
```fsharp
// Use Array.fold2 to perform computations over two arrays (of equal size)  
 // at the same time.  
 // Example: Add the greater element at each array position.  
 let  sumGreatest array1 array2 =
    Array.fold2 ( fun  acc elem1 elem2 ->
        acc + max elem1 elem2) 0 array1 array2

 let  sum = sumGreatest [| 1; 2; 3 |] [| 3; 2; 1 |]
printfn  "The sum of the greater of each pair of elements in the two arrays is %d."  sum
 ```
Output
```
The sum of the greater of each pair of elements in the two arrays is 8. 
```

 
foldBack
--------------
Applies a function to each element of an array, threading an accumulator argument through the computation. If the input function is  f  and the array elements are  i0...iN , this function computes  f i0 (...(f iN s)) .
```
: ('T -> 'State -> 'State) -> 'T [] -> 'State -> 'State
```
Example
```fsharp
// This computes 3 - 2 - 1, which evalates to -6.  
 let  subtractArray array1 = Array.fold ( fun  acc elem -> acc - elem) 0 array1
printfn  "%d"  (subtractArray [| 1; 2; 3 |])

 // This computes 3 - (2 - (0 - 1)), which evaluates to 2.  
 let  subtractArrayBack array1 = Array.foldBack ( fun  elem acc -> elem - acc) array1 0
printfn  "%d"  (subtractArrayBack [| 1; 2; 3 |])
 ```
Output
```
-6
2 
```

 
foldBack2
--------------
Applies a function to pairs of elements from two supplied arrays, right-to-left, threading an accumulator argument through the computation. The two input arrays must have the same lengths; otherwise,  ArgumentException  is raised.
```
: ('T1 -> 'T2 -> 'State -> 'State) -> 'T1 [] -> 'T2 [] -> 'State -> 'State
```
Example
```fsharp
type  Transaction =
    | Deposit
    | Withdrawal

 let  transactionTypes = [| Deposit; Deposit; Withdrawal |]
 let  transactionAmounts = [| 100.00; 1000.00; 95.00 |]
 let  initialBalance = 200.00

 let  endingBalance = Array.foldBack2 ( fun  elem1 elem2 acc ->
                         match  elem1  with 
                        | Deposit -> acc + elem2
                        | Withdrawal -> acc - elem2)
                        transactionTypes
                        transactionAmounts
                        initialBalance
printfn  "Ending balance: $%.2f"  endingBalance
 ```
Output
```
Ending balance: $1205.00 
```

 
forall
--------------
Tests whether all elements of an array satisfy the supplied condition.
```
: ('T -> bool) -> 'T [] -> bool
```
Example
```fsharp
let  allPositive = Array.forall ( fun  elem -> elem > 0)
printfn  "%A"  (allPositive [| 0; 1; 2; 3 |])
printfn  "%A"  (allPositive [| 1; 2; 3 |])
 ```
Output
```
false
true 
```

 
get
--------------
Gets an element from an array.
```
: 'T [] -> int -> 'T
```
Example
```fsharp
```
Output
```

```

 
isEmpty
--------------
Tests whether an array has any elements.
```
: 'T [] -> bool
```
Example
```fsharp
let  printArray array1 = 
     if  (Array.isEmpty array1)  then 
        printfn  "There are no elements in this array."  
     else 
        printfn  "This array contains the following elements:" 
        Array.iter ( fun  elem -> printf  "%A "  elem) array1
        printfn  "" 
printArray [|  "test1" ;  "test2"  |]
printArray [| |]
 ```
Output
```
This array contains the following elements:
"test1" "test2" 
There are no elements in this array. 
```

 
iter
--------------
Applies the supplied function to each element of an array.
```
: ('T -> unit) -> 'T [] -> unit
```
Example
```fsharp
printf  "Array.iter: " 
Array.iter ( fun  (a,b) -> printf  "(%d, %d) "  a b) [|  for  i  in  1..5 -> (i, i*i) |]
 ```
Output
```
Array.iter: (1, 1) (2, 4) (3, 9) (4, 16) (5, 25) 
```

 
iter2
--------------
Applies the supplied function to a pair of elements from matching indexes in two arrays. The two arrays must have the same lengths; otherwise,  ArgumentException  is raised.
```
: ('T1 -> 'T2 -> unit) -> 'T1 [] -> 'T2 [] -> unit)
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  array2 = [| 4; 5; 6 |]
Array.iter ( fun  x -> printfn  "Array.iter: element is %d"  x) array1
Array.iteri( fun  i x -> printfn  "Array.iteri: element %d is %d"  i x) array1
Array.iter2 ( fun  x y -> printfn  "Array.iter2: elements are %d %d"  x y) array1 array2
Array.iteri2 ( fun  i x y ->
               printfn  "Array.iteri2: element %d of array1 is %d element %d of array2 is %d" 
                 i x i y)
            array1 array2
 ```
Output
```
Array.iter: element is 1
Array.iter: element is 2
Array.iter: element is 3
Array.iteri: element 0 is 1
Array.iteri: element 1 is 2
Array.iteri: element 2 is 3
Array.iter2: elements are 1 4
Array.iter2: elements are 2 5
Array.iter2: elements are 3 6
Array.iteri2: element 0 of array1 is 1 element 0 of array2 is 4
Array.iteri2: element 1 of array1 is 2 element 1 of array2 is 5
Array.iteri2: element 2 of array1 is 3 element 2 of array2 is 6 
```

 
iteri
--------------
Applies the supplied function to each element of an array. The integer passed to the function indicates the index of the element.
```
: (int -> 'T -> unit) -> 'T [] -> unit
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  array2 = [| 4; 5; 6 |]
Array.iter ( fun  x -> printfn  "Array.iter: element is %d"  x) array1
Array.iteri( fun  i x -> printfn  "Array.iteri: element %d is %d"  i x) array1
Array.iter2 ( fun  x y -> printfn  "Array.iter2: elements are %d %d"  x y) array1 array2
Array.iteri2 ( fun  i x y ->
               printfn  "Array.iteri2: element %d of array1 is %d element %d of array2 is %d" 
                 i x i y)
            array1 array2
 ```
Output
```
Array.iter: element is 1
Array.iter: element is 2
Array.iter: element is 3
Array.iteri: element 0 is 1
Array.iteri: element 1 is 2
Array.iteri: element 2 is 3
Array.iter2: elements are 1 4
Array.iter2: elements are 2 5
Array.iter2: elements are 3 6
Array.iteri2: element 0 of array1 is 1 element 0 of array2 is 4
Array.iteri2: element 1 of array1 is 2 element 1 of array2 is 5
Array.iteri2: element 2 of array1 is 3 element 2 of array2 is 6 
```

 
iteri2
--------------
Applies the supplied function to a pair of elements from matching indexes in two arrays, also passing the index of the elements. The two arrays must have the same lengths; otherwise, an  ArgumentException  is raised.
```
: (int -> 'T1 -> 'T2 -> unit) -> 'T1 [] -> 'T2 [] -> unit
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  array2 = [| 4; 5; 6 |]
Array.iter ( fun  x -> printfn  "Array.iter: element is %d"  x) array1
Array.iteri( fun  i x -> printfn  "Array.iteri: element %d is %d"  i x) array1
Array.iter2 ( fun  x y -> printfn  "Array.iter2: elements are %d %d"  x y) array1 array2
Array.iteri2 ( fun  i x y ->
               printfn  "Array.iteri2: element %d of array1 is %d element %d of array2 is %d" 
                 i x i y)
            array1 array2
 ```
Output
```
Array.iter: element is 1
Array.iter: element is 2
Array.iter: element is 3
Array.iteri: element 0 is 1
Array.iteri: element 1 is 2
Array.iteri: element 2 is 3
Array.iter2: elements are 1 4
Array.iter2: elements are 2 5
Array.iter2: elements are 3 6
Array.iteri2: element 0 of array1 is 1 element 0 of array2 is 4
Array.iteri2: element 1 of array1 is 2 element 1 of array2 is 5
Array.iteri2: element 2 of array1 is 3 element 2 of array2 is 6 
```

 
length
--------------
Returns the length of an array. The  Length  property does the same thing.
```
: 'T [] -> int
```
Example
```fsharp
```
Output
```

```

 
map
--------------
Creates an array whose elements are the results of applying the supplied function to each of the elements of a supplied array.
```
: ('T -> 'U) -> 'T [] -> 'U []
```
Example
```fsharp
let  data = [| 1; 2; 3; 4 |]
 let  r1 = data |> Array.map ( fun  x -> x + 1)
printfn  "Adding '1' using map = %A"  r1
 let  r2 = data |> Array.map  string 
printfn  "Converting to strings by using map = %A"  r2
 let  r3 = data |> Array.map ( fun  x -> (x, x))
printfn  "Converting to tupels by using map = %A"  r3
 ```
Output
```
Adding '1' using map = [|2; 3; 4; 5|]
Converting to strings by using map = [|"1"; "2"; "3"; "4"|]
Converting to tuples by using map = [|(1, 1); (2, 2); (3, 3); (4, 4)|] 
```

 
map2
--------------
Creates an array whose elements are the results of applying the supplied function to the corresponding elements of two supplied arrays. The two input arrays must have the same lengths; otherwise,  ArgumentException  is raised.
```
: ('T1 -> 'T2 -> 'U) -> 'T1 [] -> 'T2 [] -> 'U []
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  array2 = [| 4; 5; 6 |]
 let  arrayOfSums = Array.map2 ( fun  x y -> x + y) array1 array2
printfn  "%A"  arrayOfSums
 ```
Output
```
[|5; 7; 9|] 
```

 
mapi
--------------
Creates an array whose elements are the results of applying the supplied function to each of the elements of a supplied array. An integer index passed to the function indicates the index of the element being transformed.
```
: (int -> 'T -> 'U) -> 'T [] -> 'U []
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  newArray = Array.mapi ( fun  i x -> (i, x)) array1
printfn  "%A"  newArray
 ```
Output
```
[|(0, 1); (1, 2); (2, 3)|] 
```

 
mapi2
--------------
Creates an array whose elements are the results of applying the supplied function to the corresponding elements of the two collections pairwise, also passing the index of the elements. The two input arrays must have the same lengths; otherwise,  ArgumentException  is raised.
```
: (int -> 'T1 -> 'T2 -> 'U) -> 'T1 [] -> 'T2 [] -> 'U []
```
Example
```fsharp
let  array1 = [| 1; 2; 3 |]
 let  array2 = [| 4; 5; 6 |]
 let  arrayAddTimesIndex = Array.mapi2 ( fun  i x y -> (x + y) * i) array1 array2
printfn  "%A"  arrayAddTimesIndex
 ```
Output
```
[|0; 7; 18|] 
```

 
max
--------------
Returns the largest of all elements of an array.  Operators.max  is used to compare the elements.
```
: 'T [] -> 'T
```
Example
```fsharp
```
Output
```

```

 
maxBy
--------------
Returns the largest of all elements of an array, compared via  Operators.max  on the function result.
```
: ('T -> 'U) -> 'T [] -> 'T
```
Example
```fsharp
[| -10.0 .. 10.0 |]
|> Array.maxBy ( fun  x -> 1.0 - x * x)
|> printfn  "%A" 
 ```
Output
```
0.0 
```

 
min
--------------
Returns the smallest of all elements of an array.  Operators.min  is used to compare the elements.
```
: ('T [] -> 'T
```
Example
```fsharp
```
Output
```

module Array
 
```

 
minBy
--------------
Returns the smallest of all elements of an array.  Operators.min  is used to compare the elements.
```
: ('T -> 'U) -> 'T [] -> 'T
```
Example
```fsharp
[| -10.0 .. 10.0 |]
|> Array.minBy ( fun  x -> x * x - 1.0)
|> printfn  "%A" 
 ```
Output
```
0.0 
```

 
ofList
--------------
Creates an array from the supplied list.
```
: 'T list -> 'T []
```
Example
```fsharp
let  array1 = Array.ofList [ 1 .. 10]
 ```
Output
```
val array1 : int [] = [|1; 2; 3; 4; 5; 6; 7; 8; 9; 10|] 
```

 
ofSeq
--------------
Creates an array from the supplied enumerable object.
```
: seq<'T> -> 'T []
```
Example
```fsharp
let  array1 = Array.ofSeq (  seq  { 1 .. 10 } )
 ```
Output
```
val array1 : int [] = [|1; 2; 3; 4; 5; 6; 7; 8; 9; 10|] 
```

 
partition
--------------
Splits an array into two arrays, one containing the elements for which the supplied condition returns  true , and the other containing those for which it returns  false .
```
: ('T -> bool) -> 'T [] -> 'T [] * 'T []
```
Example
```fsharp
let  removeOutliers array1 min max =
    Array.partition ( fun  elem -> elem > min && elem < max) array1
    |> fst
removeOutliers [| 1 .. 100 |] 50 60
|> printf  "%A" 
 ```
Output
```
[|51; 52; 53; 54; 55; 56; 57; 58; 59|] 
```

 
permute
--------------
Permutes the elements of an array according to the specified permutation.
```
: (int -> int) -> 'T [] -> 'T []
```
Example
```fsharp
let  printPermutation n array1 =
     let  length = Array.length array1
     if  (n > 0 && n < length)  then 
        Array.permute ( fun  index -> (index + n) % length) array1
     else 
        array1
    |> printfn  "%A"  
 let  array1 = [| 1 .. 5 |]
 // There are 5 valid permutations of array1, with n from 0 to 4.  
 for  n  in  0 .. 4  do 
    printPermutation n array1 
 ```
Output
```
[|1; 2; 3; 4; 5|]
[|5; 1; 2; 3; 4|]
[|4; 5; 1; 2; 3|]
[|3; 4; 5; 1; 2|]
[|2; 3; 4; 5; 1|] 
```

 
pick
--------------
Applies the supplied function to successive elements of a supplied array, returning the first result where the function returns  Some(x)  for some  x . If the function never returns  Some(x) ,  KeyNotFoundException  is raised.
```
: ('T -> 'U option) -> 'T [] -> 'U
```
Example
```fsharp
let  values = [| ( "a" , 1); ( "b" , 2); ( "c" , 3) |]

 let  resultPick = Array.pick ( fun  elem ->
                     match  elem  with 
                    | (value, 2) -> Some value
                    | _ -> None) values
printfn  "%A"  resultPick
 ```
Output
```
"b" 
```

 
reduce
--------------
Applies a function to each element of an array, threading an accumulator argument through the computation. If the input function is  f  and the array elements are  i0...iN , this function computes  f (...(f i0 i1)...) iN . If the array has size zero,  ArgumentException  is raised.
```
: ('T -> 'T -> 'T) -> 'T [] -> 'T
```
Example
```fsharp
let  names = [|  "A" ;  "man" ;  "landed" ;  "on" ;  "the" ;  "moon"  |]
 let  sentence = names |> Array.reduce ( fun  acc item -> acc +  " "  + item)
printfn  "sentence = %s"  sentence
 ```
Output
```
sentence = A man landed on the moon 
```

 
reduceBack
--------------
Applies a function to each element of an array, threading an accumulator argument through the computation. If the input function is  f  and the elements are  i0...iN , this function computes  f i0 (...(f iN-1 iN)) . If the array has size zero,  ArgumentException  is raised.
```
: ('T -> 'T -> 'T) -> 'T [] -> 'T
```
Example
```fsharp
// Computes ((1 - 2) - 3) - 4 = -8 
Array.reduce ( fun  elem acc -> elem - acc) [| 1; 2; 3; 4 |]
|> printfn  "%A"  
 // Computes 1 - (2 - (3 - 4)) = -2 
Array.reduceBack ( fun  elem acc -> elem - acc) [| 1; 2; 3; 4 |]
|> printfn  "%A" 
 ```
Output
```
-8
-2 
```

 
rev
--------------
Reverses the order of the elements in a supplied array.
```
: 'T [] -> 'T []
```
Example
```fsharp
let  stringReverse (s:  string ) =
    System.String(Array.rev (s.ToCharArray()))

printfn  "%A"  (stringReverse( "!dlrow olleH" ))
 ```
Output
```
"Hello world!" 
```

 
scan
--------------
Behaves like  fold , but returns the intermediate results together with the final results.
```
: ('State -> 'T -> 'State) -> 'State -> 'T [] -> 'State [])
```
Example
```fsharp
let  initialBalance = 1122.73
 let  transactions = [| -100.00; +450.34; -62.34; -127.00; -13.50; -12.92 |]
 let  balances =
    Array.scan ( fun  balance transactionAmount -> balance + transactionAmount) initialBalance transactions
printfn  "Initial balance:\n $%10.2f"  initialBalance
printfn  "Transaction   Balance"  
 for  i  in  0 .. Array.length transactions - 1  do 
    printfn  "$%10.2f $%10.2f"  transactions.[i] balances.[i]
printfn  "Final balance:\n $%10.2f"  balances.[ Array.length balances - 1]
 ```
Output
```
Initial balance:
 $   1122.73
Transaction   Balance
$   -100.00 $   1122.73
$    450.34 $   1022.73
$    -62.34 $   1473.07
$   -127.00 $   1410.73
$    -13.50 $   1283.73
$    -12.92 $   1270.23
Final balance:
 $   1257.31 
```

 
scanBack
--------------
Behaves like  foldBack , but returns the intermediary results together with the final results.
```
: ('T -> 'State -> 'State) -> 'T [] -> 'State -> 'State []
```
Example
```fsharp
// An array of functions that transform   
 // integers. (int -> int)  
 let  ops1 =
 [|  fun  x -> x + 1
     fun  x -> x + 2
     fun  x -> x - 5 |]

 let  ops2 =
 [|  fun  x -> x + 1
     fun  x -> x * 5
     fun  x -> x * x |]

 // Compare scan and scanBack, which apply the  
 // operations in the opposite order.  
 let  compareOpOrder ops x0 =
     let  xs1 = Array.scan ( fun  x op -> op x) x0 ops
     let  xs2 = Array.scanBack ( fun  op x -> op x) ops x0

     // Print the intermediate results  
     let  xs = Array.zip xs1 (Array.rev xs2)
     for  (x1, x2)  in  xs  do 
        printfn  "%10d %10d"  x1 x2
    printfn  "" 

compareOpOrder ops1 10
compareOpOrder ops2 10
 ```
Output
```
        10         10
        11          5
        13          7
         8          8

        10         10
        11        100
        55        500
      3025        501 
```

 
set
--------------
Sets an element of an array.
```
: 'T [] -> int -> 'T -> unit
```
Example
```fsharp
```
Output
```

module Array
 
```

 
sort
--------------
Sorts the elements of an array and returns a new array.  Operators.compare  is used to compare the elements.
```
: 'T[] -> 'T []
```
Example
```fsharp
```
Output
```

```

 
sortBy
--------------
Sorts the elements of an array by using the supplied function to transform the elements to the type on which the sort operation is based, and returns a new array.  Operators.compare  is used to compare the elements.
```
: ('T -> 'Key) -> 'T [] -> 'T []
```
Example
```fsharp
let  sortedArray2 = Array.sortBy ( fun  elem -> abs elem) [|1; 4; 8; -2; 5|]
printfn  "%A"  sortedArray2
 ```
Output
```
[|1; -2; 4; 5; 8|] 
```

 
sortInPlace
--------------
Sorts the elements of an array by changing the array in place, using the supplied comparison function.  Operators.compare  is used to compare the elements.
```
: 'T [] -> unit
```
Example
```fsharp
let  array1 = [|1; 4; 8; -2; 5|]
Array.sortInPlace array1
printfn  "%A"  array1
 ```
Output
```
[|-2; 1; 4; 5; 8|] 
```

 
sortInPlaceBy
--------------
Sorts the elements of an array by changing the array in place, using the supplied projection for the keys.  Operators.compare  is used to compare the elements.
```
: ('T -> 'Key) -> 'T [] -> unit
```
Example
```fsharp
let  array1 = [|1; 4; 8; -2; 5|]
Array.sortInPlaceBy ( fun  elem -> abs elem) array1
printfn  "%A"  array1
 ```
Output
```
[|1; -2; 4; 5; 8|] 
```

 
sortInPlaceWith
--------------
Sorts the elements of an array by using the supplied comparison function to change the array in place.
```
: ('T -> 'T -> int) -> 'T [] -> unit
```
Example
```fsharp
open  System

 let  array1 = [|  "<>" ;  "&" ;  "&&" ;  "&&&" ;  "<" ;  ">" ;  "|" ;  "||" ;  "|||"  |]
printfn  "Before sorting: " 
array1 |> printfn  "%A"  
 let  sortFunction (string1: string ) (string2: string ) =
     if  (string1.Length > string2.Length)  then 
       1
     else   if  (string1.Length < string2.Length)  then 
       -1
     else 
        String.Compare(string1, string2)
Array.sortInPlaceWith sortFunction array1
printfn  "After sorting: " 
array1 |> printfn  "%A" 
 ```
Output
```

```

 
sortWith
--------------
Sorts the elements of an array by using the supplied comparison function, and returns a new array.
```
: ('T -> 'T -> int) -> 'T [] -> 'T []
```
Example
```fsharp
open  System

 let  array1 = [|  "<>" ;  "&" ;  "&&" ;  "&&&" ;  "<" ;  ">" ;  "|" ;  "||" ;  "|||"  |]
printfn  "Before sorting: " 
array1 |> printfn  "%A"  
 let  sortFunction (string1: string ) (string2: string ) =
     if  (string1.Length > string2.Length)  then 
       1
     else   if  (string1.Length < string2.Length)  then 
       -1
     else 
        String.Compare(string1, string2)

Array.sortWith sortFunction array1
|> printfn  "After sorting: \n%A" 
 ```
Output
```

```

 
sub
--------------
Creates an array that contains the supplied subrange, which is specified by starting index and length.
```
: 'T [] -> int -> int -> 'T []
```
Example
```fsharp
```
Output
```

```

 
sum
--------------
Returns the sum of the elements in the array.
```
: 'T [] -> ^T
```
Example
```fsharp
[| 1 .. 10 |]
|> Array.sum
|> printfn  "Sum: %d" 
 ```
Output
```
55 
```

 
sumBy
--------------
Returns the sum of the results generated by applying a function to each element of an array.
```
: ('T -> ^U) -> 'T [] -> ^U
```
Example
```fsharp
[| 1 .. 10 |]
|> Array.sumBy ( fun  x -> x * x)
|> printfn  "Sum: %d" 
 ```
Output
```
385 
```

 
toList
--------------
Converts the supplied array to a list.
```
: 'T [] -> 'T list
```
Example
```fsharp
[| 1 .. 10 |]
|> Array.toList
|> List.rev
|> List.iter ( fun  elem -> printf  "%d "  elem)
printfn  "" 
 ```
Output
```
10 9 8 7 6 5 4 3 2 1 
```

 
tryFind
--------------
Returns the first element in the supplied array for which the supplied function returns  true . Returns  None  if no such element exists.
```
: ('T -> bool) -> 'T [] -> 'T option
```
Example
```fsharp
let  delta = 1.0e-10
 let  isPerfectSquare (x: int ) =
     let  y = sqrt ( float  x)
    abs(y - round y) < delta
 let  isPerfectCube (x: int ) =
     let  y = System.Math.Pow( float  x, 1.0/3.0)
    abs(y - round y) < delta
 let  lookForCubeAndSquare array1 =
     let  result = Array.tryFind ( fun  elem -> isPerfectSquare elem && isPerfectCube elem) array1
     match  result  with 
    | Some x -> printfn  "Found an element: %d"  x
    | None -> printfn  "Failed to find a matching element." 

lookForCubeAndSquare [| 1 .. 10 |]
lookForCubeAndSquare [| 100 .. 1000 |]
lookForCubeAndSquare [| 2 .. 50 |]
 ```
Output
```
Found an element: 1
Found an element: 729
Failed to find a matching element. 
```

 
tryFindIndex
--------------
Returns the index of the first element in an array that satisfies the supplied condition.
```
: ('T -> bool) -> 'T [] -> int option
```
Example
```fsharp
```
Output
```

// Signature:
Array.tryFindIndex : ('T -> bool) -> 'T [] -> int option

// Usage:
Array.tryFindIndex predicate array
 
```

 
tryPick
--------------
Applies the supplied function to successive elements of the supplied array, and returns the first result where the function returns  Some(x)  for some  x . If the function never returns  Some(x) ,  None  is returned.
```
: ('T -> 'U option) -> 'T [] -> 'U option
```
Example
```fsharp
let  findPerfectSquareAndCube array1 =
     let  delta = 1.0e-10
     let  isPerfectSquare (x: int ) =
         let  y = sqrt ( float  x)
        abs(y - round y) < delta
     let  isPerfectCube (x: int ) =
         let  y = System.Math.Pow( float  x, 1.0/3.0)
        abs(y - round y) < delta
     // intFunction : (float -> float) -> int -> int  
     // Allows the use of a floating point function with integers.  
     let  intFunction function1 number =  int  (round (function1 ( float  number)))
     let  cubeRoot x = System.Math.Pow(x, 1.0/3.0)
     // testElement: int -> (int * int * int) option  
     // Test an element to see whether it is a perfect square and a perfect  
     // cube, and, if so, return the element, square root, and cube root  
     // as an option value. Otherwise, return None.  
     let  testElement elem = 
         if  isPerfectSquare elem && isPerfectCube elem  then 
            Some(elem, intFunction sqrt elem, intFunction cubeRoot elem)
         else  None
     match  Array.tryPick testElement array1  with 
    | Some (n, sqrt, cuberoot) -> printfn  "Found an element %d with square root %d and cube root %d."  n sqrt cuberoot
    | None -> printfn  "Did not find an element that is both a perfect square and a perfect cube." 

findPerfectSquareAndCube [| 1 .. 10 |]
findPerfectSquareAndCube [| 2 .. 100 |]
findPerfectSquareAndCube [| 100 .. 1000 |]
findPerfectSquareAndCube [| 1000 .. 10000 |]
findPerfectSquareAndCube [| 2 .. 50 |]
 ```
Output
```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube. 
```

 
unzip
--------------
Splits an array of tuple pairs into a tuple of two arrays.
```
: ('T1 * 'T2) [] -> 'T1 [] * 'T2 []
```
Example
```fsharp
let  array1, array2 = Array.unzip [| (1, 2); (3, 4) |]
printfn  "%A"  array1
printfn  "%A"  array2
 ```
Output
```
[|1; 3|]
[|2; 4|] 
```

 
unzip3
--------------
Splits an array of tuples of three elements into a tuple of three arrays.
```
: ('T1 * 'T2 * 'T3) [] -> 'T1 [] * 'T2 [] * 'T3 []
```
Example
```fsharp
let  array1, array2, array3 = Array.unzip3 [| (1, 2,3 ); (3, 4, 5) |]
printfn  "%A"  array1
printfn  "%A"  array2
printfn  "%A"  array3
 ```
Output
```
[|1; 3|]
[|2; 4|]
[|3; 5|] 
```

 
zeroCreate
--------------
Creates an array whose elements are initially set to the default value  Unchecked.defaultof<'T> .
```
: int -> 'T []
```
Example
```fsharp
let  arrayOfTenZeroes :  int   array  = Array.zeroCreate 10
 ```
Output
```

 let  arrayOfTenZeroes :  int   array  = Array.zeroCreate 10
 
```

 
zip
--------------
Combines two arrays into an array of tuples that have two elements. The two arrays must have equal lengths; otherwise,  ArgumentException  is raised.
```
: 'T1 [] -> 'T2 [] -> ('T1 * 'T2) []
```
Example
```fsharp
let  array1, array2 = Array.unzip [| (1, 2); (3, 4) |]
printfn  "%A"  array1
printfn  "%A"  array2
 ```
Output
```
[|1; 3|]
[|2; 4|] 
```

 
zip3
--------------
Combines three arrays into an array of tuples that have three elements. The three arrays must have equal lengths; otherwise,  ArgumentException  is raised.
```
: 'T1 [] -> 'T2 [] -> 'T3 [] -> ('T1 * 'T2 * 'T3) []
```
Example
```fsharp
let  array1, array2, array3 = Array.unzip3 [| (1, 2,3 ); (3, 4, 5) |]
printfn  "%A"  array1
printfn  "%A"  array2
printfn  "%A"  array3
 ```
Output
```
[|1; 3|]
[|2; 4|]
[|3; 5|] 
```

 
 
