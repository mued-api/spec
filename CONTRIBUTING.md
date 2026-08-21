# Contributing

This repository contains the OpenAPI specification for the µEd API. Contributions should keep the source files consistent and go through GitHub pull requests.

## Creating issues

Before opening a new issue, check whether the topic is already covered by an existing issue or pull request.

When creating an issue, include:

- a clear, specific title
- the problem you observed or the change you want to propose
- the relevant part of the specification, if known
- example requests, responses, or schema snippets when they help clarify the change
- expected behavior and any constraints or open questions

Use issues to capture bugs, unclear parts of the specification, and proposed API changes before implementation when the scope is non-trivial.

## Vendor-specific fields

If you need a field that's specific to your platform and not something
every implementer needs, it likely belongs under `vendorExtensions`
rather than as a new core schema field. See
[VENDOR_EXTENSIONS.md](VENDOR_EXTENSIONS.md) for how to namespace your
data and the bar for when something becomes a core schema addition
(≥2 independent platforms needing the identical shape).

## Contributing

1. Start from the latest `main` branch.
2. Create a topic branch for your work.
3. If you do not have permission to create branches in this repository, fork the repository and open the pull request from your fork.
4. Make your changes in the source spec files.
5. Run the local checks before opening or updating a pull request:

```bash
npm install
npm run lint
npm run bundle
```

When you open the pull request:

- describe the change and why it is needed
- link the related issue when one exists
- keep the pull request focused on a single concern

## Reviewing

Reviewers should check that:

- the proposed change is clear and scoped appropriately
- the OpenAPI source remains consistent and readable
- `npm run lint` passes
- `npm run bundle` succeeds when applicable

Pull request authors should respond to review comments by updating the branch or clarifying intent in the discussion.

## Merging

Pull requests should be merged with **Squash and merge**.

Before merging:

- the pull request has been reviewed
- the GitHub CI checks for linting and bundling are passing
- open review comments have been resolved

Merged branches are deleted automatically.
