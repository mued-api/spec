# µEd API (µEd-api)

Education Microservices API **specification**.

This repository is intentionally **spec-only**. It defines an **OpenAPI 3.1** contract that educational services can implement to conform to the µEd API.

## Contents

- `openapi.yml` — the main entry point (OpenAPI 3.1)
- `paths/` — endpoint definitions (multi-file structure)
- `dist/openapi.yml` — bundled single-file spec (generated)

## What the spec covers

At a high level, the API specifies endpoints for:

- generating feedback for student submissions
- educational chat interactions

All request/response shapes, validation rules, and examples live in the spec files.

## Development

### Prerequisites

```bash
npm install
```

### Linting

Lint the OpenAPI spec using [Redocly CLI](https://redocly.com/docs/cli/):

```bash
npm run lint
```

### Bundling

Bundle the multi-file spec into a single file at `dist/openapi.yml`:

```bash
npm run bundle
```

## Viewing the spec

Open `openapi.yml` (or `dist/openapi.yml` for the bundled version) in any OpenAPI-capable tool (e.g., Swagger Editor, Swagger UI, Stoplight, Redocly) to render and explore the docs.
