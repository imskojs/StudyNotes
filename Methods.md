If a method is changing the content then it returns things other than content changed object.  
If a method is not changing the content but rather change the form, and orders than the method returns reformed or ordered object.


# Array methods;

Array methods are focused on manipulating.  
slice = copy, pop = cut, shift = cut, splice = cut/paste

Example arrays 

    //Caller Array
    var a0 = ['a', 'b', 'c', 1, 2, 3, [10,11,12, [1,2,3]], {1: "dick", 2: [1,1]}];

    //Array input into method
    var ia0 = ['A', 'B', 'C', 9, 8, 7, [101, 102, [103, 104]], {1: "a"}];


## Methods returning elements(subset of array);

### Array.pop();  

Delete last element and pop it to output.

    var output0 = a0.pop();
    // output = { '1': 'dick', '2': [ 1, 1 ] }

    var output1 = a0;
    // output1 = ['a', 'b', 'c', 1, 2, 3, [10,11,12, [1,2,3]]]


### Array.shift();

    var output0 = a0.shift();  
    // output0 = 'a'

    var output1 = a0;
    // output1 =
        [ 'b',
          'c',
          1,
          2,
          3,
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          { '1': 'dick', '2': [ 1, 1 ] } ]


### Array.slice(begin, end);

slice = copy;  caller is not affected.

    var output = a0.slice(-3);
    // output =
    [ 3,
      [ 10, 11, 12, [ 1, 2, 3 ] ],
      { '1': 'dick', '2': [ 1, 1 ] } ]

    var output = a0.slice(0,1);
    // output = [ 'a' ]


### Array.splice(startRemoveIndex, howManyToRemove, elementToInsert1, ..., elementToInsert2)

Returns removed part.  
`howManyToRemove` is counting number not index number.

    var output0 = a0.splice(0,2, "Removed2_Inserted1");
    // output0 = [ 'a', 'b' ]

    // a0 = 
        [ 'Removed2_Inserted1',
          'c',
          1,
          2,
          3,
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          { '1': 'dick', '2': [ 1, 1 ] } ]

    // Assume a0 is reset.

    var output1 = a0.splice(2,0, "Removed0_Inserted1", "Removed0_Inserted2");
    // output1 = []

    // a0 =
        [ 'a',
          'b',
          'Removed0_Inserted1',
          'Removed0_Inserted2',
          'c',
          1,
          2,
          3,
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          { '1': 'dick', '2': [ 1, 1 ] } ]



## Methods returning strings;

### Array.join([sep = ',']);  
nested arrays are converted, nested Object is not converted.

    var output = a0.join();
    // output = a,b,c,1,2,3,10,11,12,1,2,3,[object Object]


## Methods returning Boolean;


## Methods returning Array;

### Array.reverse();

    var output = a0.reverse();

    output =
        [ { '1': 'dick', '2': [ 1, 1 ] },
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          3,
          2,
          1,
          'c',
          'b',
          'a' ]

## Methods returning Number;

### Array.push(element1, ..., elementN);

Result is the pushed.length.

    var output0 = a0.push(ia0);
    // output0 = 9

    var output1 = a0;
    // output1 =
        [ 'a',
          'b',
          'c',
          1,
          2,
          3,
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          { '1': 'dick', '2': [ 1, 1 ] },
          [ 'A', 'B', 'C', 9, 8, 7, [ 101, 102, [ 103, 104 ] ], { '1': 'a' } ] ]


### Array.unshift(element1, ..., elementN);

    var output0 = a0.unshift("shifted1", {"shifted2": 2});
    // output0 = 10

    var output1 = a0;
    // output1 =
        [ 'shifted1',
          { shifted2: 2 },
          'a',
          'b',
          'c',
          1,
          2,
          3,
          [ 10, 11, 12, [ 1, 2, 3 ] ],
          { '1': 'dick', '2': [ 1, 1 ] } ]

### Array.length  (yeah, it's not a method)

    var output = a0.length;
    // output = 8

# Object Methods;

## Methods returning arrays;

### Object.keys(object)

Returns an array of `object`'s enumerable property names.
Same order as for(var i in object) loop.
It's a call method.

    var o0 = {0: "value1", 2: "value3", z: "value4", a: "value5", 1: "value2"};

    var output = Object.keys(o0);
    // output = [ '0', '1', '2', 'z', 'a' ]


# String Methods;

It seems string methods are more focused on the searching ability

Example

    var s0 = "apple";
    var s1 = "banana";
    var s2 = "tree"
    var s3 = "Apple banana trees on the beach.";

## Methods returning a character.

### String.charAt(index)

    var output = s0.charAt(9999);
    // output = ''


## Methods returning a String.

### String.concat(string1, ..., stringN)

Do not use concat. Use assignment operator as it has better performance.

    var output = s0.concat(s1, s2);
    // output = 'applebananatree'


### String.slice(beginSlice, endSlice)

If beginSlice is negative then beginSlice = String.leng + beginSlice.  
The same goes for endSlice.  

    var output = s1.slice(2, -1);
    // output = 'nan'

### String.sub()

Return caller string with sub element surrounded

    var output = s0.sub();
    // output = '<sub>apple</sub>'

### String.substring(start, countNumber)

If `start` is negative `start = String.length + start`.
If `start` is negative, and `abs(start) > String.length` then `start = 0`
If `countNumber` is negative (or 0) it returns empty string, `''`

    var output = s3.substr(-6, 6);
    // output = 'beach.'

### String.toUpperCase()

    var output = s0.toUpperCase();
    // output = 'APPLE'

### String.toLowerCase()

    var output = s0.toLowerCase();
    // output = 'apple'

## Methods returning a number.

### String.indexOf(searchString, fromIndex)

If "" is searched >=String.length then length of the string will be returned.  
Else if characters other than "" is searched in >= String.length -1 returned.

    var output = s3.indexOf("tre", 4);  
    // output = 13  

### String.length

    var output = s3.length;
    // output = 32

### String.search(RegExpObject);

Versatile version of String.indexOf() method.  LEARN RegEx.

## Methods returning an array.

### String.split(seperator, uptoCountNumber)

    var output = s3.split(" ", 2);
    // output = [ 'Apple', 'banana' ]

