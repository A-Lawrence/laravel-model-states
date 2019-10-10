---
title: Retrieving transitionable states from a state
weight: 4
---

An array of transitionable states can use the retrieved with the `transitionableStates()` method on your model.

```php
class Payment extends Model
{
    // …

    protected function registerStates(): void
    {
        $this->addState('state', PaymentState::class)
            ->allowTransition(Pending::class, Paid::class)
            ->allowTransition(Paid::class, Refunded::class)
    }
}
```

```php
$transitionableStates = $payment->transitionableStates('state', Pending::class);
```

This will return an array with all transitionable states for `Pending::class`

```php
[
    0 => "paid"
]
```