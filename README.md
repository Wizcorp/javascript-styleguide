# Style Guide

## What exactly is a style guide?

Before we begin, let us remind ourselves exactly what a code style guide is:

A style guide or style manual is a set of standards for the writing and design of code. The implementation of a style guide provides uniformity in code style and formatting, often covering guidelines regarding indentation, variable and function naming conventions, where best to apply whitespace and so on.


## Why is consistent code style important?

They say that good code is it's own documentation. We don't completely agree with this (docs are important!), the fact is, the more readable our source code is, the easier it is to maintain.

Following a consistent style guide both helps enforce this concept and improves the overall quality of the code we write. This facilitates other developers stepping in to assist with maintenance more easily and can certainly save time in the long haul.

Readable source code is arguably easier to understand as well. It's easier to browse, locate and fix bugs in and easier to optimize. It can also give us a clearer picture of how the code fits into a larger body of work.

Consistently styled code can:
- Reduce the lead time required to understand an implementation
- Make it easier to establish what code can be reused
- Clarify how updates to an implementation should be styled or structured (remember that consistent code, even when written by a team, should look like one person wrote it).


## Indentation
One of the most religious talk. Let's cut it out, at we use **tabs** for our projects. Tabs should be use for indentation only, meaning strictly only at the beginning of lines.


## Semicolons
It's true that JavaScript is so awesome that you don't have tu use them, but don't make this mistake and **use those semicolons**!


## Line length
Limit your lines to **120 characters**. We are not living in the 90's anymore our screen got a lot bigger, but at the same time our brains are the same, so let's not go too far, readability come first.


## Quotes
The use of **single quotes** only is highly recommended, but we won't stop you if you need to use double quotes in some specific cases.
```javascript
myButton.on('tap', function() {
	alert("You tapped me");
});
```
>Note: in this example single quotes are used for keys while double quotes are used for text


## Whitespace

* Conventional operators SHOULD be surrounded by a space (including ternary operators).

* Commas SHOULD be followed by a space.

* Colons SHOULD be followed by a space.

* Semi-colons in for statements SHOULD be followed by a space.

* Semi-colons SHOULD NOT be preceded by a space.

* Function calls and method calls SHOULD NOT be followed by a space. Example: `doSomething(someParameter); // NOT doSomething (someParameter)`

* Logical units within a block SHOULD be separated by one blank line.

* Curly braces SHOULD have inner spaces.


## Braces
Always start your curly braces on the same line as whatever they're opening.
```javascript
if (time < 60) {
	console.log('less than a minute');
} else {
	console.log('a minute or more');
}
```

##Naming
All names SHOULD be written in English, American English.
### In general:
##### Variable and Property names
Should use lower camel case capitalization. They should also be descriptive. Single character variables and uncommon abbreviations should generally be avoided.
```javascript
var myName = 'John';
```
##### Function and Method names
Should use lower camel case capitalization. They should also be descriptive. Single character variables and uncommon abbreviations should generally be avoided. Should be verbs or verb phrases.
```javascript
function getMaxLevel() {
	return 5;
}

obj.getSomeValue();
```
##### Class names
Should be capitalized using upper camel case. They should be nouns.
```javascript
function Button() {
}
```
##### Constants and Enum
Should be declared as regular variables or static class properties, using all uppercase letters.
```javascript
var MAX_LEVEL = 5;
var playerAttribute = {
	EARTH : 1,
	WATER: 2,
	FIRE: 3
};
````
### Extra rules

##### Abbreviations and acronyms
Should be avoided, and existing ones should not be uppercase when used as a name:
```javascript
getInnerHtml(), getXml(), XmlDocument
```

##### Private variable
When exposed, should be prepended with a "_" (underscore) char:
```javascript
this._somePrivateVariable = statement;
```

#####Specific Naming Conventions


- The "is" prefix SHOULD be used for boolean variables and methods. Alternatives include "has", "can" and "should"

- The terms "initialize" or "init" CAN be used where an object or a concept is established.

- UI Control variables SHOULD be suffixed by the control type. Examples: leftComboBox, topScrollPane

- Plural form MUST be used to name collections.

- A "num" prefix or "count" postfix SHOULD be used for variables representing a number of objects.

- Iterator variables SHOULD be called "i", "j", "k", etc.

- Complement names MUST be used for complement entities. Examples: get/set, add/remove, create/destroy, start/stop, insert/delete, begin/end, etc.

- Negated boolean variable names MUST be avoided:
```javascript
	var isNotError, isNotFound; // WRONG.
