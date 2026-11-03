# rimfrost-framework-process-openapi

OpenAPI definitions shared across all processes.
Contains endpoints that are identical regardless of the process. They are implemented once in `rimfrost-framework-process`.

## Endpoints

- `GET /processvy/steg?aktivitetId={uuid}` — the process's steps in order, with status `KLAR`, `PAGAR` or `KOMMANDE` relative to the step that contains the activity. Responds `404` if the activity is not in the process description, or if the process has no process description (the processvy is optional).
  A step can have sub-steps in the optional field `steg` (same shape as the step), at most two levels below the response's `steg[]`. The field is absent when a step has no sub-steps. A step with sub-steps is `PAGAR` if any sub-step is in progress, `KLAR` if all are done, and otherwise `KOMMANDE` (since 1.1.0).

## Artifacts

- Maven artifact: <https://github.com/Forsakringskassan/repository>

## Modules

- `rimfrost-framework-process-openapi-spec` — OpenAPI YAML spec artifact
- `rimfrost-framework-process-openapi-jaxrs-spec` — Generated JAX-RS server stubs
