---
title: Authentication
---

The Morpheus API uses an OAUTH 2.0 based authentication model.

Authentication is done by passing an access token in the Authorization HTTP header.

Use Get Access Token to acquire a valid access token.

Most `/api` endpoints require authentication, and will respond with a HTTP 401 without a valid Authorization header.

[block:callout]
{
  "type": "warning",
  "body": "Be sure to keep your access token a secret. Anyone with the token can interact with the API as your Morpheus user."
}
[/block]
