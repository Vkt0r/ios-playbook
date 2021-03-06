# Match UI test with implementation

* Author(s): Sergey Shulga
* Review Manager: Ilya Puchka, David Rodrigues, Olivier Halligon

## Introduction

The goal is to match the implementation of a feature with a corresponding UI test so we could run it on CI

## Motivation

Lately we had quite a lot of UI automation test failures which decrease the speed which we can make a release and distracts automation QAs to do this unnecessary work.

## Proposed solution

I believe that we can achieve that by adding some kind of mark style comments that can be recognized by Danger which would  be able to trigger the corresponding UI test
e.g

```swift
// UITestCase: SomeFeature
final class SomeViewModel {}

// UITestCase: SomeFeature
final class SomeRenderer { }
```

And if `SomeFeature` is missing or spelled wrong then it would fail on CI, for example.

## Impact on existing codebase

No impact on the existing codebase. These changes can be made gradually by having a Danger rule to remind people to mark `ViewModel` and `Renderer` files with the appropriate `UITestCase` marker.

## Alternatives considered

N/A
