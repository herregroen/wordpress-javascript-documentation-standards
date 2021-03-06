# JavaScript Documentation Standards

## What Should Be Documented

JavaScript documentation in WordPress takes the form of either formatted blocks of documentation or inline comments.

The following is a list of what should be documented in WordPress JavaScript files:

* Functions and class methods
* Objects
* Closures
* Object properties
* Requires
* Events
* File headers

## Documenting Tips

### Language
Short descriptions should be clear, simple, and brief. Document “what” and “when” – “why” should rarely need to be included. For example:

Functions and closures are third-person singular elements, meaning third-person singular verbs should be used to describe what each does.

> Tip: Need help remembering how to conjugate for third-person singular verbs? Imagine prefixing the function, hook, class, or method summary with “It”:
>
> * Good: “(It) Does something.”
> * Bad: “(It) Do something.”

**Functions**: What does the function do?

* Good: Handles a click on X element.
* Bad: Included for back-compat for X element.

**@since**: The recommended tool to use when searching for the version something was added to WordPress is svn blame.

If, after using these tools, the version number cannot be determined, use @since Unknown.

**Code Refactoring**: Do not refactor code in the file when making changes to the documentation.

### Grammar
Descriptive elements should be written as complete sentences. The one exception to this standard is file header summaries, which are intended as file “titles” more than sentences.

The serial (Oxford) comma should be used when listing elements in summaries, descriptions, and parameter or return descriptions.

## Formatting Guidelines

The following guidelines should be followed to ensure that the content of the doc blocks can be parsed properly for inclusion in the code reference.

**Short descriptions:**

Short descriptions should be a single sentence and contain no markup of any kind. If the description refers to an HTML element or tag, then it should be written as “link tag”, not “<a>”. For example: “Fires when printing the link tag in the header”.

**Long descriptions:**

Markdown can be used, if needed, in a long description. Lines should be

**@param and @returns tags:**

No HTML or markdown is permitted in the descriptions for these tags. HTML elements and tags should be written as “audio element” or “link tag”.

### Line wrapping
DocBlock text should wrap to the next line after 80 characters of text. If the DocBlock itself is indented on the left 20 character positions, the wrap could occur at position 100, but should not extend beyond a total of 120 characters wide.

### Aligning comments
Related comments should be spaced so that they align to make them more easily readable.

For example:
```javascript
/**
 * @param {very_long_type} name           Description.
 * @param {type}           very_long_name Description.
 */
```

## Functions

Functions should be formatted as follows:

* **Long description:** A supplement to the short description, providing a more detailed description. Use a period at the end.
* **@summary:** Short description – a brief, one line explanation of the purpose of the function. Use a period at the end.
* **@deprecated x.x.x:** Only use for deprecated functions, and provide the version the function was deprecated which should always be 3-digit (e.g. @since 3.6.0), and the function to use instead.
* **@since x.x.x:** Should always be 3-digit (e.g. @since 3.6.0).
* **@access:** Only use for functions if private. If the function is private, it is intended for internal use only, and there will be no documentation for it in the code reference.
* **@class:** Use for class constructors.
* **@augments:** For class constuctors, list direct parents.
* **@mixes:** List mixins that are mixed into the object.
* **@alias:** If this function is first assigned to a temporary variable this allows you to change the name it's documented under.
* **@memberof:** Namespace that this function is contained within if JSDoc is unable to resolve this automatically.
* **@static:** For classes, used to mark that a function is a static method on the class constructor.
* **@see:** A function or class relied on.
* **@link:** URL that provides more information.
* **@fires:** Event fired by the function. Events tied to a specific class should list the class name.
* **@listens:** Events this function listens for. An event must be prefixed with the event namespace. Events tied to a specific class should list the class name.
* **@global:** Marks this function as a global function to be included in the global namespace.
* **@param:** Give a brief description of the variable; denote particulars (e.g. if the variable is optional, its default) with JSDoc @param syntax.
* **@returns:** Note the period after the description.

```javascript
/**
 * @summary Short description. (use period)
 *
 * Long. (use period)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead.
 * @access     private
 *
 * @class
 * @augments parent
 * @mixes    mixin
 * 
 * @alias    realName
 * @memberof namespace
 *
 * @see  Function/class relied on
 * @link URL
 * @global
 *
 * @fires   eventName
 * @fires   className#eventName
 * @listens event:eventName
 * @listens className~event:eventName
 *
 * @param {type}   var           Description.
 * @param {type}   [var]         Description of optional variable.
 * @param {type}   [var=default] Description of optional variable with default variable.
 * @param {Object} objectVar     Description.
 * @param {type}   objectVar.key Description of a key in the objectVar parameter.
 * 
 * @returns {type} Description.
 */
```

## Backbone classes

Backbone's `extend` calls should be formatted as follows:

* **@lends** This tag will allow JSDoc to recognize the `extend` function from Backbone as a class definition. This should be placed right before the Object that contains the class definition.

Backbone's `initialize` functions should be formatted as follows:

* **Long description:** A supplement to the short description, providing a more detailed description. Use a period at the end.
* **@summary:** Short description – a brief, one line explanation of the purpose of the class. Use a period at the end.
* **@deprecated x.x.x:** Only use for deprecated classes, and provide the version the class was deprecated which should always be 3-digit (e.g. @since 3.6.0), and the class to use instead.
* **@since x.x.x:** Should always be 3-digit (e.g. @since 3.6.0).
* **@constructs** Marks this function as the constructor of this class.
* **@augments:** List direct parents.
* **@mixes:** List mixins that are mixed into the class.
* **@requires:** Lists modules that this class requires. Multiple **@requires** tags can be used.
* **@alias:** If this class is first assigned to a temporary variable this allows you to change the name it's documented under.
* **@memberof:** Namespace that this class is contained within if JSDoc is unable to resolve this automatically.
* **@static:** For classes, used to mark that a function is a static method on the class constructor.
* **@see:** A function or class relied on.
* **@link:** URL that provides more information.
* **@fires:** Event fired by the constructor. Should list the class name.
* **@param:** Document the arguments passed to the constructor even if not explicitly listed in `initialize`.
  * Backbone Models are passed `attributes` and `options` parameters.
  * Backbone Views are passed an `options` parameter.

