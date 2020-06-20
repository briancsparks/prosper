---
title: "When"
date: 2020-05-16T20:50:43-07:00
draft: false
---

## Basic

```kotlin
var animal = "crocodile"
var action: String = ""
when(animal) {
    "cat" -> {
        action = "pet it"
    }
    "dog" -> {
        action = "feed it"
    }
    else -> {
        action = "google it"
    }
}
println("When you meet a $animal you should $action")

```

## Expression

```kotlin
val animal = "dog"
val action = when(animal) {
    "cat" -> {
        "feed it"
    }
    "dog" -> {
        "pet it"
    }
    else -> "google it"
}
println("When you meet a $animal you should $action")
```

## Multiple Keys

```kotlin
val month = "February"
val days = when(month) {
    "January", "March", "May" -> 31
    "February" -> 28
    else -> 30
}
println("The month of $month has $days days")
```

## Capturing the Subject

```kotlin
val name = "Johnboy"
when(val length = name.length) {
    in 1..5 -> println("A name with $length characters is short")
    in 6..10 -> println("A name with $length characters is medium")
    else -> println("A name with $length characters is long")
}
```
