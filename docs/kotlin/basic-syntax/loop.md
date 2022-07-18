---
layout: post
title: 반복문
date: 2022-07-18
parent: 기본 문법
grand_parent: 코틀린
nav_order: 4
---

## for

### `..`는 마지막 element를 포함한다.

```kotlin
for (i in 1..3) {
    println(i)
}
```

출력

```
1
2
3
```

### `until`는 마지막 element를 포함하지 않는다.

```kotlin
for (i in 1 until 3) {
    println(i)
}
```

출력

```
1
2
```

### `step` 만큼 값을 증가시킨다.

```kotlin
for (i in 1..6 step 2) {
    println(i)
}
```

출력

```
1
3
5
```

{: .note }
step은 반드시 양의 정수여야 한다.

### `downTo`는 값을 반복하여 감소시킨다.

```kotlin
for (i in 5 downTo 1 step 2) {
    println(i)
}
```

출력

```kotlin
5
3
1
```

### 배열 또는 컬렉션 반복하기

#### (1) element

```kotlin
val numbers = intArrayOf(1, 2, 3)
for (n in numbers) {
    println(n)
}
```

```
1
2
3
```

#### (2) 인덱스

```kotlin
for (i in numbers.indices) {
    println(i)
}
```

```
0
1
2
```

#### (3) 인덱스, element

```kotlin
for ((i, n) in numbers.withIndex()) {
    println("$i : $n")
}
```

출력

```
0 : 1
1 : 2
2 : 3
```

## while
