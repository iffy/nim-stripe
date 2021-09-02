Very basic interface for interacting with [Stripe](https://www.stripe.com).

```nim
import stripe

proc main() {.async.} =
  let secret_key = "..."
  let client = newStripeClient(secret_key)
  let products = await stripeClient.get("/v1/products")
  echo $products
```
