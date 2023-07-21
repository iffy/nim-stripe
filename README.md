Very basic interface for interacting with [Stripe](https://www.stripe.com).

GET example:

```nim
import stripe

proc main() {.async.} =
  let secret_key = "..."
  let client = newStripeClient(secret_key)
  let products = await stripeClient.get("/v1/products")
  echo $products
```

POST example:

```nim
import stripe
import std/tables

proc main {.async.} =
  let secret_key = "..."
  let stripeClient = newStripeClient(secret_key)
  let charge = await stripeClient.post("/v1/charges", {
        "amount": 1000,
        "currency": "usd",
        "description": "A Charge",
        "statement_descriptor": "Widget You Forgot Purchasing",
        "receipt_email": "bob@example.com",
        "source": "stripeToken",
      }.toTable())
```