# TypeScript Error Handling

Follow these rules when throwing, catching, and propagating errors in TypeScript.

## Typed and Explicit Errors

- Throw `Error` subclasses only; never throw raw strings, numbers, or plain objects.
- Model distinct domain or boundary failures with dedicated `Error` subclasses carrying structured context and preserving the original error via `{ cause }`.
- Use typed result unions when callers are expected to handle failure branches routinely as part of normal control flow, and reserve thrown exceptions for invariant violations or unrecoverable failures.

## Safe Catch Blocks

- Treat caught values as `unknown` and narrow explicitly (`error instanceof Error` or a dedicated guard) before reading `message`, `stack`, or custom fields.
- Never swallow errors with empty `catch` blocks or log-and-ignore fallbacks unless explicitly justified and documented at a resilient boundary.
- Always rethrow unexpected errors or wrap them with context via `{ cause }` so root causes are never lost.

## Async Reliability

- Always `await` or explicitly handle returned promises; never leave floating promises unhandled.
- Release acquired resources deterministically in `finally` blocks (or explicit resource management) even when errors occur.
