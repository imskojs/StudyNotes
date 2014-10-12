## Tricky(Draft)

`NaN` is a special "number"  
`null` and `undifined` are undefined values nothing to do with Number.

The rules for converting strings and numbers to Boolean values state that `0, NaN, ""` count as false. Every other numbers and characters are converted to `true`

`null` and `undefined` Boolean conversions yeild false except when compared to itself.

`NaN == NaN` is the only value that produces false when compared to itself. Even `null, undefined` produces true when compared to itself

`!` perator will convert all strings except "" to true

`||` will return the value to its left when that can be converted to true and will return the value on its right otherwise.  
```
	console.log(null || "user"); 	// user
	console.log("Karl" || "user");	// Karl
```

`&&` returns the value to its left when that can be converted to fase and will return the value on its right otherwise. (opposite of ||)

|| has the lowest precedence, then comes && then the comprison operator (>,==, and
so on) and then the rest

When `null` or `undefined` occurs on either side of the operator, it produces true
only if both sides are one of null or undefined.  
```
	console.log(null == undefined);		// true
	console.log(null == 0);				// false
```
When something that doesn't map to a number  in a obvious way (such as "five" or 
"undefined") is converted to a number the value `NaN` is produced.  
```
	console.log(NaN + NaN)		// NaN
```
Other wierd type conversions;  
```
	console.log(8 * null)		// 0
	console.log("5" - 1) 		// 4
	console.log("5" + 1)		// 51
	console.log("five" * 2)
```

Keywords and reserved words other than obvious ones;  
catch, finally, implements, protected, throw, try, with.

Variable names cannot contain `.` however they can contain `-` and `$` anywhere.  
Number cannot be the first letter of the variable name.

Side-effect: A statement that affects the world. It could be trivial thisngs like displaying something on the screen(Now I understand why we print "Hello World"), or it could change the internal state of the machine in a way that will affect the statement that come after it. These changes are called side effects. On the contrary following are the statement but are not side-effects;  
```
	1;
	!false;
```
As above statements have not changed the world, it didn't output anything to screen or anywhere, it didn't change the internal state such as memory as these values are discarded straight away.

Declarative funtion is good for use within a funtion. Declarative function can be located below the function call eventhough it is recommended to declare before use.
Function expression, f;
```
	var f = function(){
		console.log(a + 2);
	}
```
Function declaration, g;
```
	function g(a, b){
		return a * b;
	}
```

A pure function is a specific kind of value-producing function that not only has no side effects but also deosn't rely on side effects from other code. For example, it doesn't read global variables that are occasionally changed by other code.  Pure = purely value only. It has a property that when called with the same arguments, it always produces the same value.

Recursive functions are mostly used for situations where branching is required.  
(Understand what it is...Hard time tracing and implementing recursions)

Arrays don't need property name. It is automatically indexed with 0 to length-1 of the array.  
Objects need property name.

When a function is called a automatic variable named `arguments` is added to the environment in which the function body runs. It is an object that holds all of the arguments passed to the function. It is an Object and not an array however this object has property names like "0", "1", "2",...but cannot use any array methods.

Closure: usually objects, including functions used within a function, is not available outside of the outer most function. Closure is exception. Returning a function from a function complete with variables from an external scope, is called a closure. That is, contents that is stored inside of the inner function will be available to the outside of the outermost function(global environment).
 A closure wraps(and freezes) up an entire environment, binding necessary variables from other scopes. For example;  
```
    function testClosure() {
        var x = 4;
        function closeX() {
            return x;
        }
        return closeX;
    }
    var checkLocalX = testClosure();
    checkLocalX(); /* or */ testClosure()();
```
Closures are like exception to the lexical scoping rule. Take below Example;  
```
    function vary() {
        var i = 0;
        return function(){
            i += 1;
            console.log("I can see i = " + i + 
            " and this gets incremented everytime it is invoked outside");
        }
    }
    vary()();   // --> 1
    vary()();   // --> 1
    vary()();   // --> 1  
```
but...  
```
    x = vary();
    x();    // --> 1
    x();    // --> 2
    x();    // --> 3
```

Objects do not have a lenght. Object.length = undefined.

A class is a set of Objects that all share the same property(key only not the value) and inherit from the same basic prototype.

A constructor: A maker of a Class of Objects. eg)  
```
    function Shoe(a, b, c) {
        this.prop1 = a;
        this.prop2 = b;
        this.prop3 = c;
        this.autoprop1 = function() { alert("Shoe's on!");}
        this.autoprop2 = function() { alert("abc");}
    }
```
    or;
```
    Shoe.prototype = {
        autoprop1 : function() { alert("Shoe's on!");},
        autoprop2 : function() { alert("abc");}
    }
```
Above is just a function. But when called with `new` it becomes a constructor.  
`new` keyword builds a new instance.

`this` refers to calling object not the owner.

Portotype of Object.prototype is null.

Default output in nodejs does not print > 2 nested Objects, use below code to override.
```
    var util = require('util');
    console.log(util.inspect(output, {showHidden: false, depth: null}));
```  

Positive index starts at 0,
Counting number starts at 1,
Negative index starts at 1 from the back.

In looping over properties with `for(var i in object0)`, numericy(character that can coerce to number... what's the proper name?) are moved in front of string type property names. These numericies are ordered in ascending order. String type property names are not ordered, that is, they stay as is behind these moved numericies.

Arrays can easily be converted to Objects by changing their index number to property names. Hence Arrays can
be treated like Objects but Objects cannot be treated like Arrays.  
In functions if objects are passed as arguments then arrays can be passed as argumets as well, Array will simply be convert to an object before use, if not... why not?

index number is front inclusive, end exclusive.  
```
|0|1|2|3|4|5|
 A B C D E F

"ABCDEF".slice(1,3)
```
slices indexes that is in "front of beginning" of index number 1 and indexes that are "behind the beginning" of index number 3
```
|0|1|2|3|4|5|
 A B C D E F
--^   ^------
```

