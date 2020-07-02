---
layout: post
title:  Typescript Multi Async Interface
date: 2020-06-26
categories: typescript
---



```typescript
interface AsyncAccessor<T> extends PromiseLike<T> {
    getLatest(): T;
    getAll(): T[];
    onNew(listener: (value: T) => void): void;
}
```
