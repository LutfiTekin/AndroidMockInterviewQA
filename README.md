# AndroidMockInterviewQA

Absolutely!
Here’s a clean README.md version, formatted properly so you can push it straight to GitHub and share with your friend:

Android (Kotlin + Jetpack Compose) Mock Interview Prep 

This document contains questions and answers to prepare for a mock Android interview focusing on Kotlin and Jetpack Compose.

1. Kotlin Language Basics 

Q: What are some key differences between val and var in Kotlin?
A:

val defines an immutable reference (like final in Java). var defines a mutable reference and can be reassigned. 

Q: What is a sealed class in Kotlin, and when would you use it?
A:

A sealed class restricts class inheritance to a known set. Useful for representing limited types like Result, State, etc. 2. Jetpack Compose Basics 

Q: How is state managed in Jetpack Compose?
A:

State is managed declaratively. Use remember, rememberSaveable, StateFlow, or a ViewModel. Practice state hoisting: pass state down, events up. 

Q: What is remember vs rememberSaveable?
A:

remember: Stores value during recomposition; lost on config change. rememberSaveable: Persists value across configuration changes. 3. UI Components and Layouts 

Q: What’s the difference between Row, Column, and Box?
A:

Row: Horizontal layout. Column: Vertical layout. Box: Stacks children on top of each other. 

Q: How would you make a scrollable list in Compose?
A:

Use LazyColumn. LazyColumn { items(listOfItems) { item -> Text(text = item.name) } } 4. Architecture 

Q: How does MVVM work with Jetpack Compose?
A:

Model: Data and business logic. ViewModel: Holds and exposes UI state. View (Compose): Observes state and rebuilds automatically. 

Q: Why is Unidirectional Data Flow (UDF) important?
A:

Makes apps predictable. Easy debugging and testing. ViewModel → State → Composable → Events → ViewModel. 5. Advanced Topics 

Q: What is a SideEffect?
A:

Used to perform side-effects after a successful recomposition. 

Q: How does rememberCoroutineScope work?
A:

Provides a lifecycle-safe CoroutineScope tied to the composable. val scope = rememberCoroutineScope() Button(onClick = { scope.launch { /* suspend functions */ } }) 6. Mock Tricky Questions Q1. How would you handle screen rotation in Compose? Move UI state to ViewModel. Use rememberSaveable when local. ViewModel survives configuration changes. Q2. What does "declarative UI" really mean? UI = function of state. You describe what the UI should be, not how to change it. Q3. How would you optimize large lists in Compose? Use LazyColumn/LazyRow. Use key for efficient item reuse. Keep items stable and lightweight. Q4. When should you NOT use Jetpack Compose? Heavy native Views (WebView, Maps). Very tight deadlines with no Compose experience. Very old device support required. Q5. What happens if you run long tasks directly inside a Composable? May cause UI freezes and ANRs. Use LaunchedEffect for safe suspending operations. Q6. How to implement error handling elegantly? Use a sealed UiState (Loading, Success, Error). Update UI based on current state. Q7. What is recomposition in Compose? Re-running Composables when input state changes. Manage with remember, @Stable, and keeping Composables small. Q8. Differences between LaunchedEffect, SideEffect, and DisposableEffect Q9. Why can infinite recomposition happen? Mutating state directly inside the Composable body without control. Must isolate side effects (use LaunchedEffect, event handlers). Q10. How to mix XML layouts and Compose? Use ComposeView to embed Compose into XML. Use AndroidView to embed XML-based Views inside Compose. Gradual migration strategy is best. 



