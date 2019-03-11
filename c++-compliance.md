# C++ compliance
When writing C++ programs, depending on the context, one of four C++ standards may be used, each with its own programming restrictions:
1. ISO C++98
2. ISO C++11
3. ISO C++14
4. ISO C++17
5. ISO C++2a

## General C++ Compliance
* DO NOT USE raw `new[]/delete[]`, use STL Collections.

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

## ISO C++14 Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.

## ISO C++17 Compliance

* If a function can be made into a valid constexpr function without sacrificing runtime performance, then it should be.
* Avoid Preprocessor macros wherever possible. Use templates, constexpr functions, and constexpr variables instead.
* Follow the Rules of Five and Zero. 
    * If a program user-defines any of Copy Constructor, Copy Assignment, Move Constructor, Move Assignment or Destructor for a class, each of the 5 should either be user-defined or deleted.
* `=default` all special member functions if possible and it makes sense to do so.
* `=delete` any special member function that does not make sense for the type. 
* Avoid raw calls to `new/delete`, use RAII Allocation wrappers, or automatic variables whenever possible.

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
