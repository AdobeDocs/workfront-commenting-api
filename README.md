# CXUE Commenting API — developer.adobe.com

Customer-facing documentation site for the [CXUE Commenting API v1](https://developer.adobe.com/workfront-commenting-api/).

## Source of truth

The OpenAPI contract and engineering docs are maintained in the [comment-stream](https://gitlab.workfront.tech/pacific/comment-stream) service repository:

- OpenAPI: `documentation/api/v1/apiv1.json`
- PR bundle sync: `documentation/api/adobedocs-pr/`

When the API contract changes, update comment-stream first, then refresh `static/apiv1.json` in this repo.

## Local development

```bash
npm run dev
```

See [ADP Developer Site Documentation](https://developer-stage.adobe.com/dev-docs-reference/) for site authoring conventions.
