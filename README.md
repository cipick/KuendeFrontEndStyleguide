## Table of Contents

* [The CoffeeScript Style Guide](#guide)
    * [Code Layout](#code_layout)
        * [Tabs or Spaces?](#tabs_or_spaces)
        * [Maximum Line Length](#maximum_line_length)
        * [Blank Lines](#blank_lines)
        * [Trailing Whitespace](#trailing_whitespace)
        * [Optional Commas](#optional_commas)
        * [Encoding](#encoding)
    * [Whitespace in Expressions and Statements](#whitespace)
    * [Comments](#comments)
        * [Block Comments](#block_comments)
        * [Inline Comments](#inline_comments)
    * [Naming Conventions](#naming_conventions)
    * [Functions](#functions)
    * [Strings](#strings)
    * [Conditionals](#conditionals)
    * [Looping and Comprehensions](#looping_and_comprehensions)
    * [Extending Native Objects](#extending_native_objects)
    * [Exceptions](#exceptions)
    * [Annotations](#annotations)
    * [Miscellaneous](#miscellaneous)
* [Marionette + Backbone Style Guide](#marionette-guide)
 	* [CoffeeScript](#mar-coffeescript)
    * [Modules](#mar-modules)
    	* [Grouping](#mar-grouping)
        * [Shared models](#mar-shared)
        * [Naming](#mar-naming--modules)
        * [File structure](#mar-file--structure)
    * [Routers](#mar-routers)
    * [Controllers](#mar-controllers)
    * [Views](#mar-views)
    	* [Naming](#mar-naming--views)
        * [Callbacks](#mar-callbacks)
    * [Regions](#mar-regions)
    	* [Naming](#mar-naming-regions)
* [Lodash] (#lodash)
	* [Object](#lod-object)
    	* [_.assign](#lod-assign)
    	* [_.clone](#lod-clone)
        * [_.forOwn](#lod-forown)
        * [_.pick](#lod-pick)
    * [Functions](#lod-func)
    	* [_.throttle](#lod-throttle)
    * [Array](#lod-array)
    	* [_.last](#lod-last)
    * [Collections](#lod-col)
    	* [_.forEach](#lod-foreach)
    
<a name="guide"/>
#  The CoffeeScript Style Guide
-------------------------------

<a name="code_layout"/>
## Code layout

<a name="tabs_or_spaces"/>
### Tabs or Spaces?

Use **tabs only**, with **one tab** per indentation level. Never mix tabs and spaces.

<a name="maximum_line_length"/>
### Maximum Line Length

Limit all lines to a maximum of 79 characters.

<a name="blank_lines"/>
### Blank Lines

Separate top-level function and class definitions with a single blank line.

Separate method definitions inside of a class with a single blank line.

Use a single blank line within the bodies of methods or functions in cases where this improves readability (e.g., for the purpose of delineating logical sections).

<a name="trailing_whitespace"/>
### Trailing Whitespace

Do not include trailing whitespace on any lines.

<a name="optional_commas"/>
### Optional Commas

Avoid the use of commas before newlines when properties or elements of an Object or Array are listed on separate lines.

```coffeescript
# Yes
foo = [
  'some'
  'string'
  'values'
]
bar:
  label: 'test'
  value: 87

# No
foo = [
  'some',
  'string',
  'values'
]
bar:
  label: 'test',
  value: 87
```
###Tabs or Spaces?

Use tabs only, with 1 tab per indentation level. Never mix tabs and spaces.

###Maximum Line Length

Limit all lines to a maximum of 79 characters.

###Blank Lines

Separate top-level function and class definitions with a single blank line.

Separate method definitions inside of a class with a single blank line.

Use a single blank line within the bodies of methods or functions in cases where this improves readability (e.g., for the purpose of delineating logical sections).

<a name="whitespace"/>
## Whitespace in Expressions and Statements

Avoid extraneous whitespace in the following situations:

- Immediately inside parentheses, brackets or braces

    ```coffeescript
       ($ 'body') # Yes
       ( $ 'body' ) # No
    ```

- Immediately before a comma

    ```coffeescript
       console.log x, y # Yes
       console.log x , y # No
    ```

Additional recommendations:

- Always surround these binary operators with a **single space** on either side

    - assignment: `=`

        - _Note that this also applies when indicating default parameter value(s) in a function declaration_

           ```coffeescript
           test: (param = null)-> # Yes
           test: (param=null)-> # No
           ```

    - augmented assignment: `+=`, `-=`, etc.
    - comparisons: `==`, `<`, `>`, `<=`, `>=`, `unless`, etc.
    - arithmetic operators: `+`, `-`, `*`, `/`, etc.

    - _(Do not use more than one space around these operators)_

        ```coffeescript
           # Yes
           x = 1
           y = 1
           fooBar = 3

           # No
           x      = 1
           y      = 1
           fooBar = 3
        ```

<a name="comments"/>
## Comments

If modifying code that is described by an existing comment, update the comment such that it accurately reflects the new code. (Ideally, improve the code to obviate the need for the comment, and delete the comment entirely.)

The first word of the comment should be capitalized, unless the first word is an identifier that begins with a lower-case letter.

If a comment is short, the period at the end can be omitted.

<a name="block_comments"/>
### Block Comments

Block comments apply to the block of code that follows them.

Each line of a block comment starts with a `#` and a single space, and should be indented at the same level of the code that it describes.

Paragraphs inside of block comments are separated by a line containing a single `#`.

```coffeescript
  # This is a block comment. Note that if this were a real block
  # comment, we would actually be describing the proceeding code.
  #
  # This is the second paragraph of the same block comment. Note
  # that this paragraph was separated from the previous paragraph
  # by a line containing a single comment character.

  init()
  start()
  stop()
```
<a name="inline_comments"/>
### Inline Comments

Inline comments are placed on the line immediately above the statement that they are describing. If the inline comment is sufficiently short, it can be placed on the same line as the statement (separated by a single space from the end of the statement).

All inline comments should start with a `#` and a single space.

The use of inline comments should be limited, because their existence is typically a sign of a code smell.

Do not use inline comments when they state the obvious:

```coffeescript
  # No
  x = x + 1 # Increment x
```

However, inline comments can be useful in certain scenarios:

```coffeescript
  # Yes
  x = x + 1 # Compensate for border
```

<a name="naming_conventions"/>
## Naming Conventions

Use `camelCase` (with a leading lowercase character) to name all variables, methods, and object properties.

Use `CamelCase` (with a leading uppercase character) to name all classes. _(This style is also commonly referred to as `PascalCase`, `CamelCaps`, or `CapWords`, among [other alternatives][camel-case-variations].)_

_(The **official** CoffeeScript convention is camelcase, because this simplifies interoperability with JavaScript. For more on this decision, see [here][coffeescript-issue-425].)_

For constants, use all uppercase with underscores:

```coffeescript
CONSTANT_LIKE_THIS
```

Methods and variables that are intended to be "private" should begin with a leading underscore:

```coffeescript
_privateMethod: ->
```

<a name="functions"/>
## Functions

_(These guidelines also apply to the methods of a class.)_

When declaring a function that takes arguments, never use space after the closing parenthesis of the arguments list:

```coffeescript
foo = (arg1, arg2)-> # Yes
foo = (arg1, arg2) -> # No
```

Do not use parentheses when declaring functions that take no arguments:

```coffeescript
bar = -> # Yes
bar = ()-> # No
```

In cases where method calls are being chained and the code does not fit on a single line, each call should be placed on a separate line and indented by one level (i.e., one tab), with a leading `.`.

```coffeescript
[1..3]
  .map((x)-> x * x)
  .concat([10..12])
  .filter((x)-> x < 11)
  .reduce((x, y)-> x + y)
```

When calling functions, choose to omit or include parentheses in such a way that optimizes for readability. Keeping in mind that "readability" can be subjective, the following examples demonstrate cases where parentheses have been omitted or included in a manner that the community deems to be optimal:

```coffeescript
baz 12

brush.ellipse x: 10, y: 20 # Braces can also be omitted or included for readability

foo(4).bar(8)

obj.value(10, 20) / obj.value(20, 10)

print inspect value

new Tag(new Value(a, b), new Arg(c))
```

You will sometimes see parentheses used to group functions (instead of being used to group function parameters). Examples of using this style (hereafter referred to as the "function grouping style"):

```coffeescript
($ '#selektor').addClass 'klass'

(foo 4).bar 8
```

This is in contrast to:

```coffeescript
$('#selektor').addClass 'klass'

foo(4).bar 8
```

<a name="strings"/>
## Strings

Use string interpolation instead of string concatenation:

```coffeescript
"this is an #{adjective} string" # Yes
"this is an " + adjective + " string" # No
```

Prefer single quoted strings (`''`) instead of double quoted (`""`) strings, unless features like string interpolation are being used for the given string.

<a name="conditionals"/>
## Conditionals

Favor `unless` over `if` for negative conditions.

Instead of using `unless...else`, use `if...else`:

```coffeescript
  # Yes
  if true
    ...
  else
    ...

  # No
  unless false
    ...
  else
    ...
```

Multi-line if/else clauses should use indentation:

```coffeescript
  # Yes
  if true
    ...
  else
    ...

  # No
  if true then ...
  else ...
```

<a name="looping_and_comprehensions"/>
## Looping and Comprehensions

Take advantage of comprehensions whenever possible:

```coffeescript
  # Yes
  result = (item.name for item in array)

  # No
  results = []
  for item in array
    results.push item.name
```

To filter:

```coffeescript
result = (item for item in array when item.name is "test")
```

To iterate over the keys and values of objects:

```coffeescript
object = one: 1, two: 2
alert("#{key} = #{value}") for key, value of object
```

<a name="annotations"/>
## Annotations

Use annotations when necessary to describe a specific action that must be taken against the indicated block of code.

Write the annotation on the line immediately above the code that the annotation is describing.

The annotation keyword should be followed by a colon and a space, and a descriptive note.

```coffeescript
  # FIXME: The client's current state should *not* affect payload processing.
  resetClientState()
  processPayload()
```

If multiple lines are required by the description, indent subsequent lines with two spaces:

```coffeescript
  # TODO: Ensure that the value returned by this call falls within a certain
  #   range, or throw an exception.
  analyze()
```

Annotation types:

- `TODO`: describe missing functionality that should be added at a later date
- `FIXME`: describe broken code that must be fixed
- `OPTIMIZE`: describe code that is inefficient and may become a bottleneck
- `HACK`: describe the use of a questionable (or ingenious) coding practice
- `REVIEW`: describe code that should be reviewed to confirm implementation

If a custom annotation is required, the annotation should be documented in the project's README.

<a name="miscellaneous"/>
## Miscellaneous

`and` is preferred over `&&`.

`or` is preferred over `||`.

`is` is preferred over `==`.

`not` is preferred over `!`.

`or=` should be used when possible:

```coffeescript
temp or= {} # Yes
temp = temp || {} # No
```

Prefer shorthand notation (`::`) for accessing an object's prototype:

```coffeescript
Array::slice # Yes
Array.prototype.slice # No
```

Prefer `@property` over `this.property`.

```coffeescript
return @property # Yes
return this.property # No
```

However, avoid the use of **standalone** `@`:

```coffeescript
return this # Yes
return @ # No
```

Avoid `return` where not required, unless the explicit return increases clarity.

Use splats (`...`) when working with functions that accept variable numbers of arguments:

```coffeescript
console.log args... # Yes

(a, b, c, rest...) -> # Yes
```

# Marionette + Backbone Style Guide
___________________________________

## CoffeeScript

We use CoffeeScript for writing our code, instead of vanilla JavaScript, allowing us to focus our attention on problem-solving.

## Modules

### Grouping

Keep your app modular. Instead of putting all views in a single "Views" namespace (and so on with models etc), use modules to break your app into components, giving each one its necessary views and models.

```coffeescript
# Bad
App.module 'Views', (Views) ->
  class Views.UserView extends Marionette.ItemView
  class Views.UsersView extends Marionette.CollectionView
  class Views.SettingView extends Marionette.ItemView

App.module 'Models', (Models) ->
  class Models.User extends Backbone.Model
  class Models.Setting extends Backbone.Model

App.module 'Collections', (Collections) ->
  class Collections.User extends Backbone.Collection

# Good
App.module 'Users', (Users) ->
  class Users.UserView extends Marionette.ItemView
  class Users.UsersView extends Marionette.CollectionView
  class Users.User extends Backbone.Model
  class Users.Users extends Backbone.Collection

App.module 'Settings', (Settings) ->
  class Settings.SettingView extends Marionette.ItemView
  class Settings.Setting extends Backbone.Model
```

### Shared models

If a model is considered very "global" such that it is shared between many modules, then it is best to define it in its own namespace.

### Naming

A module should be named after its main concern. If the concern relates to an object such as a primary model, then prefer to pluralise the name.

```coffeescript
# Bad
App.module 'UserPage', (UserPage) ->
  class UserPage.UserPageView extends Marionette.ItemView
  
# Good
App.module 'Users', (Users) ->
  class Users.UserView extends Marionette.ItemView
```

Keep areas that are related to a higher-level modules as submodules of it.

```coffeescript
# Bad
App.module 'UsersSettings', (UserSettings) ->
  class UserSettings.SettingsView extends Marionette.ItemView

# Good
App.module 'Users.Settings', (Settings) ->
  class Settings.SettingsView extends Marionette.ItemView
```

### File structure

Although models and views should be grouped within the module that they refer to, it can be useful to split the directory structure into `views` and `models`.

```
modules/
  users/
    views/
      user_view.js.coffee
      users_view.js.coffee
    models/
      user.js.coffee
      users.js.coffee
    router.js.coffee
    controller.js.coffee
```

## Routers

A module should only ever need at most one router, defining the routes necessary for that module to function.

```coffeescript
# Bad
App.module 'Routes', (Routes) ->
  class Routes.Router extends Marionette.Router
    appRoutes:
      # five million routes defined here

# Good
App.module 'Users', (Users) ->
  class Users.Router extends Marionette.Router
    appRoutes:
      "users/:id" : "show"
      "users" : "index"

App.module 'Settings', (Settings) ->
  class Settings.Router extends Marionette.Router
    appRoutes:
      "settings" : "index"
```

## Controllers

A module should only ever need at most one controller. Modules with multiple routes and actions can organise themselves better by splitting into submodules, with each submodule defining its own controller to handle the request.

```coffeescript
# OK
# modules/users/controller
App.module 'Users', (Users) ->
  class Users.Controller
    show: ->
      app.pageRegion.show(new Users.UserView)
      
    edit: ->
      app.pageRegion.show(new Users.EditUserView)

# Better
# modules/users/controller.js.coffee
App.module 'Users', (Users) ->
  class Users.Controller
    show:  -> new App.Users.Show.Controller().show()
    edit:  -> new App.Users.Edit.Controller().edit()

# modules/users/show/controller.js.coffee
App.module 'Users.Show', (Show) ->
  class Show.Controller
    show: ->
      app.pageRegion.show(new Show.UserView)

# modules/users/edit/controller.js.coffee
App.module 'Users.Edit', (Edit) ->
  class Edit.Controller
    edit: ->
      app.pageRegion.show(new Edit.UserView)
```

## Views

### Naming

All views have the class suffix `View`, but should never be called simply `View` even if they are the only or primary view of a module.

```coffeescript
# Bad
App.module 'Simple', (Simple) ->
  class Simple.View extends Marionette.ItemView

# Good
App.module 'Simple', (Simple) ->
  class Simple.SimpleView extends Marionette.ItemView
```

### Callbacks

Favour using `onRender` instead of `onShow` if you want the callback to run every time the view is rendered with `view.render()`. This is particularly useful during isolated tests where you may not be rendering the view within a region.

```coffeescript
# OK
class ThingView extends Marionette.ItemView
  onShow: ->
    @$('.thing-i-must-hide').hide()

view = new ThingView()
view.render().onShow() # because we have no region


# Better
class ThingView extends Marionette.ItemView
  onRender: ->
    @$('.thing-i-must-hide').hide()

view = new ThingView()
view.render()
```


## Regions

<a name="mar-naming-regions" />
### Naming

Name your regions with the suffix `Region` so that they do not get confused with other fields.

```coffeescript
# Bad - @name could get confusing
@name.show(@nameView)

# Good - @nameRegion is obviously a region
@nameRegion.show(@nameView)
```


#Lodash
------
```coffeescript
_.clone(value, [isDeep=false], [callback], [thisArg])
```

Creates a clone of value. If isDeep is true nested objects will also be cloned, otherwise they will be assigned by reference. If a callback is provided it will be executed to produce the cloned values. If the callback returns undefined cloning will be handled by the method instead. The callback is bound to thisArg and invoked with one argument; (value).

```coffeescript
_.throttle(func, wait, [options])
```
Creates a function that, when executed, will only call the func function at most once per every wait milliseconds. Provide an options object to indicate that func should be invoked on the leading and/or trailing edge of the wait timeout. Subsequent calls to the throttled function will return the result of the last func call.

```coffeescript
_.assign(object, [source], [callback], [thisArg])
```
Assigns own enumerable properties of source object(s) to the destination object. Subsequent sources will overwrite property assignments of previous sources. If a callback is provided it will be executed to produce the assigned values. The callback is bound to thisArg and invoked with two arguments; (objectValue, sourceValue).

```coffeescript
_.forEach(collection, [callback=_.identity], [thisArg])
```
Iterates over elements of a collection, executing the callback for each element. The callback is bound to thisArg and invoked with three arguments; (value, index|key, collection). Callbacks may exit iteration early by explicitly returning false.

Note: As with other "Collections" methods, objects with a length property are iterated like arrays. To avoid this behavior _.forIn or _.forOwn may be used for object iteration.

```coffeescript
_.last(array, [callback], [thisArg])
```
Gets the last element or last n elements of an array. If a callback is provided elements at the end of the array are returned as long as the callback returns truthy. The callback is bound to thisArg and invoked with three arguments; (value, index, array).

If a property name is provided for callback the created "_.pluck" style callback will return the property value of the given element.

If an object is provided for callback the created "_.where" style callback will return true for elements that have the properties of the given object, else false.

```coffeescript
_.assign(object, [source], [callback], [thisArg])
```
Assigns own enumerable properties of source object(s) to the destination object. Subsequent sources will overwrite property assignments of previous sources. If a callback is provided it will be executed to produce the assigned values. The callback is bound to thisArg and invoked with two arguments; (objectValue, sourceValue).

```coffeescript
_.pick(object, [callback], [thisArg])
```
Creates a shallow clone of object composed of the specified properties. Property names may be specified as individual arguments or as arrays of property names. If a callback is provided it will be executed for each property of object picking the properties the callback returns truthy for. The callback is bound to thisArg and invoked with three arguments; (value, key, object).

--------------

```coffeescript
_.forOwn(object, [callback=_.identity], [thisArg])
```
Iterates over own enumerable properties of an object, executing the callback for each property. The callback is bound to thisArg and invoked with three arguments; (value, key, object). Callbacks may exit iteration early by explicitly returning false.
```
_.forOwn({ '0': 'zero', '1': 'one', 'length': 2 }, function(num, key) {
  console.log(key);
});
// → logs '0', '1', and 'length' (property order is not guaranteed across environments)
```

#jQuery
------
Use jQuery to: 
- navigate a document 
- select and manipulate DOM elements 
```coffeescript
$('el').addClass('class')
$('el').css('left', 0)
```
- create animations
```coffeescrip 
$('el').animate({
    opacity: 0.25,
    left: "+=50",
    height: "toggle"
  }, 5000, function() {
    // Animation complete.
  });
```
- handle events

- Ajax requests.

<a name="amd"/>
#AMD
---

`require` statements should be placed on separate lines.

```coffeescript
require 'lib/setup'
Backbone = require 'backbone'
```
These statements should be grouped in the following order:

1. Standard library imports _(if a standard library exists)_
2. Third party library imports
3. Local imports _(imports specific to this application or library)_

#Building
--------
## Gulp
### Remove old fonts
``` gulp remove-old-fonts```
### Suffix fonts and copy
``` gulp copy-fonts```
### Find last git revision
``` gulp gitrev```
### Clean old uncached CSS files
``` gulp build-styles-clean```
### Build styles
``` gulp build-styles```
### Build Pages
``` gulp build-pages```
### Build Scripts
``` gulp build-scripts```
### Build Templates
``` gulp build-templates```
### Copy vendor JS code
``` gulp build-vendor```
### Build
``` gulp build```
### Development
``` gulp dev```
### Watch
``` gulp w```
### Test
``` gulp t```
### Test CI (functional tests)
``` gulp tci```
### Documentation through backend code
``` gulp doc```
### Staging deploy through backend code
``` gulp staging-full```
### Deploy only front end to staging
``` gulp s```
### Deploy only front end to staging. Deploy as dev version
``` gulp sd```

#Handlebars
----------

## Helpers

### Conditional helpers
Sometimes you may only want to display part of your template if a property exists. For example, let’s say we have a view with a person property that contains an object with firstName and lastName fields:

```coffeescript
{{#if person}}
  Welcome back, <b>{{person.firstName}} {{person.lastName}}</b>!
{{/if}}
```

```coffeescript
{{#if person}}
  Welcome back, <b>{{person.firstName}} {{person.lastName}}</b>!
{{else}}
  Please log in.
{{/if}}
```

```coffeescript
{{#unless hasPaid}}
  You owe: ${{total}}
{{/unless}}
```

### Displaying a List of Items
If you need to display a basic list of items, use Handlebar’s ```{{#each}}``` helper:

```coffeescript
{{#each people}}
Hello, {{name}}!
{{/each}}
```
### Equality
Use ```{{#eq val1 val2}}``` when you need to check the type of object.
```coffeescript
{{#eq type "all" }}
<button class="orderer" data-target="sortableAnswers_{{type}}">save order</button>
{{/eq}}
```
### Binding Element Attributes with {{bindAttr}}
In addition to text, you may also want your templates to dictate the attributes of your HTML elements. For example, imagine a view that contains a URL:
```
App.LogoView = SC.TemplateView.extend({
  logoUrl: 'http://www.mycorp.com/images/logo.png'
});
```

```
<div id="logo">
  <img {{bindAttr src="logoUrl"}} alt="Logo">
</div>
```

### Saving the Pages (400, 500, landing, lobby)
I save all Handlebars.js templates in app/pages/

### Saving the Templates
I save all Handlebars.js templates in app/templates/

Project Structure:
```
project/
	css/
	js/
    pages/
    	partials/
        _*.hbs
    templates/
      sections/
      	block/
        	element.hbs
```