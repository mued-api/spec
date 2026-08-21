# Vendor Extensions Registry

µEd-api core schemas cover only the shapes that are common across
platforms. Anything platform-specific belongs in `vendorExtensions`,
a reusable, open-ended (`additionalProperties: true`) extension point
defined once in `paths/shared/schemas/VendorExtensions.yml` and referenced
from `context`, `configuration`, and `User` schemas.

## How it works

- Vendors add exactly one top-level key inside `vendorExtensions`, named
  `x-<platform-slug>` (following the OpenAPI Specification Extensions
  convention, e.g. `x-lf`).
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
| _(none registered yet)_ | | |

## When does a vendor extension become a core schema?

A concept only graduates from a vendor extension into a typed core/shared
schema in this repository once **at least two independent platforms**
need the identical shape. Until then, it stays vendor-extension territory,
even if it looks broadly useful — this keeps core schemas free of
single-vendor assumptions (this is exactly the mistake that motivated
`vendorExtensions` in the first place: module/set/question concepts were
found to be Lambda-Feedback-specific, not universal).

To propose a graduation, open an issue showing the ≥2 independent
platforms and their (already converging) shapes, so the core addition
can be modeled from real, shared usage rather than guessed in advance.
