# aviary-iiif-test-samples

This is a sample [IIIF Presentation (v3)](https://iiif.io/api/presentation/3.0/) manifest for a [video](https://nunncenter.aviaryplatform.com/collections/1/collection_resources/1) with OHMS index points and full transcript in Aviary. Manifests would be generated by Aviary based on the following mapping and templated data and served through a IIIF Presentation (v3) API. 

Index Annotations (including title, partial transcript, synopsis, subjects, and keywords) are grouped as one AnnotationPage per index point and associated with the top-level painting Canvas. The transcript is split into one segment per Annotation with Annotations grouped as one AnnotationPage and associated with the top-level painting Canvas. Index AnnotationPages and the transcript AnnotationPage are members of an AnnotationCollection. (AnnotationCollection data would also be available through the Presentation API and is included here as a separate JSON file for demonstration purposes.) Additional annotation sets created by the provider or users would be included in their own AnnotationCollections so as to individually manage administrative metadata and access restrictions. 

| Presentation (v3) manifest                   | Aviary                                                                                    | Notes                                                                                                                                                                                                                                                                                                                                                            |
|----------------------------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Manifest**                                     |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| @id                                          | [Aviary resource manifest URL]                                                            |                                                                                                                                                                                                                                                                                                                                                                  |
| @type                                        | “Manifest”                                                                                |                                                                                                                                                                                                                                                                                                                                                                  |
| label                                        | Title                                                                                     |                                                                                                                                                                                                                                                                                                                                                                  |
| metadata                                     | ‘Author’: Agent‘Publisher’: Publisher‘Language’: Language‘Date’: Date‘Format’: Format     | Array of label/value objects (required/minimum metadata fields TBD)                                                                                                                                                                                                                                                                                              |
| summary                                      | Description                                                                               |                                                                                                                                                                                                                                                                                                                                                                  |
| thumbnail                                    |                                                                                           | List of default or user-submitted thumbnails (not included in this example)                                                                                                                                                                                                                                                                                      |
| requiredStatement                            | Rights Statement                                                                          | Array of label/value objects for Attribution and Copyright                                                                                                                                                                                                                                                                                                       |
| provider                                     |                                                                                           | Organization information                                                                                                                                                                                                                                                                                                                                         |
| provider.[*].id                              | Organization URL                                                                          |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].type                            | “Agent”                                                                                   |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].label                           | Organization Name                                                                         |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].homepage                        |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].homepage[*].id                  | Organization Aviary URL                                                                   |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].homepage[*].type                | “Text”                                                                                    |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].homepage[*].label               | Organization Name                                                                         |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].homepage[*].format              | “text/html”                                                                               |                                                                                                                                                                                                                                                                                                                                                                  |
| provider.[*].logo                            | Organization Logo                                                                         | If provided (not included in this example)                                                                                                                                                                                                                                                                                                                       |
| provider.[*].logo.@id                        | [Organization logo URL]                                                                   |                                                                                                                                                                                                                                                                                                                                                                  |
| items                                        |                                                                                           | Canvas (see below)                                                                                                                                                                                                                                                                                                                                               |
| **Canvas**                                       |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| id                                           | [Aviary resource URL + canvas id]                                                         | Video sequence id                                                                                                                                                                                                                                                                                                                                                |
| type                                         | “Canvas”                                                                                  |                                                                                                                                                                                                                                                                                                                                                                  |
| label                                        | “Video [sequence] of [total videos]”                                                      |                                                                                                                                                                                                                                                                                                                                                                  |
| duration                                     | [File duration]                                                                           | In seconds (float)                                                                                                                                                                                                                                                                                                                                               |
| height                                       |                                                                                           | (Are we storing this somewhere from tech metadata?)                                                                                                                                                                                                                                                                                                              |
| width                                        |                                                                                           | See above                                                                                                                                                                                                                                                                                                                                                        |
| items                                        |                                                                                           | Painting AnnotationPage (see below)                                                                                                                                                                                                                                                                                                                              |
| annotations                                  |                                                                                           | AnnotationPage objects (see below)                                                                                                                                                                                                                                                                                                                               |
| **AnnotationPage (Painting)**                   |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| id                                           | [Aviary resource URL + canvas id + painting annotation page id]                           | Will likely be 1 (one painting AnnotationPage per canvas)                                                                                                                                                                                                                                                                                                        |
| type                                         | “AnnotationPage”                                                                          |                                                                                                                                                                                                                                                                                                                                                                  |
| items                                        |                                                                                           | Painting Annotation (see below)                                                                                                                                                                                                                                                                                                                                  |
| **Annotation (Painting)**                        |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| id                                           | [Aviary resource URL + canvas id + painting annotation page id]                           | Will likely be 1 (one painting Annotation per AnnotationPage or the first Annotation)                                                                                                                                                                                                                                                                            |
| type                                         | “Annotation”                                                                              |                                                                                                                                                                                                                                                                                                                                                                  |
| motivation                                   | “painting”                                                                                |                                                                                                                                                                                                                                                                                                                                                                  |
| body                                         |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| body.id                                      | [direct video url]                                                                        | Will be source video url if embedded                                                                                                                                                                                                                                                                                                                             |
| body.type                                    | “Video”                                                                                   |                                                                                                                                                                                                                                                                                                                                                                  |
| body.format                                  | “video/[format]”                                                                          | Will usually be “mp4”                                                                                                                                                                                                                                                                                                                                            |
| body.duration                                | [video duration]                                                                          | In seconds (float)                                                                                                                                                                                                                                                                                                                                               |
| body.height                                  |                                                                                           | (Are we storing this somewhere from tech metadata?)                                                                                                                                                                                                                                                                                                              |
| body.width                                   |                                                                                           | See above                                                                                                                                                                                                                                                                                                                                                        |
| target                                       | [parent Canvas id]                                                                        |                                                                                                                                                                                                                                                                                                                                                                  |
| **AnnotationPage (Index points and transcript)** |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| id                                           | [Aviary resource URL + canvas id + annotation page id]                                    | Database-generated identifiers? User-defined annotation sequence? TBD                                                                                                                                                                                                                                                                                            |
| type                                         | “AnnotationPage”                                                                          |                                                                                                                                                                                                                                                                                                                                                                  |
| partOf                                       | [AnnotationCollection URI of parent annotation set]                                       |                                                                                                                                                                                                                                                                                                                                                                  |
| items                                        |                                                                                           | Annotations (see below)                                                                                                                                                                                                                                                                                                                                          |
| **Annotation (Index points and transcript)**     |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| id                                           |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| type                                         |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| label                                        | [type of annotation, ex. “Transcript”]                                                    | Label serves as both display label for annotation and to further refine motivations (below) for mediating display/behavior                                                                                                                                                                                                                                       |
| motivation                                   | “supplementing”, [additional motivation from controlled Web Annotation list]              | List of motivations -- “supplementing” is required. Add additional motivation based on function. Mapping:OHMS index title > “describing”OHMS index synopsis > “describing”OHMS index partial transcript > “describing”OHMS index subject > “tagging”OHMS index keyword > “tagging”Transcript > “transcribing”? (no applicable motivation in Web Annotation list) |
| body                                         |                                                                                           | May be single body or multiple bodies for multiple instances of similar annotations for the defined time point or range (ex. Subjects or keywords)                                                                                                                                                                                                               |
| body.type                                    | “TextualBody”                                                                             |                                                                                                                                                                                                                                                                                                                                                                  |
| body.value                                   | [annotation value]                                                                        |                                                                                                                                                                                                                                                                                                                                                                  |
| body.format                                  | [annotation type, will usually be text/plain or text/vtt (or possible text/html for vtt)] |                                                                                                                                                                                                                                                                                                                                                                  |
| target                                       |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| target.source                                | [parent Canvas id]                                                                        |                                                                                                                                                                                                                                                                                                                                                                  |
| target.selector                              |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| target.selector.type                         | “PointSelector”                                                                           | Or “RangeSelector” for time range                                                                                                                                                                                                                                                                                                                                |
| target.selector.t                            | [annotation timecode]                                                                     | In seconds (float). Used with PointSelector                                                                                                                                                                                                                                                                                                                      |
| target.selector.startSelector                |                                                                                           | Used with “RangeSelector”                                                                                                                                                                                                                                                                                                                                        |
| target.selector.startSelector.type           | “PointSelector”                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| target.selector.startSelector.t              | [annotation start timecode]                                                               | In seconds (float)                                                                                                                                                                                                                                                                                                                                               |
| target.selector.endSelector                  |                                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| target.selector.endSelector.type             | “PointSelector”                                                                           |                                                                                                                                                                                                                                                                                                                                                                  |
| target.selector.endSelector.t                | [annotation endtimecode]                                                                  | In seconds (float)                                                                                                                                                                                                                                                                                                                                               |