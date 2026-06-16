---
title: Overview - Workfront Comment Stream API
description: An overview of the Workfront Comment Stream REST API for managing comments, replies, and reactions across Workfront and Adobe platform objects.
keywords:
  - Workfront
  - Comment Stream
  - commenting API
  - REST API
hideBreadcrumbNav: true
---

# Workfront Comment Stream API

The Comment Stream REST API v1 provides an HTTP JSON interface for creating, reading, updating, and deleting comments, replies, and reactions on objects across the Workfront and Adobe ecosystem — projects, tasks, documents, AEM assets, and other registered `objectCode` values.

Use this API for stable **server-to-server integrations**. Many Adobe and Workfront product UIs call Comment Stream through GraphQL instead; this REST surface is the public contract for external integrators.

#### Resources

* [Workfront product documentation](https://experienceleague.adobe.com/docs/workfront.html)
* [Adobe Developer Console](https://developer.adobe.com/developer-console/)
* [Workfront Platform APIs](https://developer.adobe.com/workfront-apis/)

## Overview

Comment Stream is a unified commenting service for Workfront and Adobe platform objects. The REST v1 API exposes comment lifecycle operations with cursor-based list pagination, object-level access control, and Adobe IMS OAuth 2.0 authentication.

All v1 endpoints are prefixed with `/api/v1/`. Breaking changes require a new major version; non-breaking additions (optional fields, new endpoints) can ship under v1.

#### Prerequisites

This guide assumes familiarity with:

* REST API principles (HTTP methods, JSON request/response bodies, status codes)
* Adobe IMS OAuth 2.0 and Adobe Developer Console project setup
* Workfront object identifiers and `objectCode` values (for example `PROJ`, `TASK`, `DOCU`)

## Discover

[Getting Started](guides/index.md)

Set up authentication, learn required headers, and make your first API call.

[Try the API](api/index.md)

Interactive API reference with endpoint descriptions, request schemas, and curl examples.

[Error handling](guides/error-handling/index.md)

HTTP status codes and response shapes for client and server errors.

[Limits](guides/limits/index.md)

Pagination caps, content size limits, edit window, and bulk comment constraints.
