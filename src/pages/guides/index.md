---
title: Getting Started
description: Get started with the Workfront Comment Stream REST API v1
keywords:
  - Workfront Comment Stream
  - commenting API
  - getting started
hideBreadcrumbNav: true
---

# Getting Started

## Introducing the Comment Stream API

The **Comment Stream REST API v1** lets integrators programmatically manage comments, replies, and reactions on Workfront and Adobe platform objects. Use it when you need a stable HTTP resource model for server-to-server integrations.

## Before you begin

1. **[Authentication](authentication/index.md)** — Set up Adobe IMS OAuth 2.0 credentials in Adobe Developer Console and learn required request headers.
2. **[Error handling](error-handling/index.md)** — Understand HTTP status codes and error response shapes.
3. **[Limits](limits/index.md)** — Review pagination caps, content size limits, and the author edit window.
4. **[API Reference](../api/index.md)** — Explore all endpoints interactively.

## Base URL

External customer requests go through the **Adobe I/O API Gateway** once the service is onboarded (same pattern as other Workfront public APIs).

```
https://domain.my.workfront.com/comment-stream/api/v1
```

## Quick example — create a comment

```bash
curl -X POST "https://domain.my.workfront.com/comment-stream/api/v1/comment" \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "x-api-key: $API_KEY" \
  -H "x-gw-ims-org-id: $IMS_ORG_ID" \
  -H "wf-customerid: $WF_CUSTOMER_ID" \
  -H "Content-Type: application/json" \
  -d '{
    "objectID": "6400cae3000c141416060e29",
    "objectCode": "PROJ",
    "content": "Kickoff notes are ready for review.",
    "contentHTML": "<p>Kickoff notes are ready for review.</p>",
    "isPrivate": false
  }'
```

A successful response (`200 OK`) returns a comment object including `_id`, `objectID`, `objectCode`, `content`, `contentHTML`, and audit fields.

## Next steps

Head to the [API Reference](../api/index.md) for the full endpoint catalog, or read the [Authentication guide](authentication/index.md) for token and header details.
