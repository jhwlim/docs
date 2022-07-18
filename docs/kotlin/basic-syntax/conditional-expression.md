---
layout: post
title: 조건식
date: 2022-07-18
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

### 표현식이다.

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

when은 여러가지 케이스에 대한 분기처리를 위한 조건식을 정의한다.

```kotlin
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> { // (1)
        print("x is neither 1 nor 2") // (2)
    }
}
```

- (1) if와 동일하게 block 으로 표현할 수 있다.
- (2) block의 마지막 표현식을 반환한다.

### 표현식이다.

when 역시 표현식이기 때문에 when 자체를 반환할 수 있다.

```kotlin
fun describe(obj: Any): String =
    when (obj) {
        1 -> "One"
        "Hello" -> "Greeting"
        is Long -> "Long"
        !is String -> "Not a string"
        else -> "Unknown"
    }
```

### 표현식으로 사용되는 경우 else는 반드시 작성해야 하지만, enum 또는 sealed 클래스를 사용하는 경우 생략할 수 있다.

else는 어떠한 분기에 해당하지 않으면 실행된다.
이때, when이 표현식으로 사용된다면 else는 필수로 작성해야 한다.
단, enum 클래스와 sealed 클래스는 가능한 모든 케이스에 대한 내용을 작성하고 있다면 else는 작성하지 않아도 된다.

```kotlin
enum class Color {
    RED, GREEN, BLUE
}

when (getColor()) { // (1)
    Color.RED -> println("red")
    Color.GREEN -> println("green")
    Color.BLUE -> println("blue")
}

when (getColor()) { // (2)
    Color.RED -> println("red")
    else -> println("not red")
}
```

- (1) 가능한 모든 케이스에 대하여 커버하고 있기 때문에 else를 작성하지 않아도 된다.
- (2) else를 작성하지 않으면 컴파일 에러가 발생한다.

### 콤마(,)를 사용하여 여러 개의 조건식을 한 번에 처리할 수 있다.

```kotlin
when (x) {
    0, 1 -> println("x == 0 or x == 1")
    else -> println("otherwise")
}
```

### `in` 또는 `!in` 을 사용하여 범위에 대하여 조건을 처리할 수 있다.

```kotlin
val x = getNumber()
val validNumbers = intArrayOf(30, 40, 50)
when (x) {
    in 1..10 -> println("x is in the range")
    in validNumbers -> println("x is valid")
    !in 10..20 -> println("x is outside the range")
    else -> println("none of the above")
}
```

### `is` 또는 `!is`를 사용하여 특정 타입에 대하여 처리할 수 있다.

```kotlin
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}
```

### when의 인자는 없을 수도 있다.

```kotlin
when {
    x.isOdd() -> println("x is odd")
    y.isEven() -> println("y is even")
    else -> println("x+y is odd")
}
```

## References

- <https://kotlinlang.org/docs/basic-syntax.html>
- <https://kotlinlang.org/docs/control-flow.html>
