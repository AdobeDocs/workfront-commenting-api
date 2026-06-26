---
title: Overview - CXUE Commenting API
description: An overview of the CXUE Commenting API for managing comments, replies, and reactions across Workfront and Adobe platform objects.
keywords:
  - Workfront
  - CXUE Commenting
  - commenting API
  - REST API
hideBreadcrumbNav: true
---

# CXUE Commenting API

The CXUE Commenting REST API v1 provides an HTTP JSON interface for creating, reading, updating, and deleting comments, replies, and reactions on objects across the Workfront and Adobe ecosystem — projects, tasks, documents, AEM assets, and other registered `objectCode` values.

## Overview

CXUE Commenting is a unified commenting service for Workfront and Adobe platform objects. The REST v1 API exposes comment lifecycle operations with cursor-based pagination, object-level access control, and Adobe IMS OAuth 2.0 authentication.

All v1 endpoints are prefixed with `/api/v1/`. Breaking changes require a new major version; non-breaking additions (optional fields, new endpoints) can ship under v1.

## Supported object codes

The `objectCode` parameter identifies the type of object a comment is attached to. The following codes are supported:

| Platform                                | Object codes |
|-----------------------------------------|---|
| **Workfront**                           | `PROJ`, `TASK`, `OPTASK`, `DOCU`, `PRGM`, `PORT`, `TMPL`, `TTSK`, `ITRN`, `USER`, `TSHET`, `GOAL`, `TEAMOB` |
| **Workfront Boards**                    | `BOARD`, `CARD` |
| **Adobe Workfront Planning**            | `RECORD` |
| **Adobe GenStudio**                     | `GS_APPROVALS` |
| **Customer Journey Analytics**          | `cjaProject` |
| **Adobe Experience Manager**            | `AEM` |
| **Experience Success Studio (ESS)**     | `ESS_SITE_APPROVALS` |
| **Adobe Plays**                         | `plays` |
| **Adobe Journey Optimizer B2B Edition** | `sapphire_email` |
| **Workfront Intake**                    | `intake-request` |

## Discover

[Getting Started](guides/index.md)

Set up authentication, learn required headers, and make your first API call.

[Try the API](api/index.md)

Interactive API reference with endpoint descriptions, request schemas, and curl examples.

[Error handling](guides/error-handling/index.md)

HTTP status codes and response shapes for client and server errors.

[Limits](guides/limits/index.md)

Pagination caps, content size limits, edit window, and bulk comment constraints.
