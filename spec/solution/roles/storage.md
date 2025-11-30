# `storage`

Represents object/blob storage for unstructured data (e.g., Azure Blob Storage,
AWS S3, GCS Buckets).

## Characteristics

- Organizes data into containers/buckets with hierarchical keys.
- Supports large binary payloads, static website hosting, and lifecycle rules.
- Accessed via HTTP APIs, SDKs, or mounting protocols.

## Usage Notes

- Suitable for storing assets, exports, backups, or SPA bundles.
- Security posture (public vs private) and lifecycle policies belong in the
  associated application documentation.
