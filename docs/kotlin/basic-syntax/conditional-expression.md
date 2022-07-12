---
layout: post
title: 조건식
date: 2022-07-13
parent: 기본 문법
grand_parent: 코틀린
nav_order: 3
---

## if

```kotlin
fun maxOf(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}
```

{: .note }
코틀린에서 if ~ else 는 **표현식(Expression)**이다.

아래와 같이 if ~ else 자체를 반환할 수 있다.

```kotlin
fun maxOf(a: Int, b: Int): Int {
    return if (a > b) {
        a
    } else {
        b
    }
}
```

위의 코드는 아래와 같이 표현식 스타일로 작성할 수 있다.

```kotlin
fun maxOf(a: Int, b: Int) = if (a > b) a else b
```

if ~ else 는 표현식이기 때문에 변수에 값을 할당할 때에도 사용할 수 있다. 이러한 이유로 **코틀린은 삼항 연산자가 없다.**

```kotlin
val max = if (a > b) a else b
```

## when

## References

- <https://kotlinlang.org/docs/basic-syntax.html>
- <https://kotlinlang.org/docs/control-flow.html>
