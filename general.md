# Android Architecture, Networking, Threading, and Testing Interview Prep

This document covers essential **Android interview topics** around **Architecture**, **Networking**, **Threading**, and **Testing**.

---

## Table of Contents

- [1. Architecture](#1-architecture)
- [2. Networking](#2-networking)
- [3. Threading and Asynchronous Programming](#3-threading-and-asynchronous-programming)
- [4. Testing](#4-testing)

---

## 1. Architecture

**Q:** What is MVVM and why is it preferred in Android?  
**A:**  
- **Model**: Handles business logic and data sources.
- **ViewModel**: Holds UI-related state and logic, survives configuration changes.
- **View**: Displays data and forwards user actions.
- MVVM promotes separation of concerns and testability.

---

**Q:** What is Clean Architecture?

**A:**
- Divides the app into layers: **Presentation**, **Domain**, **Data**.
- **Domain Layer** is pure Kotlin (no Android dependencies).
- Promotes scalability, testability, and independence between layers.

---

**Q:** What is State Hoisting in Compose architecture?

**A:**
- Moving UI state management to the parent Composable or ViewModel.
- Makes Composables reusable and easier to test.

---

**Q:** Why is Unidirectional Data Flow (UDF) important?

**A:**
- Data flows in a single direction: ViewModel -> UI -> Events -> ViewModel.
- Ensures predictable and maintainable state changes.

---

## 2. Networking

**Q:** What libraries are commonly used for networking in Android?

**A:**
- Retrofit (HTTP Client)
- OkHttp (Underlying HTTP connection management)
- Moshi/Gson (JSON Parsing)

---

**Q:** How do you handle API errors in Retrofit?

**A:**
- Create a custom error handler or wrapper like `ApiResult`.
- Use Retrofit interceptors or check response codes manually.

Example:
```kotlin
if (response.isSuccessful) {
    // handle success
} else {
    // handle error
}
```

---

**Q:** How would you mock a network response for testing?

**A:**
- Use MockWebServer from OkHttp.
- Allows setting fake API responses for integration/UI tests.

---

**Q:** What is an Interceptor in OkHttp?

**A:**
- A component that can observe, modify, and retry requests/responses.
- Used for logging, authentication tokens, or error handling.

---

## 3. Threading and Asynchronous Programming

**Q:** What options are available for multithreading in Android?

**A:**
- Kotlin Coroutines (recommended)
- ExecutorService
- HandlerThread (legacy)
- RxJava (alternative reactive library)

---

**Q:** How do Dispatchers work in Kotlin Coroutines?

**A:**
| Dispatcher | Purpose |
|------------|---------|
| `Dispatchers.Main` | UI-thread operations |
| `Dispatchers.IO` | Network/Disk operations |
| `Dispatchers.Default` | CPU-intensive work (sorting, parsing) |
| `Dispatchers.Unconfined` | Runs on the current thread (rare use) |

---

**Q:** What is structured concurrency?

**A:**
- Children coroutines are tied to the lifecycle of their parent.
- Cancelling a parent scope cancels all its children.
- Prevents leaks and orphan coroutines.

---

**Q:** When would you use `withContext` vs `launch`?

**A:**
- `withContext`: Switch context and wait for result (sequential).
- `launch`: Start a new coroutine for concurrent work.

Example:
```kotlin
withContext(Dispatchers.IO) {
    fetchData()
}
```

---

## 4. Testing

**Q:** What types of testing are used in Android?

**A:**
- **Unit Tests**: Test logic in isolation (e.g., ViewModel, Repository).
- **UI Tests**: Test UI using Espresso or Compose Testing.
- **Integration Tests**: Verify combined modules/components.

---

**Q:** How do you test ViewModel logic?

**A:**
- Use `JUnit` for unit testing ViewModels.
- Use fake repositories or mocked dependencies.

Example:
```kotlin
@Test
fun `test ViewModel state update`() = runTest {
    val viewModel = MyViewModel(FakeRepository())
    viewModel.loadData()
    assertEquals(expected, viewModel.uiState.value)
}
```

---

**Q:** What tools are commonly used for mocking in Android tests?

**A:**
- Mockito
- MockK (Kotlin-specific)
- Fake implementations (manual mocks)

---

**Q:** How do you test asynchronous code in Kotlin?

**A:**
- Use `runTest {}` from kotlinx-coroutines-test.
- Test Dispatchers replaced with TestDispatcher to control coroutine execution.

---

> Prepared for developers aiming for mastery in Android architecture, networking, threading, and testing.

