# CDIF Packaging

Tools and examples for converting between [CDIF](https://cross-domain-interoperability-framework.github.io/cdifbook/) JSON-LD metadata and dataset packaging formats, with a current focus on [RO-Crate](https://www.researchobject.org/ro-crate/).

## Repository Structure

```
packaging/
  tools/                        Conversion and validation scripts
    ConvertToROCrate.py          CDIF JSON-LD -> RO-Crate 1.1
    ROCrateToCDIF.py             RO-Crate 1.1 -> CDIF JSON-LD
    ValidateROCrate.py           RO-Crate structural validator
  examples/                     Example files (valid and invalid)
  docs/                         Documentation
    RO-Crate-relationship.md    Property mappings and conversion details
```

## Quick Start

### Prerequisites

```bash
pip install PyLD jsonschema
```

### Convert CDIF to RO-Crate

```bash
python tools/ConvertToROCrate.py input.jsonld -o output-rocrate.json -v
```

### Convert RO-Crate to CDIF

```bash
python tools/ROCrateToCDIF.py input-rocrate.json -o output-cdif.json -v --validate
```

### Validate RO-Crate

```bash
python tools/ValidateROCrate.py input-rocrate.json --no-convert
```

## Tools

### ConvertToROCrate.py

Transforms CDIF/ADA nested JSON-LD into RO-Crate 1.1 flat `@graph` form using standard JSON-LD operations (expand, flatten, compact). Injects the RO-Crate metadata descriptor and remaps the root Dataset `@id` to `"./"`.

### ROCrateToCDIF.py

Converts an RO-Crate `@graph` document back to CDIF nested JSON-LD. Handles both distribution patterns:
- **Multiple independent DataDownloads** -- each with its own `contentUrl`
- **Archive distributions** -- a single DataDownload with `hasPart` containing MediaObject components

Also creates `schema:subjectOf` (CDIF catalog record) from the RO-Crate metadata descriptor, with `dcterms:conformsTo` pointing to the specified CDIF profile (discovery or complete).

### ValidateROCrate.py

Validates RO-Crate documents against 13 structural checks (flat graph, metadata descriptor, root dataset, etc.) and optionally runs SHACL validation via `rocrate-validator`.

## Documentation

See [docs/RO-Crate-relationship.md](docs/RO-Crate-relationship.md) for detailed property mappings between CDIF and RO-Crate, structural differences, pipeline diagrams, and round-trip examples.

## Examples

The `examples/` directory contains RO-Crate files generated from ADA/CDIF test metadata. Files with `-INVALID` in the name are older examples that do not pass RO-Crate validation (kept for reference).

---

## History Notes

This repository was created to explore integration between CDIF metadata and various dataset packaging formats. Early targets for investigation included:

### RO-Crate

[RO-Crate](https://www.researchobject.org/ro-crate/specification/1.2/metadata.html#base-metadata-standard-schemaorg) uses schema.org for base metadata and adds namespace extensions from several vocabularies:

- [PCDM](https://pcdm.org/2016/04/18/models) -- for describing repositories or collections of digital objects
- [Profiles Vocabulary](https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/) -- for describing profiles
- [Dublin Core Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/) -- `conformsTo`, `Standard`
- [IANA Link Relations](https://www.iana.org/assignments/link-relations/) -- `cite-as`
- [GeoSPARQL](https://opengeospatial.github.io/ogc-geosparql/geosparql11/) -- `Geometry`, `asWKT`
- [Bioschemas](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) -- `ComputationalWorkflow`, `FormalParameter`, `input`, `output`
- [CodeMeta 3.0](https://w3id.org/codemeta/3.0) -- software-related properties
- RO-Crate community namespace -- for terms not covered by other vocabularies (e.g., `localPath`)

### Croissant

[Croissant](https://docs.mlcommons.org/croissant/docs/croissant-spec.html) uses schema.org for base metadata. A Croissant description contains general information about the dataset (name, description, license, URL). Croissant modifies schema.org `distribution` to specify expected types: `crs:FileObject` | `crs:FileSet`, and defines `isLiveDataset` and `citeAs`. `FileObject` has `schema:CreativeWork` properties plus `containedIn`. `FileSet` likewise adds `containedIn`, `includes`, `excludes` (using [glob patterns](https://en.wikipedia.org/wiki/Glob_(programming))). `RecordSet` describes how content within the resources is organized.

See also: [Croissant working documents](https://drive.google.com/drive/folders/1a5J20z_BnFNjGfnxeIQ7kG2BXq7iUe00?usp=drive_link)

### Other Formats

- **BagIt** -- under consideration
- **Planetary Data System Bundle** -- under consideration
