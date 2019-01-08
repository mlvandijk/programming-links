# Terminology

## Programming languages

**Statically typed programming language** - the type of every expression in a program is known at compile time, 
and the compiler can validate that the methods and fields you're trying to access exist on the objects you're using.

**Dynamically typed programming language** - let you define variables and functions that can store or return data of any type 
and resolve the method and field reference at runtime.

**Compiled language** - needs to be compiled before running it.

**Type inference** - the ability of the compiler to determine types from context.

**Key concepts of functional programming:**
1. *First-class functions* - Using functions (pieces of behavior) as values; you can store them in variables, 
pass them as parameters, or return them from other functions.
2. *Immutability* - Using immutable objects, guarantess that their state can't change after creation.
3. *No side effects* - Using pure functions that return the same result given the same inputs and don't modify the state of 
other objects or interact with the outside world.

**Expression** - has a value, which can be used as part of another expression.
**Statement** - is always a top-level element in it's enclosing block doesn't have it's own value.
In Java, all control structures are statements.
In Kotlin, most control structures, except for the loops (`for`, `do`, and `do/while`) are expressions.

Assignments are expressions in Java, and become statements in Kotlin.
