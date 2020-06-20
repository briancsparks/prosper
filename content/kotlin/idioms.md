---
title: "Idioms"
date: 2020-05-16T20:07:43-07:00
draft: false
---

## Null

```kotlin
something?.let {
  // something is not null
}
```

## apply

```kotlin
val filter = IntentFilter(ConnectivityManager.CONNECTIVITY_ACTION).apply {
    addAction(Intent.ACTION_AIRPLANE_MODE_CHANGED)
}
registerReceiver(br, filter)
```
