---
layout: post
title:  Typescript Multi Async Interface
date: 2020-06-26
categories: typescript
---

I recently had to write a Javascript library which was going to be used in multiple different contexts by lots of different people. The purpose of the library was to supply a stream of updating values. Internally to the library, [RxJS](https://github.com/ReactiveX/rxjs) is used as it excellently models streams up updating values. However, the interface to the library should not expose the inner workings.

So, I wanted to allow the consumer of the library to access the values in a number of ways:

## Promises

The standard way of supplying asynchronous values. It is commonly used and with `async/await` the code is very readable:

```typescript
const currentValue = await lib.getValue();
```

The problem with this is, you can only get one value, you won't receive any further updates to the value. So, we can also support the next access method:

## Event Emitter

This will allow the consumer to subscribe to updates in the value and the syntax would be as follows:

```typescript
let currentValue;
lib.getValue()
   .onNew((value) => currentValue = value);
```



```typescript
interface AsyncAccessor<T> extends PromiseLike<T> {
    getLatest(): T;
    getAll(): T[];
    onNew(listener: (value: T) => void): void;
}
```
