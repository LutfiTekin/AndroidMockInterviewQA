---

###Jetpack Compose Interview Prep

This document covers Jetpack Compose specific mock interview questions and answers.


---

Table of Contents

1. State Management

2. Layouts and UI Components

3. Effects and Side Effects

4. Best Practices

5. Performance and Optimization

6. Advanced Topics



---

1. State Management

Q: How is state managed in Jetpack Compose?
A:

Compose uses a declarative model: UI updates automatically when state changes.

State can be managed using remember, mutableStateOf, rememberSaveable, StateFlow, or ViewModel.

Best practice: state hoisting — pass state down, events up.



---

Q: What is the difference between remember and rememberSaveable?
A:

remember: Caches values across recompositions but loses them during configuration changes.

rememberSaveable: Persists values across recompositions and configuration changes (e.g., rotation).



---

Q: What is recomposition in Compose?
A:

Recomposition is when a Composable function re-executes because the data it depends on has changed.

Compose tries to minimize work by skipping recomposition when inputs haven't changed.



---

2. Layouts and UI Components

Q: What’s the difference between Row, Column, and Box?
A:

Row: Places children horizontally.

Column: Places children vertically.

Box: Stacks children; last child drawn on top.



---

Q: How would you implement a list in Compose?
A:

Use LazyColumn for vertical scrolling.


LazyColumn {
    items(listOfItems) { item ->
        Text(text = item.name)
    }
}

Items are composed only when they are visible.



---

Q: How would you make a scrollable screen if you don't have a list?
A:

Use Column inside Modifier.verticalScroll(rememberScrollState()).


Example:

Column(
    modifier = Modifier.verticalScroll(rememberScrollState())
) {
    // Child composables
}


---

3. Effects and Side Effects

Q: What is LaunchedEffect used for?
A:

Runs suspend functions tied to the lifecycle of a composable.

Cancels and restarts if keys change.


Example:

LaunchedEffect(key1 = true) {
    delay(1000)
    println("Delayed Action")
}


---

Q: What’s the difference between LaunchedEffect, SideEffect, and DisposableEffect?


---

4. Best Practices

Q: How would you prevent unnecessary recompositions?
A:

Keep Composables small and focused.

Use remember to cache calculations.

Use @Stable, @Immutable annotations when needed.



---

Q: How would you manage UI state across configuration changes?
A:

Store UI state inside a ViewModel.

Expose state via StateFlow or LiveData.

Use rememberSaveable for small, UI-only states.



---

5. Performance and Optimization

Q: How would you optimize a large list in Compose?
A:

Use LazyColumn/LazyRow.

Provide stable keys inside items() to help Compose track and reuse items.


Example:

LazyColumn {
    items(itemsList, key = { it.id }) { item ->
        Text(text = item.name)
    }
}


---

Q: Why could infinite recomposition happen, and how would you avoid it?
A:

It happens if you modify state directly inside a Composable, triggering endless recomposition.

Avoid by isolating side-effects inside LaunchedEffect, event handlers, or ViewModel.



---

6. Advanced Topics

Q: What is state hoisting in Jetpack Compose?
A:

Moving state up to a parent Composable so child Composables are stateless and reusable.

Follows the principle: pass state down, events up.



---

Q: How do you integrate existing Views in Compose?
A:

Use AndroidView to embed classic Views inside Compose.


Example:

AndroidView(factory = { context ->
    TextView(context).apply { text = "Old View in Compose" }
})


---

Q: How do you embed a Compose screen inside an XML layout?
A:

Use ComposeView in the XML layout:


<androidx.compose.ui.platform.ComposeView
    android:id="@+id/composeView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>

Then set content in Activity or Fragment:


composeView.setContent {
    Text("Hello Compose inside XML!")
}


---



> Prepared for serious Android developers moving into modern UI with Jetpack Compose.