```javascript
Class = Parent.extend(/** @lends namespace.Class.prototype */{
    /**
     * @summary Short description. (use period)
     *
     * Long. (use period)
     *
     * @since      x.x.x
     * @deprecated x.x.x Use new_function_name() instead.
     * @access     private
     *
     * @constructs namespace.Class
     * @memberOf   namespace
     * @augments   Parent
     * @mixes      mixin
     * 
     * @alias    realName
     * @memberof namespace
     *
     * @see   Function/class relied on
     * @link  URL
     * @fires Class#eventName
     *
     * @param {Object} attributes     The model's attributes.
     * @param {type}   attributes.key One of the model's attributes.
     * @param {Object} [options]      The model's options.
     * @param {type}   attributes.key One of the model's options.
     */
    initialize: function() {
        //Do stuff.
    }
})
```

If a Backbone class does not have an initialize function it should be documented by using **@inheritDoc** as follows:

```javascript
/**
 * @summary Short description. (use period)
 *
 * Long. (use period)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead.
 * @access     private
 *
 * @constructs namespace.Class
 * @memberOf   namespace
 * @augments   Parent
 * @mixes      mixin
 * @inheritDoc
 * 
 * @alias    realName
 * @memberof namespace
 *
 * @see   Function/class relied on
 * @link  URL
 */
Class = Parent.extend(/** @lends namespace.Class.prototype */{
	// Functions and properties.
})
```

> Note: This currently doesn't provide the expected functionality due to a bug with JSDoc's inheritDoc tag.
> See the issue [here](https://github.com/jsdoc3/jsdoc/issues/1012)

### Local functions

At times functions will be assigned to a local variable before being assigned as a class member.

Such functions should be marked as inner functions of the namespace that uses them using `~`.

The functions should be formatted as follows:

```javascript
/**
 * Function description, you can use any JSDoc here as long as the function remains private.
 * 
 * @alias namespace~doStuff
 */
var doStuff = function () {
	// Do stuff.
}

Class = Parent.extend(/** @lends namespace.Class.prototype */{
    /**
     * Class description
     *
     * @constructs namespace.Class
     * 
     * @borrows namespace~doStuff as prototype.doStuff
     */
    initialize: function() {
        //Do stuff.
    },

    /*
     * This function will automatically have it's documentation copied from above.
     * You should make a comment ( not a DocBlock using /**, instead use /* or // )
     * noting that you're describing this function using @borrows.
     */
    doStuff: doStuff,
})
```

### Local ancestors

At times classes will have Ancestors that are only assigned to a local variable.
Such classes should be assigned to the namespace their children are and be made inner classes using `~`.

These should be documented as follows:

```javascript
var Parent = GrandParent.extend(/** @lends namespace~Parent.prototype */{
	/**
     * Class description
     *
     * @constructs namespace~Class
     */
    initialize: function() {
        //Do stuff.
    },
})
```

## Class members

Class members should be formatted as follows:

 * **Short description:** Use a period at the end.
 * **@since x.x.x:** Should always be 3-digit (e.g. @since 3.6.0).
 * **@access:** If the members is private, protected or public. Private members are intended for internal use only.
 * **@type:** List the type of the class member.
 * **@property** List all properties this object has in case it's an Object.
 * **@member:** Optionally use this to override JSDoc's member detection in place of **@type** to force a class member.
 * **@memberof:** Optionally use this to override what class this is a member of.

```javascript
/**
 * Short description. (use period)
 *
 * @since  x.x.x
 * @access (private, protected, or public)
 *
 * @type     {type}
 * @property {type} key Description.
 *
 * @member   {type} realName
 * @memberof className
 */
```

## Namespaces

Namespaces should be formatted as follows:

 * **Short description:** Use a period at the end.
 * **@namespace:** Marks this symbol as a namespace, optionally provide a name as an override.
 * **@since x.x.x:** Should always be 3-digit (e.g. @since 3.6.0).
 * **@memberof:** Namespace that this namespace is contained in.
 * **@property:** Properties that this namespace exposes.
 
```javascript
/**
 * Short description. (use period)
 *
 * @namespace realName
 * @memberof  parentNamespace
 * 
 * @since x.x.x
 *
 * @property {type} key Description.
 */
```

## Inline Comments

Inline comments inside methods and functions should be formatted as follows:

### Single line comments 
```javascript
// Extract the array values.
```

### Multi-line comments
```javascript
/*
 * This is a comment that is long enough to warrant being stretched over
 * the span of multiple lines. You'll notice this follows basically
 * the same format as the JSDoc wrapping and comment block style.
 */

```
**Important note:** Multi-line comments must not begin with /** (double asterisk). Use /* (single asterisk) instead.

## File Headers

The JSDoc file header block is used to give an overview of what is contained in the file.

Whenever possible, all WordPress JavaScript files should contain a header block.

WordPress uses JSHint for general code quality testing. Any inline configuration options should be placed at the end of the header block.

```javascript
/**
 * The long description of the file's purpose goes here and
 * describes in detail the complete functionality of the file.
 * This description can span several lines and ends with a period.
 *
 * @summary A short description of the file.
 *
 * @link   URL
 * @file   This files defines the MyClass class.
 * @author AuthorName.
 * @since  x.x.x
 */
 
/** jshint {inline configuration here} */
```
