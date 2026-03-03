# SwiftUI Basics (Layman's Terms)

## struct (Simple Copy Box)

A `struct` is a **copy box**.

If you give it to someone, they get their **own copy**.

If they change it → your original stays the same.

Example idea: You write a number on paper. You photocopy it. Your friend
changes their copy. Your paper doesn't change.

👉 In SwiftUI, **Views are structs**.

------------------------------------------------------------------------

## class (Shared Object)

A `class` is a **shared object**.

If two people hold it and one changes it → both see the change.

Like a shared Google Doc.

Used when: - You want shared data - You want one source of truth

------------------------------------------------------------------------

# @State

Simple meaning:

> "This view owns this small piece of data."

Example:

``` swift
@State var count = 0
```

This means: - This screen owns `count` - If it changes → the screen
redraws

Use it for: - Simple numbers - Toggle on/off - Text field values

Think of it like: 📒 Your own notebook in your room.

------------------------------------------------------------------------

# @StateObject

Simple meaning:

> "This view owns a big object."

Usually used with a `class` (ViewModel).

Example:

``` swift
@StateObject var viewModel = CounterViewModel()
```

This means: - This screen created the object - This screen is
responsible for it - If the object changes → update UI

Think of it like: 👨‍💼 You hired a manager for your store. You own that
manager.

------------------------------------------------------------------------

# @ObservedObject

Simple meaning:

> "I don't own this object. I'm just watching it."

Example:

``` swift
@ObservedObject var viewModel: CounterViewModel
```

This means: - The object was created somewhere else - I'm just observing
it - If it changes → update UI

Think of it like: 📺 Watching a live TV broadcast. You didn't create the
show. You're just watching it.

------------------------------------------------------------------------

# @Binding

Simple meaning:

> "I don't own this value. I'm borrowing it."

Used when: - Parent owns data - Child needs to change it

Example:

Parent:

``` swift
@State var count = 0
ChildView(count: $count)
```

Child:

``` swift
@Binding var count: Int
```

The `$` means: "I'm passing a connection, not a copy."

Think of it like: 🎮 A remote control to someone else's TV.

You don't own the TV. But you can change the channel.

------------------------------------------------------------------------

# Quick Ownership Table

  Thing             Owns Data?        Shared?
  ----------------- ----------------- -----------
  struct            No (copy)         ❌
  class             Yes (reference)   ✅
  @State            Yes               ❌
  @StateObject      Yes               ✅
  @ObservedObject   No                ✅
  @Binding          No                Connected
