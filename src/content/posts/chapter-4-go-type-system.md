---
title: "Chapter 4 — Go’s Type System: Structs, Slices, Maps, and Interfaces"
meta_title: "Chapter 4 — Go Type System"
description: "A comprehensive exploration of Go’s type system, covering structs, slices, maps, interfaces, and the idioms that make Go code scalable and maintainable."
date: 2025-04-04T05:00:00Z
image: "/images/posts/04.jpg"
categories: ["golang", "software-engineering"]
authors: ["Geoffrey Callaghan"]
tags: ["golang", "types", "interfaces", "slices", "maps"]
draft: false
---

# Chapter 4 — Go’s Type System: Structs, Slices, Maps, and Interfaces

Go’s type system is intentionally minimal, but it is far from simplistic. It is designed to support large-scale engineering without the complexity of inheritance hierarchies, generics-heavy abstractions, or deep metaprogramming. Instead, Go emphasises clarity, composition, and predictable behaviour. Understanding the type system is essential for writing idiomatic, maintainable Go code that scales with teams and production workloads.

## Foundations of Go’s Type System

Go’s types fall into several categories that work together to form a cohesive model:

- basic types such as integers, floats, booleans, and strings
- composite types including arrays, slices, maps, and structs
- reference types such as pointers, slices, maps, channels, and functions
- interfaces that define behaviour rather than structure
- custom named types and type aliases

Go avoids implicit conversions between types. This explicitness prevents subtle bugs and makes code easier to reason about, especially in large teams.

## Structs: The Core Data Model

Structs are Go’s primary mechanism for modelling data. They are simple, explicit, and free of hidden behaviour.

    type User struct {
        Name string
        Age  int
    }

Structs can embed other structs, enabling composition:

    type Admin struct {
        User
        Permissions []string
    }

Embedding is not inheritance. It is a way to reuse fields and methods without creating rigid hierarchies. This keeps systems flexible and avoids the deep class trees common in traditional OOP languages.

### Methods on Structs

Methods can be defined on any named type:

    func (u User) Greet() {
        fmt.Println("Hello,", u.Name)
    }

Go supports both value receivers and pointer receivers. Pointer receivers are used when the method modifies the struct, when the struct is large, or when consistency across methods is desired. This explicitness avoids ambiguity and makes behaviour predictable.

## Arrays and Slices: The Backbone of Collections

Arrays in Go have fixed size and are rarely used directly:

    var a [3]int

Slices, however, are one of the most important types in Go. A slice is a lightweight descriptor containing a pointer to an underlying array, a length, and a capacity.

    numbers := []int{1, 2, 3}

Slices grow dynamically and are passed by reference, making them efficient and flexible.

### Slice Operations

Appending values:

    numbers = append(numbers, 4)

Slicing:

    subset := numbers[1:3]

Understanding how slices share underlying arrays is essential for avoiding subtle bugs and unnecessary allocations. Capacity management becomes important in performance-sensitive code.

## Maps: Fast, Flexible Key–Value Storage

Maps are Go’s built-in hash table type:

    scores := map[string]int{
        "Alice": 90,
        "Bob":   85,
    }

Maps are reference types and safe for concurrent reads but not concurrent writes. Writing to a map from multiple goroutines without synchronisation leads to runtime panics.

### Checking for Existence

Go provides a clear pattern for checking keys:

    value, ok := scores["Alice"]
    if ok {
        fmt.Println("Found:", value)
    }

This avoids exceptions and keeps control flow explicit.

## Interfaces: Behaviour Without Inheritance

Interfaces are one of Go’s most powerful features. They define behaviour, not structure:

    type Writer interface {
        Write([]byte) (int, error)
    }

Any type that implements the required methods satisfies the interface automatically. There is no `implements` keyword. This enables decoupled design and makes testing easier.

### Small Interfaces Are Better

Idiomatic Go encourages small, focused interfaces:

- io.Reader
- io.Writer
- fmt.Stringer

Large, multi-method interfaces are discouraged because they reduce flexibility and increase coupling.

### Interface Values

An interface value contains both a concrete value and the type of that value. Understanding this is essential for avoiding nil pitfalls. An interface holding a typed nil value is not itself nil, which can lead to subtle bugs if not understood.

## Type Assertions and Type Switches

Type assertions extract the underlying concrete type:

    value, ok := w.(Writer)

Type switches provide a clean way to branch on types:

    switch v := i.(type) {
    case string:
        fmt.Println("string:", v)
    case int:
        fmt.Println("int:", v)
    }

These features allow flexible behaviour without resorting to reflection-heavy patterns.

## Custom Types and Aliases

Go allows defining new named types:

    type ID string

This improves clarity and type safety. Type aliases allow renaming types without creating new ones:

    type MyString = string

Aliases are useful for refactoring and API evolution.

## Putting It All Together: Idiomatic Composition

Go’s type system encourages building software from small, composable pieces:

- structs model data
- methods add behaviour
- interfaces define capabilities
- slices and maps manage collections
- composition replaces inheritance

This approach leads to codebases that are easier to maintain, test, and evolve.

The next chapter explores Go’s concurrency model—goroutines, channels, and the patterns that make Go one of the most effective languages for building concurrent and distributed systems.

