---
title: "LiveData, et. al."
description: "LiveData, et. al."
date: 2020-04-13T05:27:16-07:00
draft: false
---

## LiveData

When you have to fetch or manipulate data asyncronously, use `LifecycleObserver`, `LiveData`,
and `ViewModel`.

* Make sure you are not using the old `android.arch.lifecycle` versions.
* Android Docs
  * [Architecture Doc](https://developer.android.com/topic/libraries/architecture/livedata)
  * [LiveData](https://developer.android.com/reference/androidx/lifecycle/LiveData)
  * [LifecycleObserver](https://developer.android.com/reference/androidx/lifecycle/LifecycleObserver)
  * [Lifecycle](https://developer.android.com/reference/androidx/lifecycle/Lifecycle)
  * [Lifecycle.State](https://developer.android.com/reference/androidx/lifecycle/Lifecycle.State)
  * [ViewModel](https://developer.android.com/reference/androidx/lifecycle/ViewModel)
* Other
  * [Sunflower Article on Medium](https://medium.com/androiddevelopers/introducing-android-sunflower-e421b43fe0c2)
  * The sunflower git repo
    * `git clone https://github.com/googlesamples/android-sunflower`

## Example

```sh
git clone git@github.com:briancsparks/prosper-example-livedata
```

## Codelab

* There is a [codelab](https://codelabs.developers.google.com/codelabs/android-lifecycles/index.html?index=..%2F..%2Findex#4).
* And the associated git repository:
  * `git clone git@github.com:googlecodelabs/android-lifecycles.git`

## LifecycleObserver

Make any component "Lifecycle Aware".

```java

```
