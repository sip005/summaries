# The Principles Of Object Oriented JavaScript  

## Chapter - One: Primitive and Reference Types

- [1.0.0 Primitive and Reference Types](#100-primitive-and-reference-types)
- [1.1.0 What Are Types?](#110-what-are-types)
- [1.2.0 Primitive Types](#120-primitive-types)
  - [1.2.1 Identifying Primitive Types](#121-identifying-primitive-types)
  - [1.2.2 Primitive Methods](#122-primitive-methods)
- [1.3.0 Reference Types](#130-reference-types)
  - [1.3.1 Creating Objects](#131-creating-objects)
  - [1.3.2 Dereferencing Objects](#132-dereferencing-objects)
  - [1.3.3 Adding or Removing Properties](#133-adding-or-removing-properties)
- [1.4.0 Instantiating Built-in Types](#140-instantiating-built-in-types)
  - [1.4.1 Literal Forms](#141-literal-forms)
  - [1.4.2 Object and Array Literals](#142-object-and-array-literals)
  - [1.4.3 Function Literals](#143-function-literals)
  - [1.4.4 Regular Expression Literals](#144-regular-expression-literals)
- [1.5.0 Property Access](#150-property-access)
- [1.6.0 Identifying Reference Types](#160-identifying-reference-types)
- [1.7.0 Identifying Arrays](#170-identifying-arrays)
- [1.8.0 Primitive Wrapper Types](#180-primitive-wrapper-types)
- [1.9.0 Summary](#190-summary)

### 1.0.0 Primitive and Reference Types  

JavaScript does not have formal support for classes. Instead of defining classes from the begining we can just write codes and create data structure as we need them. Because it lacks classes, also it lacks class grouping such as packages.  
Whereas in languages like Java, package and class names define both the types of objects we use and the layout of files and folders in our project, programming in JavaScript is like starting with a blank slate.  
To ease the transition from traditional object-oriented languages, JavaScript makes objects the central part of the language. Almost all data in JavaScript is either an object or accessed through objects. In fact, even functions (which languages traditionally make us jump through hoops to get references to) are represented as objects in JavaScript, which makes them `first-class functions`.

#### 1.1.0 What Are Types?  

Although JavaScript has no concept of classes, it still uses two kinds of types:  
`primitive and reference`.  

1. Primitive types are stored as simple data types.  
2. Reference types are stored as objects, which are really just references to locations in memory.  

The tricky thing is that JavaScript lets us treat primitive types like reference types in order to make the language more consistent for the developer.  
While other programming languages distinguish between primitive and reference types by storing primitives on the stack and references in the heap, JavaScript does away with this concept completely: It tracks variables for a particular scope with a variable object. Primitive values are stored directly on the variable object, while reference values are placed as a pointer in the variable object, which serves as a reference to a location in memory where the object is stored. However, as we’ll see later, primitive values and reference values behave quite differently although they may initially seem the same. Of course, there are other differences between primitive and reference types.

#### 1.2.0 Primitive Types  

Primitive types represent simple pieces of data that are stored as is  

**Boolean** -  true or false  
**Number** -  Any integer or floating-point numeric value  
**String** -  A character or sequence of characters delimited by either single or double quotes (JavaScript has no separate character type)  
**Null** - A primitive type that has only one value, null  
**Undefined** - A primitive type that has only one value, undefined (undefined is the value assigned to a variable that is not initialized)  

The first three types (Boolean, number, and string) behave in similar ways, while the last two (null and undefined) work a bit differently.  

All primitive types have literal representations of their values. Literals represent values that aren’t stored in a variable, such as a hardcoded name or price. Here are some examples of each type using its literal form:  

```js
// strings
var name = "Nicholas";
var selection = "a";
// numbers
var count = 25;
var cost = 1.51;
// boolean
var found = true;
// null
var object = null;
// undefined
var flag = undefined;
var ref; // assigned undefined automatically
```  

In JavaScript, as in many other languages, a variable holding a primitive directly contains the primitive value (rather than a pointer to an object). When you assign a primitive value to a variable, the value is copied into that variable. This means that if you set one variable equal to another, each variable gets its own copy of the data. For example:  

```js
var color1 = "red";
var color2 = color1;
```  

Here, color1 is assigned the value of "red". The variable color2 is then assigned the value color1, which stores "red" in color2. Even though color1 and color2 contain the same value, they are completely separate from each other, and we can change the value in color1 without affecting color2 and vice versa. That’s because there are two different storage locations, one for each variable.  

Because each variable containing a primitive value uses its own storage space, changes to one variable are not reflected on the other. For example:  

```js
var color1 = "red";
var color2 = color1;
console.log(color1); // "red"
console.log(color2); // "red"
color1 = "blue";
console.log(color1); // "blue"
console.log(color2); // "red"
```  

In this code, color1 is changed to "blue" and color2 retains its original value of "red".

##### 1.2.1 Identifying Primitive Types  

The best way to identify primitive types is with the typeof operator, which works on any variable and returns a string indicating the type of data. The typeof operator works well with strings, numbers, Booleans, and undefined. The following shows the output when using typeof on different primitive values:  

```js
console.log(typeof "Nicholas"); // "string"
console.log(typeof 10); // "number"
console.log(typeof 5.1); // "number"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"
// Exception
console.log(typeof null); // "object"
```  

The tricky part involves null. The best way to determine if a value is null is to compare it against
null directly, like this:  

```js
console.log(value === null); // true or false
```  

**Notice** that this code uses the triple equals operator `(===)` instead of the double equals operator. The reason is that triple equals does the comparison without coercing the variable to another type. To understand why this is important, consider the following:  

```js
console.log("5" == 5); // true
console.log("5" === 5); // false
console.log(undefined == null); // true
console.log(undefined === null); // false
```  

When you use the double equals, the string `"5"` and the number `5` are considered equal because the double equals converts the string into a number before it makes the comparison. The triple equals operator doesn’t consider these values equal because they are two different types. Likewise, when you compare `undefined` and `null`, the double equals says that they are equivalent, while the triple equals says they are not. When you’re trying to identify null, use triple equals so that you can correctly identify the type.  

##### 1.2.2 Primitive Methods  

Despite the fact that they’re primitive types, strings, numbers, and Booleans actually have methods. `(The null and undefined types have no methods.)` Strings, in particular, have numerous methods to help you work with them. For example:  

```js
var name = "Nicholas";
var lowercaseName = name.toLowerCase(); // convert to lowercase
var firstLetter = name.charAt(0); // get first character
var middleOfName = name.substring(2, 5); // get characters 2-4
var count = 10;
var fixedCount = count.toFixed(2); // convert to "10.00"
var hexCount = count.toString(16); // convert to "a"
var flag = true;
var stringFlag = flag.toString(); // convert to "true"
```  

*Despite the fact that they have methods, primitive values themselves are not objects. JavaScript makes them look like objects to provide a consistent experience in the language, as we’ll see later in this chapter.*  

#### 1.3.0 Reference Types  

Reference types represent objects in JavaScript and are the closest things to classes that you will find in the language. Reference values are instances of reference types and are synonymous with objects (the rest of this chapter refers to reference values simply as objects). An object is an unordered list of properties consisting of a name (always a string) and a value. When the value of a property is a function, it is called a method. Functions themselves are actually reference values in JavaScript, so there’s little difference between a property that contains an array and one that contains a function except that a function can be executed. Of course, you must create objects before you can begin working with them.

##### 1.3.1 Creating Objects  

It sometimes helps to think of JavaScript objects as nothing more than hash tables. There are a couple of ways to create, or instantiate, objects. The first is to use the new operator with a constructor. (A constructor is simply a function that uses new to create an object—any function can be a constructor.) By convention, constructors in JavaScript begin with a capital letter to distinguish them from nonconstructor functions. For example, this code instantiates a generic object and stores a reference to it in object:  

```js
var object = new Object();
```  

Reference types do not store the object directly into the variable to which it is assigned, so the object variable in this example doesn’t actually contain the object instance. Instead, it holds a pointer (or reference) to the location in memory where the object exists. This is the primary difference between objects and primitive values, as the primitive is stored directly in the variable. When you assign an object to a variable, you’re actually assigning a pointer. That means if you assign one variable to another, each variable gets a copy of the pointer, and both still reference the same object in memory. For example:  

```js
var object1 = new Object();
var object2 = object1;
```  

This code first creates an object (with new) and stores a reference in object1. Next, object2 is assigned the value of object1. There is still only the one instance of the object that was created on the first line, but both variables now point to that object.  

##### 1.3.2 Dereferencing Objects  

JavaScript is a garbage-collected language, so you don’t really need to worry about memory allocations when you use reference types. However, it’s best to dereference objects that you no longer need so that the garbage collector can free up that memory. The best way to do this is to set the object variable to null.  

```js
var object1 = new Object();
// do something
object1 = null; // dereference
```  

Here, object1 is created and used before finally being set to null. When there are no more references to an object in memory, the garbage collector can use that memory for something else. (Dereferencing objects is especially important in very large applications that use millions of objects.)  

##### 1.3.3 Adding or Removing Properties  

Another interesting aspect of objects in JavaScript is that you can add and remove properties at any time. For example:  

```js
var object1 = new Object();
var object2 = object1;
object1.myCustomProperty = "Awesome!";
console.log(object2.myCustomProperty); // "Awesome!"
```  

Here, myCustomProperty is added to object1 with a value of "Awesome!". That property is also accessible on object2 because both object1 and object2 point to the same object.  

*This example demonstrates one particularly unique aspect of JavaScript: You can modify objects whenever you want, even if you didn’t define them in the first place. And there are ways to prevent such modifications, as you’ll learn later.*  

**In addition to generic object reference types, JavaScript has several other built-in types that are at your disposal.**

#### 1.4.0 Instantiating Built-in Types  

You’ve seen how to create and interact with generic objects created with `new Object()`. The Object type is just one of a handful of built-in reference types that JavaScript provides. The other built-in types are more specialized in their intended usage and can be instantiated at any time. The built-in types are:  

**Array** An ordered list of numerically indexed values  
**Date** A date and time  
**Error** A runtime error (there are also several more specific error subtypes)  
**Function** A function  
**Object** A generic object  
**RegExp** A regular expression  

You can instantiate each built-in reference type using new, as shown here:  

```js
var items = new Array();
var now = new Date();
var error = new Error("Something bad happened.");
var func = new Function("console.log('Hi');");
var object = new Object();
var re = new RegExp("\\d+");
```  

##### 1.4.1 Literal Forms  

Several built-in reference types have literal forms. A literal is syntax that allows you to define a reference value without explicitly creating an object, using the new operator and the object’s constructor.  

##### 1.4.2 Object and Array Literals  

To create an object with object literal syntax, you can define the properties of a new object inside braces. Properties are made up of an identifier or string, a colon, and a value, with multiple properties separated by commas. For example:  

```js
var book = {
  name: "The Principles of Object-Oriented JavaScript",
  year: 2014
};
```  

You can also use string literals as property names, which is useful when you want a property name to have spaces or other special characters:  

```js
var book = {
"name": "The Principles of Object-Oriented JavaScript",
"year": 2014
};
```  

This example is equivalent to the previous one despite the syntactic differences. Both examples are also logically equivalent to the following:  

```js
var book = new Object();
book.name = "The Principles of Object-Oriented JavaScript";
book.year = 2014;
```  

The outcome of each of the previous three examples is the same:  
*an object with two properties. The choice of pattern is up to you because the functionality is ultimately the same.*  

**Using an object literal doesn’t actually call new Object(). Instead, the JavaScript engine follows the same steps it does when using new Object() without actually calling the constructor. This is true for all reference literals.**  

You can define an array literal in a similar way by enclosing any number of comma-separated values inside square brackets. For example:  

```js
var colors = [ "red", "blue", "green" ];
console.log(colors[0]); // "red"
```  

This code is equivalent to the following:  

```js
var colors = new Array("red", "blue", "green")
console.log(colors[0]); // "red"
```  

##### 1.4.3 Function Literals  

You almost always define functions using their literal form. In fact, using the `Function` constructor is typically discouraged given the challenges of maintaining, reading, and debugging a string of code rather than actual code, so you’ll rarely see it in code.  

Creating functions is much easier and less error prone when you use the literal form. For example:  

```js
function reflect(value) {
return value;
}
// is the same as
var reflect = new Function("value", "return value;");
```  

This code defines the `reflect()` function, which returns any value passed to it. Even in the case of this simple function, the literal form is easier to write and understand than the constructor form.  

Further, there is no good way to debug functions that are created in the constructor form:  

These functions aren’t recognized by JavaScript debuggers and therefore act as a black box in your application.  

##### 1.4.4 Regular Expression Literals  

JavaScript also has regular expression literals that allow you to define regular expressions without using the `RegExp` constructor. Regular expression literals look very similar to regular expressions in Perl: The pattern is contained between two slashes, and any additional options are single characters following the second slash. For example:  

```js
var numbers = /\d+/g;
// is the same as
var numbers = new RegExp("\\d+", "g");
```  

The literal form of regular expressions in JavaScript is a bit easier to deal with than the constructor form because you don’t need to worry about escaping characters within strings. When using the RegExp constructor, you pass the pattern in as a string, so you have to escape any backslashes. (That’s why `\d` is used in the literal and `\\d` is used in the constructor.) Regular expression literals are preferred over the constructor form in JavaScript except when the regular expression is being constructed dynamically from one or more strings. That said, with the exception of Function, there really isn’t any right or wrong way to instantiate built-in types. Many developers prefer literals, while some prefer constructors. Choose whichever method you find more comfortable to use.

#### 1.5.0 Property Access  

Properties are name/value pairs that are stored on an object. Dot notation is the most common way to access properties in JavaScript (as in many object-oriented languages), but you can also access properties on JavaScript objects by using bracket notation with a string. For example, you could write this code, which uses dot notation:  

```js
var array = [];
array.push(12345);
```  

With bracket notation, the name of the method is now included in a string enclosed by square brackets, as in this example:  

```js
var array = [];
array["push"](12345);
```  

This syntax is very useful when you want to dynamically decide which property to access. For example, here bracket notation allows you to use a variable instead of the string literal to specify the property to access.  

```js
var array = [];
var method = "push";
array[method](12345);
```  

In this listing, the variable method has a value of `"push"`, so `push()` is called on the array. This capability is quite useful. The point to remember is that, other than syntax, the only difference—performance or otherwise—between dot notation and bracket notation is that bracket notation allows you to use special characters in property names. Developers tend to find dot notation easier to read, so you’ll see it used more frequently than bracket notation.  

#### 1.6.0 Identifying Reference Types  

A function is the easiest reference type to identify because when you use the typeof operator on a function, the operator should return `"function"`:  

```js
function reflect(value) {
return value;
}
console.log(typeof reflect); // "function"
```  

Other reference types are trickier to identify because, for all reference types other than functions, typeof returns `"object"`. That’s not very helpful when you’re dealing with a lot of different types. To identify reference types more easily, you can use JavaScript’s `instanceof` operator. The `instanceof` operator takes an object and a constructor as parameters. When the value is an instance of the type that the constructor specifies, instanceof returns true; otherwise, it returns false, as you can see here:  

```js
var items = [];
var object = {};
function reflect(value) {
return value;
}
console.log(items instanceof Array); // true
console.log(object instanceof Object); // true
console.log(reflect instanceof Function); // true
```  

In this example, several values are tested using instanceof and a constructor. Each reference type is correctly identified by using `instanceof` and the constructor that represents its true type (even though the constructor wasn’t used in creating the variable). The instanceof operator can identify inherited types. That means every object is actually an instance of Object because every reference type inherits from `Object`. To demonstrate, the following listing examines the three references previously created with `instanceof`:  

```js
var items = [];
var object = {};
function reflect(value) {
return value;
}
console.log(items instanceof Array); // true
console.log(items instanceof Object); // true
console.log(object instanceof Object); // true
console.log(object instanceof Array); // false
console.log(reflect instanceof Function); // true
console.log(reflect instanceof Object); // true
```  

Each reference type is correctly identified as an instance of Object, from which all reference types inherit.

#### 1.7.0 Identifying Arrays  

Although instanceof can identify arrays, there is one exception that affects web developers: JavaScript values can be passed back and forth between frames in the same web page. This becomes a problem only when you try to identify the type of a reference value, because each web page has its own global context—its own version of Object, Array, and all other builtin types. As a result, when you pass an array from one frame to another, instanceof doesn’t work because the array is actually an instance of Array from a different frame. To solve this problem, `ECMAScript 5` introduced `Array.isArray()`, which definitively identifies the value as an instance of Array regardless of the value’s origin. This method should return true when it receives a value that is a native array from any context. If your environment is `ECMAScript 5` compliant, `Array.isArray()` is the best way to identify arrays:  

```js
var items = [];
console.log(Array.isArray(items)); // true
```  

The Array.isArray() method is supported in most environments, both in browsers and in Node.js. This method isn’t supported in Internet Explorer 8 and earlier.

#### 1.8.0 Primitive Wrapper Types

#### 1.9.0 Summary
