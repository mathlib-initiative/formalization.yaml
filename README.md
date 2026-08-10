# formalization.yaml

A self-reporting standard for autoformalization projects.

Drop a filled-in `formalization.yaml` at the root of your formalization repo. Fill in the `[required]` fields; the rest are optional. The point is to set an expectation that projects report on what was formalized, how, and how faithfully; without requiring everyone to invent their own format.

## How to use it

1. Copy `formalization.yaml` to the root of your formalization repo.
2. Fill in every field marked `[required]`. Fill in as much of the rest as is useful.

The file is meant to live **alongside the formalization it describes**. That co-location is deliberate: anything the repo already encodes (the Lean toolchain (`lean-toolchain`), dependencies and pins (`lakefile`), build status (CI), commit history) is intentionally *not* duplicated here. This file captures the things that aren't mechanically obvious from the source tree: provenance, intent, process, and how faithfully the formalization tracks its source.

## Validating

The template carries a `# yaml-language-server: $schema=…` line, so editors with the YAML extension validate it live as you fill it in, with no setup beyond the extension.

To check it from the command line or CI (handy for agents too):

```
check-jsonschema --schemafile https://raw.githubusercontent.com/mathlib-initiative/formalization.yaml/main/schema/formalization.schema.json formalization.yaml
```

The schema picks the right rules from the file's `version` field; a file with no `version` is checked against the latest.
