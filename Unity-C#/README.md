
#Preamble 
The below style uses the MSDN Style guidelines as a base to work with Unity, however because some of the nuances in Unity this style adapts and breaks from some of the standard conventions to obtain a higher level of readability.

MSDN Style: http://msdn.microsoft.com/en-us/library/ff926074.aspx
MSDN Class Styles documenting that public fields are not supposed to be used: http://msdn.microsoft.com/en-us/library/ms229012(v=vs.110).aspx
MSND XML Comments: http://msdn.microsoft.com/en-us/library/b2s063f7.aspx

There is also a Unity style guide however because they have used Properties, which is not supported in the Unity Editor), and that the style is almost exactly the same as the MSDN style, the MSDN style was used where possible.
Unity Style: http://wiki.unity3d.com/index.php/Csharp_Coding_Guidelines

# Style

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

* Function calls and method calls SHOULD NOT be followed by a space. Example: `DoSomething(string name); // NOT DoSomething (string name)`

* Logical units within a block SHOULD be separated by one blank line.

* Curly braces SHOULD have inner spaces.


## Braces
In C# where the braces are placed is up to the user, however the C# MSDN standard is on a new line.  That said as long as the project has agreed to use on the same line there should be no complaints.


## Naming
All names SHOULD be written in English, American English.
### In general:
##### Variable names
The reason that underscore use of private varibles is favored even though it is generally not standard is because Properties are not supported in Unity so the standard public accessor notation for C# and the MSDN guidelines can not be used effectively.
```csharp
public int aName;
private int _aName;
```


##### Property names
In Unity properties are not supported in the editor, and their use is discouraged.  If you want to have a member in the Unity Editor you need to use a public member (which is against MSDN coding guidelines).
```csharp
public int Name { get; set; }
```


##### Method names

```csharp
public void Rename(int name)
```


##### Class names
```csharp
public class User
```


##### Constants
```csharp
public const int MyNumber = 42;
```


##### Enum
```csharp
public enum Name
```


##### Specific Naming Conventions

- The "is" prefix SHOULD be used for boolean variables and methods. Alternatives include "has", "can" and "should".

- The terms "initialize" or "init" CAN be used where an object or a concept is established.

- Plural form MUST be used to name collections.

- Iterator variables SHOULD be called "i", "j", "k", etc.

- Complement names MUST be used for complement entities. Examples: get/set, add/remove, create/destroy, start/stop, insert/delete, begin/end, etc.

- Negated boolean variable names MUST be avoided:
```csharp
	bool isNotError, isNotFound; // WRONG.
```

- Methods returning an object MAY be named after what they return, and methods returning void after what they do.


## Variable declarations
Declare one variable per type statement, it makes it easier to re-order the lines, and put declarations in the order in which they make sense.
Idealy, variables should be initialized where they are declared and they must be declared in the smallest scope possible.


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
```csharp

```


## Conditions
Any non-trivial conditions should be assigned to a descriptive variable
```csharp
bool isAuthorized = (user.IsAdmin() || user.IsModerator());
if (isAuthorized)
{
	Console.Log('winning');
}
```

## Return statement
To avoid deep nesting of if-statements, always return a function's value as early as possible.

```csharp
public bool IsPercentage(int percent) 
{
	if (percent < 0)
	{
		return false;
	}

	if (percent > 100)
	{
		return false;
	}

	return true;
}

```


## Comments

Comments are the documentation of your code; therefore **tricky code should not be commented but rewritten**. 

All comments should be written in English and be politically correct, even those that are supposed to be temporary.

Comments should be indented relative to their position in the code, preceding the code in question.

Even if everybody likes commented code, do not comment every single line of code; you will kill the readability of it.

Comments are supposed to explain an algorithm, not repeat it in a different language. This is wrong:
```csharp
// increment i by 1
i += 1;
```

Try to put comment at the top of a block of code to explain the point of it..


### Comment Syntax
The Visual Studio syntax is based on XML . Many tools can extract this XML and create useful help documents for you. These comments must be well-formed.

It is important to note that projects in Unity may not be using Visual Studio, in this case one style should be picked, and be accepted project wide.
```csharp
/// <summary>
/// You can use the summary tags above any piece of code so tools can extract this
/// </summary>

// If you do not want the comment to appear you can use the normal comment syntax,
// the use of /* comment */ is discouraged.

// Single line version is prefered
```

### Class Comments
Classes must be documented with a description summary
```csharp
/// <summary>
/// A simple user class
/// </summary>
public class User
{
	/// <summary>
	/// User constructor initialises user name
	/// </summary>
	/// <param name="name">Persons name</param>
	public User(string name) 
	{
		// ...
	}
}

// A simple user class
public class User
{
	// User constructor initialises user name
	// name - Persons name
	public User(string name) 
	{
		// ...
	}
}
```

### Method Comments
Method descriptions should start with a sentence written in the third person declarative voice.
```csharp
/// <summary>
/// Renames the user
/// </summary>
/// <param name="name">Persons name</param>
public void Rename(string name)
{
	// ...
}

// Renames the user
// name - Persons name
public void Rename(string name)
{
	// ...
}
```

