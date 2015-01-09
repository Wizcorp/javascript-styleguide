## Indentation
Yes, a highly contencios topic so let's not waste time, at Wizcorp we use **tabs** for our projects. Tabs should be used for indentation, meaning at the beginning of lines only.


## Line length
Limit your lines to **120 characters**. We are not living in the 90's anymore our screen got a lot bigger, but at the same time our brains are the same, so let's not go too far, readability come first.


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
In C# where the braces are placed is up to the user, however the C# standard is on a new line.  That said as long as the project has agreed to use on the same line we won't complain.


## Naming
All names SHOULD be written in English, American English.
### In general:
##### Variable names
```csharp
public int aName;
private int _aName;
```


##### Property names
```csharp
public int Name { get; set; }
```


##### Function and Method names
```csharp

```


##### Class names
```csharp

```


##### Constants and Enum
```csharp

```


### Extra rules

##### Abbreviations and acronyms
```csharp

```

##### Specific Naming Conventions

- The "is" prefix SHOULD be used for boolean variables and methods. Alternatives include "has", "can" and "should".

- The terms "initialize" or "init" CAN be used where an object or a concept is established.

- UI Control variables SHOULD be suffixed by the control type. Examples: leftComboBox, topScrollPane.

- Plural form MUST be used to name collections.

- A "num" prefix or "count" postfix SHOULD be used for variables representing a number of objects.

- Iterator variables SHOULD be called "i", "j", "k", etc.

- Complement names MUST be used for complement entities. Examples: get/set, add/remove, create/destroy, start/stop, insert/delete, begin/end, etc.

- Negated boolean variable names MUST be avoided:
```javascript
	var isNotError, isNotFound; // WRONG.
```

- Methods returning an object MAY be named after what they return, and methods returning void after what they do.


## Variable declarations
Declare one variable per var statement, it makes it easier to re-order the lines, and put declarations in the order in which they make sense.
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
```csharp

```


## Conditions
Any non-trivial conditions should be assigned to a descriptive variable
```csharp
bool isAuthorized = (user.isAdmin() || user.isModerator());
if (isAuthorized) {
	Console.Log('winning');
}
```

## Return statement
To avoid deep nesting of if-statements, always return a function's value as early as possible.

```csharp
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
```csharp


```


## Comments

Comments are the documentation of your code; therefore **tricky code should not be commented but rewritten**. 

All comments should be written in English and be politically correct, even those that are supposed to be temporary.

Comments should be indented relative to their position in the code, preceding the code in question.

Even if everybody likes commented code, do not comment every single line of code; you will kill the readability of it.

Comments are supposed to explain an algorithm, not repeat it in a different language. This is wrong:
```javascript
// increment i by 1
i += 1;
```

Try to put comment at the top of a block of code to explain the point of it. And do not comment at the end of line of code, or only for declaration of variables (see JSDoc).


### Comment Syntax
The JSDoc syntax is based on JavaDoc . Many tools extract metadata from JSDoc comments to perform code validation and optimizations. These comments must be well-formed.
```javascript
/**
 * A JSDoc comment should begin with a slash and 2 asterisks.
 * Inline tags should be enclosed in braces like {@code this}.
 * @desc Block tags should always start on their own line.
 */
```

### Class Comments
Classes must be documented with a description and a type tag that identifies the constructor.
```javascript
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
```javascript
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
```javascript
/** @constructor */
function MyClass() {
	/**
	 * Maximum number of things per pane.
	 * @type {number}
	 */
	this.paneLimit = 4;
}
```

