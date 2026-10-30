# Vendor Extensions Registry

µEd-api core schemas cover only the shapes that are common across
platforms. Anything platform-specific belongs in `vendorExtensions`,
a reusable extension point defined once in
`paths/shared/schemas/VendorExtensions.yml` and referenced from:

- **Requests:** `ChatRequest.context`, `ChatRequest.configuration`,
  `EvaluateRequest.configuration`, and `User`.
- **Responses:** each `Feedback` item returned by `/evaluate`, and
  `ChatResponse.metadata`.

## How it works

- Vendors add exactly one top-level key inside `vendorExtensions`, named
  `x-<platform-slug>` (following the OpenAPI Specification Extensions
  convention, e.g. `x-lf`).
- The schema enforces this namespace envelope: keys must match
  `^x-[a-z0-9]+(?:-[a-z0-9]+)*$` and each value must be an object.
  Anything else (e.g. `{"module": 1}` or `{"x-lf": 42}`) is invalid.
- µEd-api does **not** define, host, or validate the contents under a
  vendor's namespace. Each vendor is responsible for documenting and
  versioning the shape of its own `x-<platform-slug>` object in its own
  repository or docs.
- This file exists **only** to reserve namespace slugs and prevent
  collisions between vendors — it is not a schema registry and does not
  imply any endorsement or validation by µEd-api.

## Registering a namespace

To reserve a namespace, open a PR adding a row to the table below with
your slug, an identifying owner/organization, and a link to where your
fields are actually documented (your own repo, docs site, or spec).

| Namespace (`x-<slug>`) | Owner | Docs / Repo |
|---|---|---|
| `x-lf` | Lambda Feedback | https://github.com/lambda-feedback/mued-vendor-spec |

## When does a vendor extension become a core schema?

A concept only graduates from a vendor extension into a typed core/shared
schema in this repository once **at least two independent platforms**
need the same underlying concept and agree on a common core
representation for it. Their existing payloads do not have to match
already: for example, `{ "timeLimitSeconds": 60 }` and
`{ "durationMs": 60000 }` express the same time limit and could map to
one shared schema. Until then, it stays vendor-extension territory,
even if it looks broadly useful — this keeps core schemas free of
single-vendor assumptions (this is exactly the mistake that motivated
`vendorExtensions` in the first place: module/set/question concepts were
found to be Lambda-Feedback-specific, not universal).

To propose a graduation, open an issue showing the ≥2 independent
platforms, their current shapes for the concept, and the proposed common
core representation, so the core addition can be modeled from real,
shared usage rather than guessed in advance.
