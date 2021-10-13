---
description: The internal structure we used to build the API and why.
---

# Architecture Rationale

The architecture is more or less custom as the API layer on a NextJS app is very thin, it focuses on using simple **handlers** for processing API requests.

All API requests hit the `pages/api` directory, are processed by a defined set of middleware, then if successfully forwarded to a given handler.

You can consider `app/handlers` to effectively be invokable single function controllers.

The validation for a given handler is expected to be tightly coupled to the code, as it is simpler to test a handler in isolation.

As the Hedera Hashgraph costs a small amount of real money, we have created a mock that is injected into the handlers during the basic set of tests to prove additional logic for the API query and body parameters.

All other items that validate and inject into a handler do so at the API route layer. We use a `process` function to chain a list of middleware, authentication validation, and context injection before hitting in the handler. Providing a higher degree of flexible testability.

Due to the constraints of Vercel only providing a maximum of 12 unique routes for a free account, this can be slightly overcome through leveraging a routing to handler approach.

The topic handler `pages/api/consensus/topic/[id].js` provides additional insight into how to wrap a single route to manage a given resource consisting of different handlers.

Thank you to [James Wrightson](https://github.com/guerrillacontra) for your insight on handling injecting additional functionality as **context** for a given handler.
