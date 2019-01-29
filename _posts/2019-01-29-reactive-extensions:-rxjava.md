---
title: "Reactive Extensions: RxJava"
layout: post
date: 2019-01-29 23:06
description:
tag:
- ReactiveX
- RxJava
- Java
- Kotlin
blog: true
jemoji:
---

<div class="text-center" markdown="1">
![ReactiveX][0]{:width="25%"}
<figcaption class="caption">Reactive Extensions (ReactiveX)</figcaption>
</div>
<br/>

I always has been interested by Reactive Streams (ReactiveX) and RxJava (and RxKotlin).  
Recently, I enjoyed reading the excellent book: [Learning RxJava][1] by Thomas Nield, and the following are my notes.

## Why RxJava ?
* Concurrency, event handling, obsolete data states, and exception recovery.
* Maintainable, reusable, and evolvable.
* Allows applications to be tactical and evolvable while maintaining stability in production.

## Quick Start
In ReactiveX, the core type is the `Observable` which essentially pushes things. A given `Observable<T>` pushes things of type `T` through a series of operators until it arrives at an `Observer` that consumes the items. 
The following is an example of an `Observable<String>` that will push three `String` objects:
```kotlin
fun main() {
    val observable = Observable.just("Hello", "world", "!")
}
```
However, running this `main` method is not going to do anything other than declare a `Observable<String>`. To make this `Observable` actually push (or emit) these three strings, we need an `Observer` to _subscribe_ to it and receive the items:
```kotlin
fun main() {
    val observable = Observable.just("Hello", "world", "!")
    observable.subscribe {
        print("$it ")
    }
}
```
This time, the output is the following:
```
Hello world ! 
```
What happened here is that our `Observable<String>` pushed each `String` object once at a time to the `Observer` (the lambda).

It’s possible to use several operators between `Observable` and `Observer` to transform each pushed item or manipulate them, the following is an example of `map()`:
```kotlin
fun main() {
    val observable = Observable.just("Hello", "world", "!")
    observable.map { it.toUpperCase() }.subscribe { print("$it ") }
}
```
The output should be:
```
HELLO WORLD !
```

## RxJava vs Java 8 Streams
How `Observable` is any different from Java 8 _Streams_ or Kotlin _sequences_? The key difference is that `Observable` _pushes_ the items while Streams and sequences _pull_ the items. 

## Advanced RxJava
The following are more detailed subjects for a deeper understanding of RxJava:

* [Observable & Observer][11]
* [Hot vs Cold Observable][12]
* [Observable Factories][13]
* [Disposing][14]
* [Operators: Supressing][15]
* [Operators: Transforming][16]
* [Operators: Reducing][17]

## Sources
* [Learning RxJava][1]
* [ReactiveX Documentation: Observable][2]
* [ReactiveX Documentation: Operators][3]
* [RxMarbles][4]

-- *Mouaad*

[0]: {{ site.url }}/assets/images/blog/reactivex.png
[1]: https://www.amazon.com/Learning-RxJava-Thomas-Nield/dp/1787120422
[2]: http://reactivex.io/documentation/observable.html
[3]: http://reactivex.io/documentation/operators.html
[4]: https://rxmarbles.com/
[11]: {{ site.url }}/rxjava-observable-and-observer
[12]: {{ site.url }}/rxjava-hot-vs-cold-observable
[13]: {{ site.url }}/rxjava-observable-factories
[14]: {{ site.url }}/404
[15]: {{ site.url }}/404
[16]: {{ site.url }}/404
[17]: {{ site.url }}/404