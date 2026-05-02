
# Essential SML Code Blocks

A structured roadmap of the core concepts, ordered from foundational to advanced.

---

## 1. Basic Values & Bindings

```sml
val x = 42
val pi = 3.14
val greeting = "hello"
val flag = true
```

---

## 2. Arithmetic & Expressions

```sml
val sum = 3 + 4
val quot = 10 div 3      (* integer division *)
val rem = 10 mod 3
val flt = 3.0 / 2.0      (* real division *)
val concat = "foo" ^ "bar"
```

---

## 3. Function Definitions

```sml
fun square x = x * x
fun add (x, y) = x + y
fun greet name = "Hello, " ^ name
```

---

## 4. Conditionals

```sml
fun abs x = if x < 0 then ~x else x
```

---

## 5. Recursion

```sml
fun factorial 0 = 1
  | factorial n = n * factorial (n - 1)

fun fib 0 = 0
  | fib 1 = 1
  | fib n = fib (n-1) + fib (n-2)
```

---

## 6. Pattern Matching

```sml
fun describe 0 = "zero"
  | describe 1 = "one"
  | describe _ = "many"
```

---

## 7. Tuples

```sml
val point = (3, 4)
fun fst (x, _) = x
fun snd (_, y) = y
```

---

## 8. Lists

```sml
val nums = [1, 2, 3, 4]
val mixed = 0 :: nums          (* cons *)
val joined = [1,2] @ [3,4]     (* append *)

fun len [] = 0
  | len (_::rest) = 1 + len rest

fun myMap _ [] = []
  | myMap f (x::xs) = f x :: myMap f xs
```

---

## 9. Let Expressions (local bindings)

```sml
fun hypotenuse (a, b) =
  let
    val a2 = a * a
    val b2 = b * b
  in
    Math.sqrt (Real.fromInt (a2 + b2))
  end
```

---

## 10. Higher-Order Functions

```sml
fun apply f x = f x
fun compose f g x = f (g x)

val doubled = map (fn x => x * 2) [1,2,3]
val evens   = List.filter (fn x => x mod 2 = 0) [1,2,3,4]
val total   = foldl (fn (x, acc) => x + acc) 0 [1,2,3,4]
```

---

## 11. Anonymous Functions (lambdas)

```sml
val square = fn x => x * x
val add    = fn (x, y) => x + y
```

---

## 12. Algebraic Data Types (datatypes)

```sml
datatype shape = Circle of real
               | Rect of real * real

fun area (Circle r)    = Math.pi * r * r
  | area (Rect (w, h)) = w * h
```

---

## 13. Option Type

```sml
fun safeDiv (_, 0) = NONE
  | safeDiv (x, y) = SOME (x div y)

fun showResult NONE     = "error"
  | showResult (SOME v) = Int.toString v
```

---

## 14. Records

```sml
val person = { name = "Alice", age = 30 }
val name   = #name person
```

---

## 15. Mutual Recursion

```sml
fun isEven 0 = true
  | isEven n = isOdd (n - 1)
and isOdd 0  = false
  | isOdd n  = isEven (n - 1)
```

---

## 16. Exceptions

```sml
exception DivByZero

fun safeDivide (_, 0) = raise DivByZero
  | safeDivide (x, y) = x div y

val result = safeDivide (10, 2) handle DivByZero => ~1
```

---

## 17. Signatures & Structures (modules)

```sml
signature STACK = sig
  type 'a stack
  val empty  : 'a stack
  val push   : 'a * 'a stack -> 'a stack
  val pop    : 'a stack -> 'a * 'a stack
end

structure Stack : STACK = struct
  type 'a stack = 'a list
  val empty       = []
  fun push (x, s) = x :: s
  fun pop (x::s)  = (x, s)
    | pop []      = raise Empty
end
```

---

## Learning Order Recommendation

|Phase|Topics|
|---|---|
|**Start**|Values, arithmetic, functions, conditionals|
|**Core**|Recursion, pattern matching, lists, let|
|**Intermediate**|HOFs, lambdas, datatypes, option|
|**Advanced**|Records, exceptions, mutual recursion, modules|

> **Key insight:** The most SML-specific things to internalize are **pattern matching**, **algebraic datatypes**, and the **type system** — these are what make SML distinct from most other languages.
