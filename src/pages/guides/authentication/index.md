---
title: Authentication
description: Authenticate to the Adobe CX Commenting API with Adobe IMS OAuth 2.0
keywords:
  - Adobe CX Commenting
  - authentication
  - IMS
  - OAuth
---

# Authentication

The Adobe Customer Experience (CX) Commenting API accepts Adobe IMS OAuth 2.0 bearer tokens on the `Authorization` header. Integrations should follow the [Adobe IMS Server-to-Server authentication guide](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) to obtain access tokens.

## Required headers

Include these headers on every request:

| Header | Required | Description |
|--------|----------|-------------|
| `Authorization` | Yes | `Bearer <IMS_ACCESS_TOKEN>` |
| `x-api-key` | Recommended | API client ID from Adobe Developer Console (used for logging and client identification) |
| `x-gw-ims-org-id` | For service tokens | IMS organization ID (tenant) when using a service-to-service token |
| `wf-userid` | For service tokens | Workfront user ID on whose behalf the action runs |
| `wf-customerid` | For service tokens | Workfront customer (instance) ID, when applicable |
| `Content-Type` | For bodies | `application/json` |

## User tokens

Pass the end-user IMS token in `Authorization`. The service validates the token and resolves the user context for access checks.

## Service tokens

Service tokens include a `pac` claim. When using a service token you must supply tenant and user context headers so the service can enforce object access:

- `x-gw-ims-org-id` or `wf-customerid` — tenant
- `wf-userid` or `user-id` — acting user

The service validates the token against IMS with scope `workfront.comment-stream`.

## Object access

The default requirement for allowing comments on an object is that the user has view access to that object. If the resolved user does not have at least view permission on the target object, the API returns a `403 Forbidden` response.

## Session-based access (Workfront UI only)

Workfront browser sessions may authenticate via `sessionid` cookie or `wf-auth` cookie through Kong. That path is for product UI traffic, not for third-party server integrations. **External integrators should use IMS OAuth only.**

## First request — create a comment

```bash
curl -X POST "https://domain.my.workfront.com/comments/api/v1/comment" \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "x-api-key: $API_KEY" \
  -H "x-gw-ims-org-id: $IMS_ORG_ID" \
  -H "Content-Type: application/json" \
  -d '{
    "objectID": "6400cae3000c141416060e29",
    "objectCode": "PROJ",
    "content": "Kickoff notes are ready for review.",
    "contentHTML": "<p>Kickoff notes are ready for review.</p>",
    "isPrivate": false
  }'
```

## List comments on an object

```bash
curl -G "https://workfront.adobe.io/comments/api/v1/comment" \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "x-api-key: $API_KEY" \
  --data-urlencode "objectID=6400cae3000c141416060e29" \
  --data-urlencode "objectCode=PROJ" \
  --data-urlencode "limit=20"
```

**Response** (`200 OK`):

```json
{
  "data": [
    {
      "_id": "...",
      "content": "...",
      "objectID": "...",
      "objectCode": "PROJ"
    }
  ],
  "pageInfo": {
    "hasNextPage": true,
    "nextCursor": 1710000000000
  }
}
```

Use `pageInfo.nextCursor` as the `cursor` query parameter on the next request to fetch the following page.

## Related topics

- [Error handling](../error-handling/index.md)
- [Limits](../limits/index.md)
- [API Reference](../../api/index.md)
