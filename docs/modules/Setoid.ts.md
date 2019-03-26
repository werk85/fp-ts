---
title: Setoid.ts
nav_order: 78
parent: Modules
---

---

<h2 class="text-delta">Table of contents</h2>

- [Setoid (interface)](#setoid-interface)
- [setoidAll (constant)](#setoidall-constant)
- [setoidBoolean (constant)](#setoidboolean-constant)
- [setoidDate (constant)](#setoiddate-constant)
- [setoidNumber (constant)](#setoidnumber-constant)
- [setoidString (constant)](#setoidstring-constant)
- [contramap (function)](#contramap-function)
- [fromEquals (function)](#fromequals-function)
- [getArraySetoid (function)](#getarraysetoid-function)
- [getNullableSetoid (function)](#getnullablesetoid-function)
- [~~getProductSetoid~~ (function)](#getproductsetoid-function)
- [~~getRecordSetoid~~ (function)](#getrecordsetoid-function)
- [getStructSetoid (function)](#getstructsetoid-function)
- [getTupleSetoid (function)](#gettuplesetoid-function)
- [strictEqual (function)](#strictequal-function)

---

# Setoid (interface)

**Signature**

```ts
export interface Setoid<A> {
  readonly equals: (x: A, y: A) => boolean
}
```

Added in v1.0.0

# setoidAll (constant)

**Signature**

```ts
export const setoidAll: Setoid<any> = ...
```

Added in v1.16.0

# setoidBoolean (constant)

**Signature**

```ts
export const setoidBoolean: Setoid<boolean> = ...
```

Added in v1.0.0

# setoidDate (constant)

**Signature**

```ts
export const setoidDate: Setoid<Date> = ...
```

Added in v1.4.0

# setoidNumber (constant)

**Signature**

```ts
export const setoidNumber: Setoid<number> = ...
```

Added in v1.0.0

# setoidString (constant)

**Signature**

```ts
export const setoidString: Setoid<string> = ...
```

Added in v1.0.0

# contramap (function)

Returns the `Setoid` corresponding to the partitions of `B` induced by `f`

**Signature**

```ts
export const contramap = <A, B>(f: (b: B) => A, fa: Setoid<A>): Setoid<B> => ...
```

Added in v1.2.0

# fromEquals (function)

**Signature**

```ts
export const fromEquals = <A>(equals: (x: A, y: A) => boolean): Setoid<A> => ...
```

Added in v1.14.0

# getArraySetoid (function)

**Signature**

```ts
export const getArraySetoid = <A>(S: Setoid<A>): Setoid<Array<A>> => ...
```

Added in v1.0.0

# getNullableSetoid (function)

**Signature**

```ts
export const getNullableSetoid = <A>(S: Setoid<A>): Setoid<A | undefined | null> => ...
```

Added in v1.16.0

# ~~getProductSetoid~~ (function)

Use `getTupleSetoid` instead

**Signature**

```ts
export const getProductSetoid = <A, B>(SA: Setoid<A>, SB: Setoid<B>): Setoid<[A, B]> => ...
```

Added in v1.0.0

# ~~getRecordSetoid~~ (function)

Use `getStructSetoid` instead

**Signature**

```ts
export const getRecordSetoid = <O extends { [key: string]: any }>(
  setoids: { [K in keyof O]: Setoid<O[K]> }
): Setoid<O> => ...
```

Added in v1.0.0

# getStructSetoid (function)

**Signature**

```ts
export const getStructSetoid = <O extends { [key: string]: any }>(
  setoids: { [K in keyof O]: Setoid<O[K]> }
): Setoid<O> => ...
```

Added in v1.14.2

# getTupleSetoid (function)

Given a tuple of `Setoid`s returns a `Setoid` for the tuple

**Signature**

```ts
export const getTupleSetoid = <T extends Array<Setoid<any>>>(
  ...setoids: T
): Setoid<{ [K in keyof T]: T[K] extends Setoid<infer A> ? A : never }> => ...
```

**Example**

```ts
import { getTupleSetoid, setoidString, setoidNumber, setoidBoolean } from 'fp-ts/lib/Setoid'

const S = getTupleSetoid(setoidString, setoidNumber, setoidBoolean)
assert.strictEqual(S.equals(['a', 1, true], ['a', 1, true]), true)
assert.strictEqual(S.equals(['a', 1, true], ['b', 1, true]), false)
assert.strictEqual(S.equals(['a', 1, true], ['a', 2, true]), false)
assert.strictEqual(S.equals(['a', 1, true], ['a', 1, false]), false)
```

Added in v1.14.2

# strictEqual (function)

**Signature**

```ts
export const strictEqual = <A>(a: A, b: A): boolean => ...
```

Added in v1.0.0
