# µEd API (µEd-api)

Educational Microservices API **specification**.

This repository is intentionally **spec-only**. It defines an **OpenAPI 3.1** contract that educational services can implement to conform to the µEd API.

## Contents

- `openapi.yml` — the source of truth (OpenAPI 3.1).

## What the spec covers

At a high level, the API specifies endpoints for:

- generating feedback for student submissions
- educational chat interactions

All request/response shapes, validation rules, and examples live in `openapi.yml`.

## Viewing the spec

Open `openapi.yml` in any OpenAPI-capable tool (e.g., Swagger Editor / Swagger UI, Stoplight) to render and explore the docs.
