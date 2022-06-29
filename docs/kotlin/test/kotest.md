---
layout: post
title: Kotest
parent: 테스트 코드 작성하기
grand_parent: 코틀린
date: 2022-06-29
---

## 테스트 준비하기

### gradle

```gradle
testImplementation("io.kotest:kotest-runner-junit5:${version}")
```

### Intellij Plugin 설치

<https://plugins.jetbrains.com/plugin/14080-kotest>

### Isolation Mode 설정

Kotest는 3개의 Isolation Mode를 제공하고 있다.

- `SingleInstance`
- `InstancePerTest`
- `InstancePerLeaf`

{: .note }
기본값은 `SingleInstance`으로 테스트간 충돌이 발생할 수 있다. 따라서 테스트간 완전한 격리를 위해서는 Isolation Mode를 `InstancePerLeaf`로 설정해야 한다.

```kotlin
internal class MyTests : BehaviorSpec({

    isolationMode = IsolationMode.InstancePerLeaf

    // ...
})
```

## Assertion

```kotlin
"actual" shouldBe "expected"
```

### Exception

```kotlin
val exception = shouldThrow {
    // 예외를 발생시키는 코드
}
```

## Behavior Spec

Given, When, Then 패턴을 간결하게 정의할 수 있다.

## Mockk와 함께 사용하기

## References

- <https://techblog.woowahan.com/5825/>
