---
layout: default
---

# Wrap Up

Overall, Orval provides a compelling solution to boiler plate code which streamlines the busy-work of integrating the UI with an API such as a BFF.

The option of having type-safe API code generated for you and knowing confidently that it matches the specification would give us confidence in our integrations and keep us abreast of changes to the API we're consuming.

However:

- Works best when your response schemas differ a lot for negative cases
- Limited control over the generated control (though there is some)
- Any custom generators we use need to be validated ourselves
- Requires us to rethink how we integrate APIs.
