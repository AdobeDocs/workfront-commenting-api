---
title: Error handling
description: HTTP status codes and error response shapes for the Workfront Comment Stream REST API v1
keywords:
  - Workfront Comment Stream
  - error handling
  - HTTP status codes
---

# Error handling

## HTTP status codes

| Code | When it occurs |
|------|----------------|
| 200 | Success (including create/update/delete for v1) |
| 400 | Validation failure, unsupported bulk operation, or bad input |
| 401 | Missing or invalid authentication |
| 403 | Authenticated but not allowed on the object or comment |
| 404 | Comment or resource not found |
| 500 | Unexpected server error |

## Response shapes

### Validation errors (`400`)

When request JSON fails schema validation:

```json
{
  "message": "body must have required property 'objectCode'",
  "validation": "body must have required property 'objectCode'"
}
```

### Authentication (`401`)

```json
{
  "message": "Unauthorized"
}
```

### Other client errors (`400` / `403`)

```json
{
  "message": "Human-readable explanation"
}
```

### Server errors (`500`)

```json
{
  "message": "Something went wrong"
}
```

Internal details are logged server-side; responses do not expose stack traces.

## Common scenarios

| Scenario | Typical status | Example message theme |
|----------|----------------|------------------------|
| Invalid ObjectId in path | 400 | Validation on `id` pattern |
| Bulk on non-Redrock objects | 400 | Bulk commenting only available for Redrock objects |
| No access to object | 403 | Permission / access check failure |
| Edit outside allowed window | 400 / 403 | Edit time limit exceeded |
| Invalid IMS token | 401 | Unauthorized |

## Request tracing

Pass or generate `x-request-id` on inbound calls. The service uses request IDs in structured logs for support investigations.

## Related topics

- [Authentication](../authentication/index.md)
- [Limits](../limits/index.md)
- [API Reference](../../api/index.md)
