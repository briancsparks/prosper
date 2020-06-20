---
title: "Aar"
date: 2020-05-16T13:31:40-07:00
draft: false
---

## Convert APK project to AAR

From: <https://developer.android.com/studio/projects/android-library>

1. Open module-level `build.gradle` file.
2. Delete line for `applicationId`.
3. At top of file, replace

```groovy
apply plugin: 'com.android.application'
```

with:

```groovy
apply plugin: 'com.android.library'
```

4. Sync
