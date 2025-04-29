# Kotlin Interview Prep

This document covers **Kotlin** specific **mock interview questions and answers**, including tricky topics like **coroutines** and **flows**.

---

## Table of Contents

- [1. Language Basics](#1-language-basics)
- [2. Coroutines](#2-coroutines)
- [3. Flow and Reactive Streams](#3-flow-and-reactive-streams)
- [4. Advanced Kotlin Topics](#4-advanced-kotlin-topics)
- [5. Best Practices](#5-best-practices)

---

## 1. Language Basics

**Q:** What is the difference between `val` and `var`?  
**A:**  
- `val`: Immutable reference (cannot be reassigned).
- `var`: Mutable reference (can be reassigned).

---

**Q:** What is a `sealed class` in Kotlin?  
**A:**  
- A `sealed class` restricts subclassing to the same file.
- Useful for representing restricted types (e.g., `Result`, `State`).
- Helps make `when` expressions exhaustive.

---

**Q:** What is an `inline` function in Kotlin?  
**A:**  
- The compiler copies the function code at the call site.
- Reduces overhead for small functions, especially for lambdas.
- Important for high-performance and functional programming.

---

**Q:** What is the difference between `data class` and `regular class`?

**A:**
- `data class` automatically generates `equals()`, `hashCode()`, `toString()`, `copy()` and `componentN()` functions.
- Great for representing simple data-holding objects.

---

## 2. Coroutines

**Q:** What is a coroutine?  
**A:**  
- Lightweight thread managed by Kotlin runtime.
- Used for asynchronous and non-blocking code.
- Launched in CoroutineScope.

---

**Q:** What is `suspend` in Kotlin?  
**A:**  
- Marks a function that can be paused and resumed later.
- Must be called from another suspend function or a coroutine.

---

**Q:** What is the difference between `launch` and `async`?  
**A:**  
- `launch`: Fire-and-forget coroutine. Returns a `Job`.
- `async`: Returns a `Deferred` that can return a result with `await()`.

Example:
```kotlin
val result = async { getData() }.await()
```

---

**Q:** What is structured concurrency?  
**A:**  
- Coroutines must be tied to a `CoroutineScope`.
- When the scope is cancelled, all child coroutines are also cancelled.
- Prevents memory leaks and untracked jobs.

---

## 3. Flow and Reactive Streams

**Q:** What is `Flow` in Kotlin?  
**A:**  
- A cold asynchronous stream of data that emits values sequentially.
- Built to replace RxJava in modern Kotlin apps.

Example:
```kotlin
flow {
    emit(1)
    emit(2)
}
```

---

**Q:** How is `Flow` different from `LiveData`?  
**A:**  
- `Flow` is a Kotlin coroutine type and cold by default.
- `LiveData` is lifecycle-aware and tied to Android UI components.
- `Flow` is preferred for business/data layer logic.

---

**Q:** What is the difference between `flowOn`, `collect`, and `launchIn`?

| Operator      | Purpose                                         |
|---------------|--------------------------------------------------|
| `flowOn`       | Changes the upstream dispatcher                |
| `collect`      | Terminal operator to collect values from Flow   |
| `launchIn`     | Launches Flow in CoroutineScope automatically  |

---

## 4. Advanced Kotlin Topics

**Q:** What is `delegation` in Kotlin?  
**A:**  
- One class hands off (delegates) certain responsibilities to another class.
- Used for patterns like `by lazy {}`, `ObservableProperty`, or custom delegates.

Example:
```kotlin
val lazyValue: String by lazy {
    println("computed!")
    "Hello"
}
```

---

**Q:** What is `reified` keyword?  
**A:**  
- Used with `inline` functions to keep type information at runtime.
- Useful when you need to check or access the class type inside a generic function.

Example:
```kotlin
inline fun <reified T> getTypeName() = T::class.java.name
```

---

**Q:** Explain `Channel` vs `Flow`.

**A:**
- `Channel`: Hot, push-based stream. Suitable for inter-coroutine communication.
- `Flow`: Cold, pull-based stream. Suitable for data transformations and reactive programming.

---

## 5. Best Practices

**Q:** How do you handle errors in Flows?

**A:**
- Use `catch {}` operator to handle exceptions.
- Use `retry {}` for automatic retries on failure.

Example:
```kotlin
flow {
    emit(fetchData())
}.catch { e ->
    emit(fallbackData())
}.collect { data ->
    // use data
}
```

---

**Q:** How would you cancel a coroutine?

**A:**
- Store the `Job` reference and call `cancel()`.
- Example:
```kotlin
val job = scope.launch { /* work */ }
job.cancel()
```
- Or use `withTimeout {}` to auto-cancel after a time limit.

---

> Prepared for developers serious about Kotlin mastery, coroutines, and reactive programming.

