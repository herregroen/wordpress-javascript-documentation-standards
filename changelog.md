#Changelog

## Aligning comments
* Added a section on aligning comments.

##Function documentation:
* **@augments** should not list the chain of inheritance, JSDoc can resolve this automatically if parents are properly documented and if ancestors are listed later their methods will override those of direct parents.
* Added **@alias**.
* Added **@memberOf**.
* Clarified **@fires** that it can optionally list a class name the event is tied to and corrected the example to use a hashtag.
* Updated example of **@listens** for proper usage of the event namespace.
* **@global** should not be used to list globals used. It should be used to mark the function as global.
* Added examples of optional variables using **@param**.
* Added examples of variables with default values using **@param**.

##Backbone class documentation
* Added explanation and examples for documenting Backbone classes.

##Object properties
* Changed to Class members as that seems to be what it's trying to explain. **@property** can not be used as shown.

##Namespaces
* Added explanation and examples for documenting namespaces.

##File headers
* Updated to use the **@file** and **@author** tags instead of the **@class** tag.
* Removed tags that cannot be used in file headers.
