# purescript-pirates-charm

A library for binding `Event`s to synchronous and asynchronous effects.

The library contains four functions.

| Function    | Signature                                        | Description |
| ----------- | ------------------------------------------------ | ----------- |
| `bindToAff` | `forall a b. Event a -> (a -> Aff b) -> Event b` | Transforms `a` into `b` via an Aff, emitting `b`-s in order. |
| `bindToAffWithCancellation` | `forall a b. Event a -> (a -> Aff b) -> Event b` | Transforms `a` into `b` via an Aff, emitting `b`-s in order. When a new `a` is received, the previous computation to produce `Aff b` is canceled if it is still ongoing. |
| `bindToAffParallel` | `forall a b. Event a -> (a -> Aff b) -> Event b` | Transforms `a` into `b` via an Aff, emitting `b`-s as soon as they come in. This could result in `b`-s arriving out of order compared to the `a`-s. |
| `bindToEffect` | `forall a b. Event a -> (a -> Effect b) -> Event b` | Transforms `a` into `b` via an Effect. |