```

- Methods returning an object MAY be named after what they return, and methods returning void after what they do.


##Variable declarations
Declare one variable per var statement, it makes it easier to re-order the lines, and put declarations wherever they make sense.
Idealy, variables should be initialized where they are declared and they must be declared in the smallest scope possible. A null initialization is acceptable.


### Loop
Only loop control statements MUST be included in the "for" loop construction.

Loop variables should be initialized immediately before the loop; loop variables in a "for" statement may be initialized in the "for" loop construction.

The use of "break" and "continue" is not discouraged.

### Conditionals
Complex conditional expressions SHOULD be avoided; use temporary boolean variables instead with proper naming.

The nominal case should be put in the "if" part and the exception in the "else" part of an "if" statement.

Executable statements in conditionals MUST be avoided.

### Miscellaneous
The use of magic numbers in the code should be avoided; they should be declared using named **constants** instead.


## Object and Array creation
Use trailing commas and put short declarations on a single line. Only quote keys when your interpreter complains.
```javascript
var a = ['hello', 'world'];
var b = {
	good: 'code',
	'is generally': 'pretty'
};
var c = { short: true };
```

## Equality operator
Programming is not about remembering [stupid rules](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Operators/Comparison_Operators). Use the triple equality operator as it will work just as expected.
```javascript
var a = 0;
if (a === '') {
	console.log('winning');
}
```

## Extending prototypes
Do not extend the prototypes of any objects, especially native ones.

## Conditions
Any non-trivial conditions should be assigned to a descriptive variable
```
var isAuthorized = (user.isAdmin() || user.isModerator());
if (isAuthorized) {
	console.log('winning');
}
```

## Return statement
To avoid deep nesting of if-statements, always return a functions value as early as possible.

```
function isPercentage(val) {
	if (val < 0) {
		return false;
	}

	if (val > 100) {
		return false;
	}

	return true;
}

```

## Inheritance / Object oriented programming
Object oriented programming is a fairly well-understood approach to write maintainable Software. Even so JavaScript does not explicitly favor OOP, it makes it easy enough to use it.

```
(function () {

	// Helper function for inheritance

	function inherits(child, parent) {
		child.prototype = Object.create(parent.prototype, {
			constructor: { value: child, enumerable: false, writable: true, configurable: true }
		});
	};


	// SuperClass definition

	function SuperClass () {
		this.x = 0;
		this.y = 0;
	}

	SuperClass.prototype.move = function (params) {
		params = params || {};
		this.x += params.x || 0;
		this.y += params.y || 0;
	};


	//Class definition

	function Class(params) {
		SuperClass.call(this);
		
		params = params || {};

		this.width = params.width || 0;
		this.height = params.height || 0;

		if (params.x || params.y) {
			SuperClass.prototype.move.call(this, params);
		}
	}

	inherits(Class, SuperClass);

	Class.prototype.resize = function (width, height) {
		if (width) {
			this.width = width;
		}
		
		if (height) {
			this.height = height;
		}
	};


	// SubClass definition

	function SubClass(params) {

		// Set a custom value
		params.height = params.width * 2 || 10;

		Class.call(this, params);
		this.o = {};
	}

	inherits(SubClass, Class);

	// Overrid of the parent method
	SubClass.prototype.resize = function (params) {
		Class.prototype.resize.call(this, { width: params.width, height: params.height + 50 });
	}


	// Code

	var myObject = new SubClass({ x: 10, width: 25 });
	console.log(myObject);
	
	myObject.resize({ width: 10, height: 10 });
	console.log(myObject);

})();
```

## Comments

Comments are the documentation of your code; therefore **tricky code should not be commented but rewritten**. 

All comments should be written in English and be politically correct, even those are supposed to be temporary.

Comments should be indented relative to their position in the code, preceding or to the right of the code in question.

Even if everybody likes commented code, do not comment every single line of code; you will kill the readability of it.

Try to put comment at the top of a block of code to explain the point of it. And do not comment at the end of line of code, or only for declaration of variables (see JSDoc).

## JSDoc
If you need to learn more about JSDoc and its tags you can visit the official [wiki](https://code.google.com/p/jsdoc-toolkit/w/list).


### Comment Syntax
The JSDoc syntax is based on JavaDoc . Many tools extract metadata from JSDoc comments to perform code validation and optimizations. These comments must be well-formed.
```
/**
 * A JSDoc comment should begin with a slash and 2 asterisks.
 * Inline tags should be enclosed in braces like {@code this}.
 * @desc Block tags should always start on their own line.
 */
```

### Class Comments
Classes must be documented with a description and a type tag that identifies the constructor.
```
/**
 * Class making something fun and easy.
 * @param {string} arg1 An argument that makes this more interesting.
 * @param {Array.<number>} arg2 List of numbers to be processed.
 * @constructor
 */
function MyClass(arg1, arg2) {
	// ...
};
```

### Method and Function Comments
Parameter and return types should be documented. The method description may be omitted if it is obvious from the parameter or return type descriptions. Method descriptions should start with a sentence written in the third person declarative voice.
```
/**
 * Operates on an instance of MyClass and returns something.
 * @param {MyClass} obj Instance of MyClass which leads to a long
 *     comment that needs to be wrapped to two lines.
 * @return {boolean} Whether something occured.
 */
function someMethod(obj) {
	// ...
}
```
### Property Comments
```
/** @constructor */
function MyClass() {
	/**
	 * Maximum number of things per pane.
	 * @type {number}
	 */
	this.someProperty = 4;
}
```

