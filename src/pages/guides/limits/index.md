---
title: Limits
description: Pagination, content size, edit window, and rate limits for the CXUE Commenting API v1
keywords:
  - CXUE Commenting
  - limits
  - pagination
  - rate limits
---

# Limits

## Pagination

| Constraint | Value |
|------------|-------|
| Maximum `limit` per list request | **500** |
| Minimum `limit` | 1 (values below 1 are raised to 1) |
| Pagination model | Cursor via `pageInfo.nextCursor` (numeric timestamp) and optional `endCursor` (document ID) |

Requesting `limit` above 500 is capped to 500 server-side.

## Content size

| Constraint | Value |
|------------|-------|
| Maximum comment text length | **15,000** characters |

## Edit window

| Constraint | Value |
|------------|-------|
| Author edit window | **15 minutes** after creation |

After this window, authors may receive an error when updating unless they have elevated permissions. Exact behavior depends on object security context and product rules.

## Bulk comments

- Bulk create (`POST /comment/bulk`) is only supported for eligible Redrock `objectCode` values.
- Objects that fail access checks are skipped; if none pass, the API returns **400**.

## Rate limiting

- REST v1 does not apply a global rate limiter in the application layer today.
- Public gateway rate limits are enforced at Kong / Adobe I/O when the service is exposed externally.

## Forward compatibility

Clients should:

- Ignore unknown JSON fields in responses.
- Treat new optional request fields as non-breaking when added under v1.

Breaking changes (removed fields, stricter validation, path changes) require a new API major version.

## Related topics

- [Authentication](../authentication/index.md)
- [Error handling](../error-handling/index.md)
- [API Reference](../../api/index.md)
