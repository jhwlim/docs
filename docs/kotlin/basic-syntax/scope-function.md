---
layout: post
title: Scope 함수
date: 2021-06-24
parent: 기본 문법
grand_parent: 코틀린
---

{: .info }
_이 글은 [코틀린 공식 문서](https://kotlinlang.org/docs/scope-functions.html)를 참고하여 작성된 글 입니다._

<br>

일시적인 영역을 형성하는 함수를 **Scope 함수**라고 한다.

Scope 함수에는 `let`, `run`, `with`, `apply`, `also` 가 있다.

<br>

**Scope 함수를 활용하면 코드를 간결하게 작성할 수 있다.**

```kotlin
data class Person(
    var name: String,
    var age: Int = 0,
    var city: String = ""
) {
    fun moveto(newCity: String) { city = newCity }
    fun incrementAge() { age++ }
}
```

Scope 함수 없이 일반적으로 코드를 작성하면 아래와 같이 작성할 수 있다.

```kotlin
val alice = Person("Alice", 20, "Amsterdam")
println(alice) // Person(name=Alice, age=20, city=Amsterdam)
alice.moveto("London")
alice.incrementAge()
println(alice) // Person(name=Alice, age=21, city=London)
```

Scope 함수 활용하면 아래와 같이 좀 더 간결하게 코드를 작성할 수 있다.

```kotlin
Person("Alice", 20, "Amsterdam").let {
    println(it) // Person(name=Alice, age=20, city=Amsterdam)
    it.moveto("London")
    it.incrementAge()
    println(it) // Person(name=Alice, age=21, city=London)
}
```

{: .warn }
Scope 함수는 코드를 더 간결하게 하거나, method chain을 활용할 수 있는 장점이 있지만, 과도하게 사용하면 오히려 코드를 더 복잡하게 만들 수 있다.

## let

```kotlin
public inline fun <T, R> T.let(block: (T) -> R): R {
    return block(this)
}
```

- 객체 참조 방법 : `it`
- 반환 값 : 람다 결과

### 하나 이상의 함수를 연쇄적으로 호출할 때

```kotlin
val numbers = listOf("one", "two", "three", "four", "five")

numbers.map { it.length }
    .filter { it > 3 }
    .let {
        println(it) // 3
    }
```

### non-null 일 때에만 코드 블록을 실행할 때

```kotlin
val str: String? = "Hello"
val length = str?.let {
    // `?.`를 사용하지 않아도 된다.
    println(it.length) // 5
}
```

### 일회성으로 제한된 영역에서 로컬 변수를 사용하고 싶을 때

```kotlin
val numbers = listOf("one", "two", "three", "four")
val modifiedFirstItem = numbers.first()
    .let { firstItem ->
        if (firstItem.length >= 5) firstItem else "!$firstItem!"
    }.uppercase()
println(modifiedFirstItem) // !ONE!
```

## with

```kotlin
public inline fun <T, R> with(receiver: T, block: T.() -> R): R {
    return receiver.block()
}
```

- 객체 참조 방법 : `this`
- 반환 값 : 람다 결과

{: .note }
`with`는 확장 함수가 아니기 때문에 `this`에 해당하는 객체를 매개변수로 전달해야 한다.

### 람다 결과를 제공하지 않고 사용할 때

```kotlin
val numbers = listOf("one", "two", "three")
with(numbers) {
    println(this.size) // 3
}
```

### Helper Object

```kotlin
val numbers = listOf("one", "two", "three")
val firstAndLast = with(numbers) {
    "${this.first()}, ${this.last()}"
}
println(firstAndLast) // one, three
```

## run

```kotlin
public inline fun <T, R> T.run(block: T.() -> R): R {
	return block()
}
```

- 객체 참조 방법 : `this`
- 반환 값 : 람다 결과

### 초기화와 동시에 결과 값을 반환해야 할 때

```kotlin
val service = MultiportService(
    url = "https://example.kotlinlang.org",
    port = 80
)

val result = service.run {
    this.port = 8080
    this.query(this.prepareRequest() + " to port ${this.port}")
}
println(result) // Result for query 'Default request to port 8080'
```

`this`는 생략할 수 있기 때문에 아래와 같이 간결하게 작성할 수 있다.

```kotlin
val result = service.run {
    port = 8080
    query(prepareRequest() + " to port ${port}")
}
```

`let`을 사용하면 아래와 같이 좀 더 코드가 길어진다.

```kotlin
val result = service.let {
    it.port = 8080
    it.query(it.prepareRequest() + " to port ${it.port}")
}
```

### 확장 함수 대신 사용하기

```kotlin
val hexNumberRegex = run {
    val digits = "0-9"
    val hexDigits = "A-Fa-f"
    val sign = "+-"

    Regex("[$sign]?[$digits$hexDigits]+") // 16진수에 대한 정규표현식
}

for (match in hexNumberRegex.findAll("+123 -FFFF !%*& 88 XYZ")) {
    println(match.value)
}
```

출력

```
+123
-FFFF
88
```

## apply

```kotlin
public inline fun <T> T.apply(block: T.() -> Unit): T {
    block()
    return this
}
```

- 객체 참조 방법 : `this`
- 반환 값 : `this` 자기 자신

### Object Configuration

```kotlin
val adam = Person("Adam").apply {
    this.age = 32
    this.city = "London"
}
println(adam) // Person(name=Adam, age=32, city=London)
```

## also

```kotlin
public inline fun <T> T.also(block: (T) -> Unit): T {
    block(this)
    return this
}
```

- 객체 참조 방법 : `it`
- 반환 값 : `it` 자기 자신

### 함수의 인자로 활용할 때

```kotlin
val numbers = mutableListOf("one", "two", "three")
numbers
    .also { println(it) } // [one, two, three]
    .add("four")
println(numbers) // [one, two, three, four]
```

## Scope 함수 비교

| Function | 객체 참조 방법 |    반환 값     | 확장 함수 여부 |
| :------: | :------------: | :------------: | :------------: |
|  `let`   |      `it`      | Lambda Result  |      Yes       |
|  `run`   |     `this`     | Lambda Result  |      Yes       |
|  `run`   |       -        | Lambda Result  |       No       |
|  `with`  |     `this`     | Lambda Result  |       No       |
| `apply`  |     `this`     | Context Object |      Yes       |
|  `also`  |      `it`      | Context Object |      Yes       |

### Context Object

Scope 함수를 실행하고 있는 객체를 말하며, `this`(Lambda Receiver) 이나 `it`(Lambda Argument) 키워드를 이용하여 접근할 수 있다. 이때, `this`와 `it` 은 동일한 기능을 수행한다.

|      | `this`                                                           | `it`                                                                        |
| :--: | :--------------------------------------------------------------- | :-------------------------------------------------------------------------- |
| 장점 | 생략할 수 있다.                                                  | - `this`보다 짧고 읽기 쉽다. <br> - `it` 대신에 다른 이름을 사용할 수 있다. |
| 단점 | `this`를 생략하면 외부의 변수나 함수와 구별하기 어렵다.          | 생략할 수 없다.                                                             |
| 활용 | **`this`의 대상이 되는 객체의 함수를 호출하거나 값을 수정할 때** | **함수 호출의 인자로 활용되거나, 블록 내부에 많은 변수들을 사용할 때**      |

### Lambda Result

매개변수로 전달한 람다 함수의 결과를 말한다.

**chaining 형태로 method를 호출할 때, 사용할 수 있다.**

또한, **람다 결과를 무시하고 일시적인 scope를 생성하는 용도로 활용할 수 있다.**

```kotlin
val numbers = listOf("one", "two", "three")
with(numbers) {
    val firstItem = this.first()
    val lastItem = this.last()
    println("$firstItem, $lastItem") // one, three
}
```

## References

- <https://kotlinlang.org/docs/scope-functions.html>
