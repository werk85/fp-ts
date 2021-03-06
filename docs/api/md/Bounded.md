MODULE [Bounded](https://github.com/gcanti/fp-ts/blob/master/src/Bounded.ts)

# Bounded

_type class_

```ts
interface Bounded<A> extends Ord<A> {
  readonly top: A
  readonly bottom: A
}
```

The `Bounded` type class represents totally ordered types that have an
upper and lower boundary.

Instances should satisfy the following law in addition to the `Ord` laws:

* Bounded: `bottom <= a <= top`

# boundedNumber

_instance_

_since 1.0.0_

```ts
Bounded<number>
```
