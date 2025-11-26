# packaging
This folder is for work related to description of datasets that are delivered using one of the various packaging formats in use.


Near term targets for integration

[RO-CRATES](https://www.researchobject.org/ro-crate/specification/1.2/metadata.html#base-metadata-standard-schemaorg)-- uses schema.org for base metadata, adds namespace extensions from (PCDM version https://pcdm.org/2016/04/18/models) to describe repositories or collections of digital objects and imports these terms:, [Profiles Vocabulary](https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/) to describe profiles;  Dublin Core Terms  conformsTo, Standard; [IANA link relations](https://www.iana.org/assignments/link-relations/) registry cite-as; [GeoSPARQL ontology](https://opengeospatial.github.io/ogc-geosparql/geosparql11/) Geometry  and asWKT; [Bioschemas profile ComputationalWorkflow 1.0-RELEASE](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) and [FormalParameter 1.0-RELEASE]( ComputationalWorkflow , FormalParameter , input , output ; Several properties from CodeMeta 3.0 mostly related to software;  RO-Crate community maintains a common namespace for terms not covered by other vocabularies. localPath
[RO-CRATES](https://www.researchobject.org/ro-crate/specification/1.2/metadata.html#base-metadata-standard-schemaorg)-- uses schema.org for base metadata, adds namespace extensions from (PCDM version https://pcdm.org/2016/04/18/models) to describe repositories or collections of digital objects and imports these terms:, [Profiles Vocabulary](https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/) to describe profiles;  Dublin Core Terms  conformsTo, Standard; [IANA link relations](https://www.iana.org/assignments/link-relations/) registry cite-as; [GeoSPARQL ontology](https://opengeospatial.github.io/ogc-geosparql/geosparql11/) Geometry  and asWKT; [Bioschemas profile ComputationalWorkflow 1.0-RELEASE](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) and [FormalParameter 1.0-RELEASE]( ComputationalWorkflow , FormalParameter , input , output ; Several properties from CodeMeta 3.0 mostly related to software;  RO-Crate community maintains a common namespace for terms not covered by other vocabularies. localPath
[RO-CRATES](https://www.researchobject.org/ro-crate/specification/1.2/metadata.html#base-metadata-standard-schemaorg)-- uses schema.org for base metadata, adds namespace extensions from (PCDM version https://pcdm.org/2016/04/18/models) to describe repositories or collections of digital objects and imports these terms:, [Profiles Vocabulary](https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/) to describe profiles;  Dublin Core Terms  conformsTo, Standard; [IANA link relations](https://www.iana.org/assignments/link-relations/) registry cite-as; [GeoSPARQL ontology](https://opengeospatial.github.io/ogc-geosparql/geosparql11/) Geometry  and asWKT; [Bioschemas profile ComputationalWorkflow 1.0-RELEASE](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) and [FormalParameter 1.0-RELEASE](https://bioschemas.org/profiles/FormalParameter/1.0-RELEASE) ComputationalWorkflow , FormalParameter , input , output ; Several properties from [CodeMeta 3.0](https://w3id.org/codemeta/3.0) mostly related to software;  RO-Crate community maintains a common namespace for terms not covered by other vocabularies. localPath
 

Croissant -- uses schema.org for base metadata, Croissant description contains general information about the dataset such as name, short description, license and URL. Most of these attributes are from schema.org, with a few additions described in the [Dataset-level information](https://docs.mlcommons.org/croissant/docs/croissant-spec.html#dataset-level-information).  Croissant modifies schema.org distribution to specify expected type: crs:FiileObject | crs:FileSet; also defines isLiveDataset and citeAs.  FileObject has schema:creativeWork properties, adds containedIn.  FileSet likewise, but adds containedIn, includes, excludes.  Includes and excludes are [glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) that specifies the files to include.

	Recordset: how content within the resources is organized.

	see also https://drive.google.com/drive/folders/1a5J20z_BnFNjGfnxeIQ7kG2BXq7iUe00?usp=drive_link


Bagit


Planetary Data System Bundle
