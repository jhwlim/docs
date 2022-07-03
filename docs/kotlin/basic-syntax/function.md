---
layout: post
title: 함수
date: 2022-07-03
parent: 기본 문법
grand_parent: 코틀린
nav_order: 2
---

## 함수 선언하기

`fun` 키워드를 사용하여 함수를 선언한다.

```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}
```

위의 코드는 아래와 같이 표현식 스타일로 작성할 수 있다.

```kotlin
fun sum(a: Int, b: Int): Int = a + b
```

이때, 함수의 반환 타입은 컴파일러가 추론할 수 있기 때문에 반환 타입을 생략할 수 있다.

```kotlin
fun sum(a: Int, b: Int) = a + b
```

{: .warn }
함수의 body `{}`를 사용하여 함수를 선언하는 경우에는 반환 타입이 `Unit`이 아니면 반드시 작성해야 한다.

## Default Arguments

함수의 인자는 기본값을 가질 수 있다.

```kotlin
fun greeting(message: String = "Hello") {
    println(message)
}
```

```kotlin
greeting() // Hello
greeting("Hi") // Hi
```

## Named Arguments

함수를 호출할 때 전달하는 인자의 값을 이름과 직접 지정할 수 있다.

```kotlin
fun reformat(
    str: String,
    normalizeCase: Boolean = true,
    upperCaseFirstLetter: Boolean = true,
    divideByCamelHumps: Boolean = false,
    wordSeparator: Char = ' ',
) { ... }
```

```kotlin
reformat("This is a short String!", upperCaseFirstLetter = false, wordSeparator = '_')
```

## References

- <https://kotlinlang.org/docs/basic-syntax.html#functions>
- <https://kotlinlang.org/docs/functions.html>
