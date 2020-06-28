---
layout: post
title:  "Typescript File Inheritance"
date: 2020-06-26
categories: typescript
---


shared/user.ts

```typescript
interface RequestUser {
    name: string;
    email: string;
}
```

api/user.ts

```typescript
import * as User from "../shared/user.ts";

interface DatabaseUser extends RequestUser {
    password: string;
}
```

But what happens in our API handler when we want to use both `User` and `DatabaseUser`?

api/handler.ts

```typescript
import * as User from "../shared/user.ts";
import * as ApiUser from "./user.ts";

export function handler(body: any) {
    const requestUser = body.user as User.RequestUser;
    
}
```
