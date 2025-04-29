# Android Fundamentals Interview Prep

This document covers **Android Fundamentals** for interviews, focusing on core concepts every Android developer must know.

---

## Table of Contents

- [1. Activities and Fragments](#1-activities-and-fragments)
- [2. Intents and Broadcasts](#2-intents-and-broadcasts)
- [3. Services and Background Work](#3-services-and-background-work)
- [4. Storage and Permissions](#4-storage-and-permissions)
- [5. Jetpack Components](#5-jetpack-components)

---

## 1. Activities and Fragments

**Q:** What is an Activity?

**A:**
- A single, focused screen with a user interface.
- Manages lifecycle events (`onCreate`, `onStart`, `onResume`, etc.).

---

**Q:** What is a Fragment?

**A:**
- A reusable portion of a user interface or behavior within an Activity.
- Must be attached to an Activity to exist.

---

**Q:** What are the important lifecycle methods of a Fragment?

**A:**
- `onAttach()`
- `onCreateView()`
- `onViewCreated()`
- `onStart()`
- `onResume()`
- `onPause()`
- `onStop()`
- `onDestroyView()`
- `onDetach()`

---

**Q:** How does Fragment differ from Activity?

**A:**
- Fragment must be hosted by an Activity.
- Fragment has its own lifecycle tied to the host Activity lifecycle.
- Fragments allow modular UIs within a single Activity.

---

## 2. Intents and Broadcasts

**Q:** What is an Intent in Android?

**A:**
- Messaging object used to request an action from another component.
- Can be explicit (target specific component) or implicit (let system choose).

---

**Q:** What is the difference between explicit and implicit Intent?

**A:**
- **Explicit Intent**: Target specific component (e.g., open Activity B).
- **Implicit Intent**: System chooses the appropriate component (e.g., open web page).

---

**Q:** What is a BroadcastReceiver?

**A:**
- Listens for system-wide broadcast messages (e.g., battery low, connectivity change).
- Can be registered statically in `AndroidManifest.xml` or dynamically at runtime.

---

## 3. Services and Background Work

**Q:** What is a Service in Android?

**A:**
- Component that runs in the background to perform long-running operations.
- No user interface.

---

**Q:** What are the types of Services?

**A:**
- **Started Service**: Continues to run until stopped.
- **Bound Service**: Provides a client-server interface for components to interact.
- **Foreground Service**: Displays a persistent notification and is less likely to be killed.

---

**Q:** What is WorkManager?

**A:**
- A Jetpack library for deferrable, guaranteed background work.
- Supports constraints like network availability, charging status.
- Replaces older APIs like JobScheduler and AlarmManager.

---

## 4. Storage and Permissions

**Q:** What storage options are available in Android?

**A:**
- SharedPreferences (key-value pairs)
- Internal Storage (private files)
- External Storage (public files, needs permissions)
- Databases (SQLite, Room)

---

**Q:** How do runtime permissions work?

**A:**
- Dangerous permissions must be requested at runtime (e.g., location, camera).
- Use `ActivityCompat.requestPermissions` or Jetpack libraries like `Accompanist` or `Permission APIs`.

---

## 5. Jetpack Components

**Q:** What is ViewModel?

**A:**
- Lifecycle-aware class that holds and manages UI-related data.
- Survives configuration changes.

---

**Q:** What is LiveData?

**A:**
- Lifecycle-aware observable data holder.
- Automatically updates UI components when data changes.

---

**Q:** What is Room Database?

**A:**
- SQLite abstraction layer.
- Provides compile-time query verification, entities, DAOs, and migrations.

Example:
```kotlin
@Entity
data class User(
    @PrimaryKey val id: Int,
    val name: String
)
```

---

**Q:** What is Navigation Component?

**A:**
- Handles navigation between destinations (Activities, Fragments, Composables).
- Supports safe arguments, deep linking, and back stack management.

---

> Prepared for developers mastering Android's core building blocks and system components.

