---
layout: post
title: 가이드
date: 2021-06-21
permalink: /guide/
---

## 제목

```md
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

{: .no_toc }
# H1
{: .no_toc }
## H2
{: .no_toc }
### H3
{: .no_toc }
#### H4
{: .no_toc }
##### H5
{: .no_toc }
###### H6
{: .no_toc }

## 텍스트 스타일

```md
**굵게**, __굵게__
*기울게*, _기울게_
<u>밑줄</u>
~~취소선~~
```

**굵게**, __굵게__

*기울게*, _기울게_

<u>밑줄</u>

~~취소선~~

## 목록

- Parent 1
    - Child 1
    - Child 2
    - Child 3
- Parent 2
    1. Child 1
    2. Child 2
    3. Child 3

## 인용

```md
> Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 
```

> Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

## 텍스트 컨테이너

```md
{: .note }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

{: .warn }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

{: .info }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 
```

{: .note }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

{: .warn }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

{: .info }
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 

## 링크

```md
[구글](https://www.google.com)

[Home](./)

[About](../about)
```

[구글](https://www.google.com)

[Home](/)

[About](../about)

## 버튼

```md
<button type="button" name="button" class="btn">Button1</button>

[Button2](http://example.com/){: .btn }

[Button3](http://example.com/){: .btn .btn-purple }
[Button4](http://example.com/){: .btn .btn-blue }
[Button5](http://example.com/){: .btn .btn-green }

[Button6](http://example.com/){: .btn .btn-outline }

[Button7](http://example.com/){: .btn .btn-purple .mr-2 }
[Button8](http://example.com/){: .btn .btn-blue .fs-8 }

[Button9](http://example.com/){: .btn .btn-blue .fs-3 }
```

<button type="button" name="button" class="btn">Button1</button>

[Button2](http://example.com/){: .btn }

[Button3](http://example.com/){: .btn .btn-purple }
[Button4](http://example.com/){: .btn .btn-blue }
[Button5](http://example.com/){: .btn .btn-green }

[Button6](http://example.com/){: .btn .btn-outline }

[Button7](http://example.com/){: .btn .btn-purple .mr-2 }
[Button8](http://example.com/){: .btn .btn-blue .fs-8 }

[Button9](http://example.com/){: .btn .btn-blue .fs-3 }

## 이미지

```md
![sample-1](https://cdn.pixabay.com/photo/2017/08/10/08/47/laptop-2620118_1280.jpg)

![sample-2](/assets/images/guide/sample.jpg)
```

![sample-1](https://cdn.pixabay.com/photo/2017/08/10/08/47/laptop-2620118_1280.jpg)

![sample-2](/assets/images/guide/sample.jpg)

## 표

```md
|기본 정렬|왼쪽 정렬|가운데 정렬|오른쪽 정렬|
|---|:--|:-:|--:|
|생생하며,|많이 무엇을 과실이 사랑의 뭇 사랑의 아니다.|것은 그들의 피가 거친 있다.|황금시대의 무엇이 곳으로 더운지라 그리하였는가?|
|미인을 끓는 것이다.|얼마나 이상 든 아니한 소리다.|보라, 그리하였는가?|우리는 가치를 아니한 같은 새가 인생에 보라.|
|이것은 인간의 발휘하기 힘있다.|별과 생생하며,|얼음이 천자만홍이 따뜻한 더운지라 풀이 구하지 타오르고 이것이다.|것은 사는가 타오르고 노년에게서 봄바람이다.|
```

|기본 정렬|왼쪽 정렬|가운데 정렬|오른쪽 정렬|
|---|:--|:-:|--:|
|생생하며,|많이 무엇을 과실이 사랑의 뭇 사랑의 아니다.|것은 그들의 피가 거친 있다.|황금시대의 무엇이 곳으로 더운지라 그리하였는가?|
|미인을 끓는 것이다.|얼마나 이상 든 아니한 소리다.|보라, 그리하였는가?|우리는 가치를 아니한 같은 새가 인생에 보라.|
|이것은 인간의 발휘하기 힘있다.|별과 생생하며,|얼음이 천자만홍이 따뜻한 더운지라 풀이 구하지 타오르고 이것이다.|것은 사는가 타오르고 노년에게서 봄바람이다.|

## 코드

### 인라인

`인라인 코드` 입니다.

### 블록

````
```kotlin
fun printHelloWorld() {
    println("Hello World!")
}
```
````

```kotlin
fun printHelloWorld() {
    println("Hello World!")
}
```