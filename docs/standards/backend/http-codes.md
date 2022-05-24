---
layout: default
title: HTTP Codes
permalink: /standards/backend/http-codes
parent: Backend
grand_parent: Standards
nav_order: 3
---

# HTTP Codes

## Why

HTTP Status codes help categorize the response. Sometimes they are self-explanatory (e.g. 404) and sometimes they are backed by information (e.g. 201). A REST API MUST implement these status codes well to convey the right information to its clients. Correct status codes help client app developers handle responses better.

## HTTP Code for Data Errors
- 400 for when the requested information is incomplete or malformed.
- 422 for when the requested information is okay, but invalid.
- 404 for when everything is okay, but the resource doesn’t exist.
- 409 for when a conflict of data exists, even with valid information.

## HTTP Code for Auth Errors

- 401 for when an access token isn’t provided, or is invalid.
- 403 for when an access token is valid, but requires more privileges.

## HTTP Code for Standard Statuses

- 200 for when everything is okay.
- 204 for when everything is okay, but there’s no content to return.
- 500 for when the server throws an error, completely unexpected. 