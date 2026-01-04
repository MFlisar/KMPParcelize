[![Maven Central](https://img.shields.io/maven-central/v/io.github.mflisar.kmpparcelize/library?style=for-the-badge&color=blue)](https://central.sonatype.com/artifact/io.github.mflisar.kmpparcelize/library) ![API](https://img.shields.io/badge/api-23%2B-brightgreen.svg?style=for-the-badge) ![Kotlin](https://img.shields.io/github/languages/top/MFlisar/KMPParcelize.svg?style=for-the-badge&amp;color=blueviolet) ![Kotlin Multiplatform](https://img.shields.io/badge/Kotlin_Multiplatform-blue?style=for-the-badge&amp;label=Kotlin) [![License](https://img.shields.io/github/license/MFlisar/KMPParcelize?style=for-the-badge)](https://github.com/MFlisar/KMPParcelize/blob/main/LICENSE)
# KMPParcelize
![Android](https://img.shields.io/badge/android-3DDC84?style=for-the-badge) ![iOS](https://img.shields.io/badge/ios-A2AAAD?style=for-the-badge) ![Windows](https://img.shields.io/badge/windows-5382A1?style=for-the-badge) ![macOS](https://img.shields.io/badge/macos-B0B0B0?style=for-the-badge) ![WebAssembly](https://img.shields.io/badge/wasm-624DE7?style=for-the-badge)

This library provides `parcelize` annotations that can be used inside `commonMain` source sets.

Following is provided inside the `com.michaelflisar.parcelize` package:

<!-- snippet: Parcelize -->
```kt
package com.michaelflisar.parcelize

expect interface Parcelable

@Target(AnnotationTarget.CLASS)
@Retention(AnnotationRetention.BINARY)
expect annotation class Parcelize()

@Target(AnnotationTarget.PROPERTY)
@Retention(AnnotationRetention.SOURCE)
expect annotation class IgnoredOnParcel()

@Target(AnnotationTarget.TYPE)
@Retention(AnnotationRetention.BINARY)
expect annotation class RawValue
```
<!-- endSnippet -->

The actual implementations for android looks as following:

<!-- snippet: Parcelize2 -->
```kt
package com.michaelflisar.parcelize

actual typealias Parcelable = android.os.Parcelable
actual typealias Parcelize = kotlinx.parcelize.Parcelize
actual typealias IgnoredOnParcel = kotlinx.parcelize.IgnoredOnParcel
actual typealias RawValue = kotlinx.parcelize.RawValue
```
<!-- endSnippet -->

# :information_source: Table of Contents

- [Supported Platforms](#computer-supported-platforms)
- [Setup](#wrench-setup)
- [Usage](#rocket-usage)
- [Other Libraries](#bulb-other-libraries)
- [API Documentation](#books-api-documentation)

# :computer: Supported Platforms

| Module | android | iOS | windows | macOS | wasm |
|---|---|---|---|---|---|
| Library | ✅ | ✅ | ✅ | ✅ | ✅ |

# :wrench: Setup

<details>

<summary>Dependencies</summary>

<br>

Simply add the dependencies inside your **build.gradle.kts** file.

```kotlin
val kmpparcelize = "<LATEST-VERSION>"

implementation("io.github.mflisar.kmpparcelize:library:${kmpparcelize}")
```

</details>

<details>

<summary>Version Catalogue</summary>

<br>

Define the dependencies inside your **libs.versions.toml** file.

```toml
[versions]

kmpparcelize = "<LATEST-VERSION>"

[libraries]

library = { module = "io.github.mflisar.kmpparcelize:library", version.ref = "kmpparcelize" }
```

And then use the definitions in your projects **build.gradle.kts** file like following:

```shell
implementation(libs.library)
```

</details>

# :rocket: Usage

Simple use the provided annotations instead of the one from `androidx` and you are done.

# :books: API Documentation

Check out the [API documentation](https://MFlisar.github.io/KMPParcelize/).

# :bulb: Other Libraries

You can find more libraries (all multiplatform) of mine that all do work together nicely [here](https://github.com/MFlisar/MyLibraries).
