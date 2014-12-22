CoffeeScript
------------

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

Backbone/Marionette
-------------------

Lodash
------

jQuery
------

AMD
---

Building
--------

Handlebars
----------
###Saving the Templates
I save all Handlebars.js templates in app/templates/
###Saving the Pages
I save all Handlebars.js templates in app/pages/