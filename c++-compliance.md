# C++ compliance
When writing C++ programs, depending on the context, one of five C++ standards may be used, each with its own programming restrictions:
1. ISO C++98
2. ISO C++11
3. ISO C++14
4. ISO C++17
5. ISO C++2a

## General C++ Compliance
* DO NOT USE raw `new[]/delete[]`, use STL Collections.
* Prefer static polymorphism over dynamic polymorphism. 
* Use exceptions to indicate situations out of the control of the programmer, not to indicate programmer error
    * Ignore this in cases where exceptions may be explicitly requested by the programmer (such as `PolymorphicWrapper::checkedcast`/equivalent)
    * If a possible and available, cause a compile time error to indicate a programming issue
    * Otherwise, document these errors as preconditions. (IE. the behavior is undefined)
* Use Pass-by-reference over pass-by-value for all class-types where it makes sense. 
   * Ignore this point for small, *TriviallyCopyable* types.
* Use Pass-by-value for all scalar types.
* Use pointers only to indicate one of the following:
    * An array with a dynamic length
    * An optional reference
    * A type-erased reference
* Use array references to pass arrays whenever it makes sense.
* Do not declare reference, `const`, or `volatile` non-static data members. 
    * Also avoid `mutable` members.
* Do not declare global static objects that are not scalar, *Trivial*, or *LiteralType*.
    * All global static object should either be constant initialized or trivially default-initialized.
    * Prefer declaring global static objects as either `const` or `constexpr` (when available and applicable).
    * Declare any other global objects as global functions that return a reference to a `function-local static`.
* Do not fwrite or fread objects which do not meet the requirements for lclib-c++ *BytesWritable* or *BytesReadable* concepts respectively.
* Avoid `volatile` member functions.

## ISO C++98 Compliance

* Follow the rule of Three
    * If a program defines any of Copy Constructor, Copy Assignment, or Destructor for a class. It should define all 3.

## ISO C++11 Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.
* Const member functions should always be safe to call concurrently with any other const member function
* Prefer scoped enumerations over unscoped enumerations.

## ISO C++14 Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.
* Const member functions should always be safe to call concurrently with any other const member function
* Prefer scoped enumerations over unscoped enumerations.

## ISO C++17 Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.
* Const member functions should always be safe to call concurrently with any other const member function
* Prefer scoped enumerations over unscoped enumerations.

## ISO C++2a Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
    * Use `std::is_constant_evaluated()` in circumstances where it can be made into a constexpr function, but at the cost of performace.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Prefer `[[assert]]` over `assert` macro.
* Prefer using `[[expects]]` and `[[ensures]]` over `[[assert]]` wherever it makes sense.
* Prefer concepts over SFINAE.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.
* Use ranges whenever possible over iterator-pair algorithms.
* Const member functions should always be safe to call concurrently with any other const member function
* Prefer scoped enumerations over unscoped enumerations.
