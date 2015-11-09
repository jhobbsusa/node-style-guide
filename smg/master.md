# Style Guide

This is a guide for writing consistent and aesthetically pleasing node.js code.
It is inspired by what is popular within the community, and flavored with some
personal opinions.

There is a .jshintrc which enforces these rules as closely as possible. You can
either use that and adjust it, or use
[this script](https://gist.github.com/kentcdodds/11293570) to make your own.

This guide was created by [Felix Geisendörfer](http://felixge.de/) and is
licensed under the [CC BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/)
license. You are encouraged to fork this repository and make adjustments
according to your preferences.

![Creative Commons License](http://i.creativecommons.org/l/by-sa/3.0/88x31.png)

## Table of contents

### Formatting
* [2 Spaces for indentation for open source](#2-spaces-for-indentation-for-open-source)
* [4 Spaces for indentation for Microsoft](#4-spaces-for-indentation-for-microsoft)
* [Newlines](#newlines)
* [No trailing whitespace](#no-trailing-whitespace)
* [Use Semicolons](#use-semicolons)
* [80 characters per line](#80-characters-per-line)
* [Use single quotes](#use-single-quotes)
* [Opening braces go on the same line](#opening-braces-go-on-the-same-line)
* [Declare one variable per var statement](#declare-one-variable-per-var-statement)

### Naming Conventions
* [Use lowerCamelCase for variables, properties and function  names](#use-lowercamelcase-for-variables-properties-and-function-names)
* [Use UpperCamelCase for class names](#use-uppercamelcase-for-class-names)
* [Use UPPERCASE for Constants](#use-uppercase-for-constants)

### Variables
* [Object / Array creation](#object--array-creation)

### Conditionals
* [Use the === operator](#use-the--operator)
* [Use multi-line ternary operator](#use-multi-line-ternary-operator)
* [Never nest multi-line ternary operators](#never-nest-multi-line-ternary-operators)
* [Use Regex sparingly](#use-regex-sparingly)
* [Use descriptive conditions](#use-descriptive-conditions)

### Functions
* [Write small functions](#write-small-functions)
* [Return early from functions](#return-early-from-functions)
* [Name your closures](#name-your-closures)
* [No nested closures](#no-nested-closures)
* [Method chaining](#method-chaining)

### Comments
* [Use slashes for comments](#use-slashes-for-comments)

### SQL
* [Use lowerCamelCase for variables](#use-lowercamcelcase-for-variables)
* [Use ALL UPPERCASE for all built-in keywords](#use-all-uppercase-for-all-built-in-keywords)
* [Use UpperCamelCase for everything else](#use-uppercamelcase-for-everything-else)
* [Make use of case-insensitivity to improve code clarity](#make-use-of-case-insensitivity-to-improve-code-clarity)
* [Use consistent indentation for code readability](#use-consistent-indentation-for-code-readability)

### Miscellaneous
* [Object.freeze, Object.preventExtensions, Object.seal, with, eval](#objectfreeze-objectpreventextensions-objectseal-with-eval)
* [Requires at top](#requires-at-top)
* [Always use import aliases](#always-use-import-aliases)
* [Getters and setters](#getters-and-setters)
* [Do not extend built-in prototypes](#do-not-extend-built-in-prototypes)
* [Don't mix modern standards with old](#dont-mix-modern-standards-with-old)


## Formatting


### 2 spaces for indentation for Open Source

Use 2 spaces for indenting your code and swear an oath to never mix tabs and
spaces - a special kind of hell is awaiting you otherwise.

This applies to PHP, JavaScript, HTML, CSS, and Asterisk.

### 4 spaces for indentation for Microsoft

This applies to .Net, VBA, ASP, etc.

### Newlines

Use UNIX-style newlines (`\n`), and a newline character as the last character
of a file. Windows-style newlines (`\r\n`) are forbidden inside any repository.

### No trailing whitespace

Just like you brush your teeth after every meal, you clean up any trailing
whitespace in your JS files before committing. Otherwise the rotten smell of
careless neglect will eventually drive away contributors and/or co-workers.

### Use Semicolons

According to [scientific research][hnsemicolons], the usage of semicolons is
a core value of our community. Consider the points of [the opposition][], but
be a traditionalist when it comes to abusing error correction mechanisms for
cheap syntactic pleasures.

[the opposition]: http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding
[hnsemicolons]: http://news.ycombinator.com/item?id=1547647

### 80 characters per line

Limit your lines to 80 characters (Strongly recommended). Yes, screens have gotten much bigger over the
last few years, but your brain has not. Use the additional room for split screen,
your editor supports that, right?

Due to existing class names that are very long this may not be a reasonable requirement.  
In such cases your hard limit is 120 characters.

### Use single quotes

Use single quotes, unless you are writing JSON.

*Right:*

```js
var foo = 'bar';
```

*Wrong:*

```js
var foo = "bar";
```

### Opening braces go on the same line

Your opening braces go on the same line as the statement.

*Right:*

```js
if (true) {
  console.log('winning');
}
```

*Wrong:*

```js
if (true)
{
  console.log('losing');
}
```

Also, notice the use of whitespace before and after the condition statement.

### Declare one variable per var statement

Declare one variable per var statement, it makes it easier to re-order the
lines. However, ignore [Crockford][crockfordconvention] when it comes to
declaring variables deeper inside a function, just put the declarations wherever
they make sense.

*Right:*

```js
var keys   = ['foo', 'bar'];
var values = [23, 42];

var object = {};
while (keys.length) {
  var key = keys.pop();
  object[key] = values.pop();
}
```

*Wrong:*

```js
var keys = ['foo', 'bar'],
    values = [23, 42],
    object = {},
    key;

while (keys.length) {
  key = keys.pop();
  object[key] = values.pop();
}
```

[crockfordconvention]: http://javascript.crockford.com/code.html

### Naming Conventions

### Use lowerCamelCase for variables, properties and function names

Variables, properties and function names should use `lowerCamelCase`.  They
should also be descriptive. Single character variables and uncommon
abbreviations should generally be avoided.

*Right:*

```js
var adminUser = db.query('SELECT * FROM users ...');
```

*Wrong:*

```js
var admin_user = db.query('SELECT * FROM users ...');
```

### Use UpperCamelCase for class names

Class names should be capitalized using `UpperCamelCase`.

*Right:*

```js
function BankAccount() {
}
```

*Wrong:*

```js
function bank_Account() {
}
```

## Use UPPERCASE for Constants

Constants should be declared as regular variables or static class properties,
using all uppercase letters.

*Right:*

```js
var SECOND = 1 * 1000;

function File() {
}
File.FULL_PERMISSIONS = 0777;
```

*Wrong:*

```js
const SECOND = 1 * 1000;

function File() {
}
File.fullPermissions = 0777;
```

[const]: https://developer.mozilla.org/en/JavaScript/Reference/Statements/const

## Variables

### Object / Array creation

Use trailing commas and put *short* declarations on a single line. Only quote
keys when your interpreter complains:

*Right:*

```js
var a = ['hello', 'world'];
var b = {
  good: 'code',
  'is generally': 'pretty',
};
```

*Wrong:*

```js
var a = [
  'hello', 'world'
];
var b = {"good": 'code'
        , is generally: 'pretty'
        };
```

## Conditionals

### Use the === operator

Programming is not about remembering [stupid rules][comparisonoperators]. Use
the triple equality operator as it will work just as expected.

*Right:*

```js
var a = 0;
if (a !== '') {
  console.log('winning');
}

```

*Wrong:*

```js
var a = 0;
if (a == '') {
  console.log('losing');
}
```

[comparisonoperators]: https://developer.mozilla.org/en/JavaScript/Reference/Operators/Comparison_Operators

### Use multi-line ternary operator

The ternary operator should be used on a single line.

*Right:*

```js
var foo = (a === b) ? 1 : 2;
```

*Wrong:*

```js
var foo = (a === b)
  ? 1
  : 2;
```

### Never nest multi-line ternary operators

We need to be able to read this stuff.  Keep it simple.

*Right:*

```js
var foo = 0;
if (a === b) {
 if (c === SOME_CONST) {
   foo = 1;
 }
} else {
  foo = 2;
}
```

*Wrong:*

```js
var foo = (a === b) ? (c === SOME_CONST) ? 1 : 0 : 2;
```


### Use Regex sparingly

While Regex offers great performance, it is rarely easy to read.  Always lean towards code readability over performance, except when it is truly necessary.  Keeping this in mind, use Regex sparingly.

### Use descriptive conditions

Any non-trivial conditions should be assigned to a descriptively named variable or function:

*Right:*

```js
var isValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);

if (isValidPassword) {
  console.log('winning');
}
```

*Wrong:*

```js
if (password.length >= 4 && /^(?=.*\d).{4,}$/.test(password)) {
  console.log('losing');
}
```

## Functions

### Write small functions

Keep your functions short. A good function fits on a slide that the people in
the last row of a big room can comfortably read. So don't count on them having
perfect vision and limit yourself to ~15 lines of code per function.

### Return early from functions

To avoid deep nesting of if-statements, always return a function's value as early
as possible.

*Right:*

```js
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

*Wrong:*

```js
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
```

Or for this particular example it may also be fine to shorten things even
further:

```js
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}
```

### Name your closures

Feel free to give your closures a name. It shows that you care about them, and
will produce better stack traces, heap and cpu profiles.

*Right:*

```js
req.on('end', function onEnd() {
  console.log('winning');
});
```

*Wrong:*

```js
req.on('end', function() {
  console.log('losing');
});
```

### No nested closures

Use closures, but don't nest them. Otherwise your code will become a mess.

*Right:*

```js
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
```

*Wrong:*

```js
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
```


### Method chaining

One method per line should be used if you want to chain methods.

You should also indent these methods so it's easier to tell they are part of the same chain.

*Right:*

```js
User
  .findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

*Wrong:*

```js
User
.findOne({ name: 'foo' })
.populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });

User.findOne({ name: 'foo' }).populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' }).populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

## Comments

### Use slashes for comments

Use slashes for both single line and multi line comments. Try to write
comments that explain higher level mechanisms or clarify difficult
segments of your code. Don't use comments to restate trivial things.

*Right:*

```js
// 'ID_SOMETHING=VALUE' -> ['ID_SOMETHING=VALUE', 'SOMETHING', 'VALUE']
var matches = item.match(/ID_([^\n]+)=([^\n]+)/));

// This function has a nasty side effect where a failure to increment a
// redis counter used for statistics will cause an exception. This needs
// to be fixed in a later iteration.
function loadUser(id, cb) {
  // ...
}

var isSessionValid = (session.expires < Date.now());
if (isSessionValid) {
  // ...
}
```

*Wrong:*

```js
// Execute a regex
var matches = item.match(/ID_([^\n]+)=([^\n]+)/);

// Usage: loadUser(5, function() { ... })
function loadUser(id, cb) {
  // ...
}

// Check if the session is valid
var isSessionValid = (session.expires < Date.now());
// If the session is valid
if (isSessionValid) {
  // ...
}
```

## SQL 

### Use lowerCamelCase for variables, properties and function names

*Right:*

```sql
ALTER proc [dbo].[DoSomeMagic] @spellName varchar(25)
AS
BEGIN
  Declare @batchId varchar(32)
```

*Wrong:*

```sql
ALTER proc [dbo].[DoSomeMagic] @SpellName varchar(25)
AS
BEGIN
  Declare @batch_id varchar(32)
```

### Use ALL UPPERCASE for all built-in keywords

All SQL Keywords should be in all UPPERCASE, like constants.

*Right:*

```sql
CREATE TABLE phoneNumbers (
  id INT IDENTITY(1,1),
  Area_Code VARCHAR(3) NOT NULL,
  NUMBER VARCHAR(8) NOT NULL,
  Createdat DATETIME NOT NULL,
  -- ...
)
```

*Wrong:*

```sql
create Table phoneNumbers (
  id int IDENTITY(1,1),
  Area_Code varchar(3) NOT NULL,
  NUMBER VARCHAR(8) not null,
  Createdat DateTime NOT NULL,
  -- ...
)
```


### Use UpperCamelCase for everything else

*Right:*

```sql
CREATE TABLE PhoneNumbers (
  Id int IDENTITY(1,1),
  AreaCode varchar(3) NOT NULL,
  Number varchar(8) NOT NULL,
  CreatedAt datetime NOT NULL,
  -- ...
)
```

*Wrong:*

```sql
CREATE TABLE phoneNumbers (
  id int IDENTITY(1,1),
  Area_Code varchar(3) NOT NULL,
  NUMBER varchar(8) NOT NULL,
  Createdat datetime NOT NULL,
  -- ...
)
```

### Make use of case-insensitivity to improve code clarity

There are many tables, views, etc that do not adhere to these coding standards.  When writing SQL make use of SQL Server's case-insensitivity to improve code clarity and to adhere to our current naming conventions.

Optionally use a single line for very simple statements involving no joins and a single where.

*Right:*

```js
// Given TABLE PBX..applications ( applicationid );
var sql = 'SELECT * FROM PBX..Applications WHERE ApplicationId = ?';
```

*Wrong:*

```js
// Given TABLE PBX..applications ( applicationid );
var sql = 'SELECT * FROM PBX..applications WHERE applicationid = ?';
```

### Use consistent indentation for code readability

*Right:*

```js
var sql = " \
  SELECT * \
  FROM   PBX..Applications app \
  JOIN   PBX..SplitTestApplications sta ON app.ApplicationId = sta.ApplicationId \
  WHERE  sta.SplitTestId = " + splitTest.id + " \
    AND  app.isActive = 1";
```

*Wrong:*

```js
var sql = 'SELECT * \
  FROM   PBX..Applications app \
  JOIN   PBX..SplitTestApplications sta ON app.ApplicationId = sta.ApplicationId \
  WHERE  sta.SplitTestId = " + splitTest.id + " \
  AND    app.isActive = 1";

var sql = ' \
  SELECT * FROM PBX..Applications app \
  JOIN PBX..SplitTestApplications sta \
  ON app.ApplicationId = sta.ApplicationId \
  WHERE sta.SplitTestId = " + splitTest.id;
```

## Miscellaneous

### Object.freeze, Object.preventExtensions, Object.seal, with, eval

Crazy shit that you will probably never need. Stay away from it.

### Requires at top

Always put requires at top of file to clearly illustrate a file's dependencies. Besides giving an overview for others at a quick glance of dependencies and possible memory impact, it allows one to determine if they need a package.json file should they choose to use the file elsewhere.

### Always use import aliases

This makes it immediately clear where variables and methods are coming from

*Right:* 

```vb.net
Imports db = DBCommanderController
Imports dbOptions = DBCommanderController.DBCommanderOptions
Imports dbSources = DBCommanderController.DBCommanderOptions.DataSources
Imports generic = System.Collections.Generic

' ...
dataSet = db.Execute(sql, dbSources.NUMBERS, dbOptions._DataSet)

Dim respOrgs As generic.List(Of String) = New generic.List(Of String)
```

*Wrong:*

```vb.net
Imports DBCommanderController
Imports DBCommanderController.DBCommanderOptions
Imports DBCommanderController.DBCommanderOptions.DataSources
Imports System.Collections.Generic

' ...
dataSet = Execute(sql, NUMBERS, _DataSet)

Dim respOrgs As List(Of String) = New List(Of String)
```

### Getters and setters

Do not use setters, they cause more problems for people who try to use your
software than they can solve.

Feel free to use getters that are free from [side effects][sideeffect], like
providing a length property for a collection class.

[sideeffect]: http://en.wikipedia.org/wiki/Side_effect_(computer_science)

### Do not extend built-in prototypes

Do not extend the prototype of native JavaScript objects. Your future self will
be forever grateful.

*Right:*

```js
var a = [];
if (!a.length) {
  console.log('winning');
}
```

*Wrong:*

```js
Array.prototype.empty = function() {
  return !this.length;
}

var a = [];
if (a.empty()) {
  console.log('losing');
}
```

### Don't mix modern standards with old

When editing legacy code try your best to adhere to the standards in the legacy code.  Don't force the new standard into the legacy documents.  Any standard is only as good as it is uniformly implemented.

