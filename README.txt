This document intends to layout a style to follow for language bindings,
depending on the nature of the language.


Naming
------

If possible and no name clashes exist with other bindings, use the language's
shortest name or file suffix and append 'dc' or 'dyncall'. E.g.:
  Ruby: rbdc
  Go:   godc
  ...


Code style
----------

* Imperative:

  - Object oriented or prototype:

      Create 2 objects, one as a handle to each external library (e.g. extlib), one as a handle to a callvm

  - Without objects:

      Wrap dyncall as close as possible, exposing function by function

  - Statically typed (and no reflection/RTTI):

      Expose all dcArg, etc. calls
      Expose formatted call ('...') if possible, but as ArgF (instead of CallF), b/c return type is statically typed

  - with reflection/RTTI:

      Write a single call function and let users pass arguments, directly - if needed for type-conversion, this
      should be done via call signature



* Functional:

  ... nothing really different from imparative guidelines above?



* Other language features

 - Namespaces/modules/packages

     Use and name dyncall or dc (prefer former)
     Use casing depending on language requirements (e.g. 'Dyncall' for ruby as modules are const)

 - Function overloading or default arguments

     Use if available to define things like CallVM stack size; use independently named functions, otherwise

