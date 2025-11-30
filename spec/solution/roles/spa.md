### [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > spa

# `spa`

Represents a browser-delivered client experience such as a single-page
application, WASM shell, or other rich frontend. A `spa` role signals that the
software expects:

- route and URI definitions,
- asset bundles (HTML/CSS/JS, WASM modules)

## Characteristics

- Entry point: typically an `index.html` or equivalent bootstrap file that
  loads the SPA runtime.
- Interaction model: may use HTTP/gRPC calls to backend APIs, websockets, or
  real-time services.
- Deployment: optimized for static hosting and potentially CDN distribution

## Usage Notes

- SPA roles can appear under `owned` or `dependency` blocks depending on who
  maintains the frontend.
- Detailed route definitions, assets, and integration points belong in the
  application-specific spec sections (e.g., `software.trail`).