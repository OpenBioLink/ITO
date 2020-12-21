# Natural language processing task hierarchy JSON export 
(State: 21.12.2020)

For each class, the JSON can contain the following fields (if available):

## Annotation fields

| Field | Description | Example |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------|---|
| papers_with_code_id | Original task id from Papers With Code. Classes that have no `papers_with_code_id` field have been introduced by us while re-structuring the task hierarchy.  | Sentence Classification
| name                | Task label. If no changes were introduced, this field is identical to `papers_with_code_id`. |   Sentence Classification |                                                                                                                   |
| hasExactSynonym     | List of exact synonyms for the task name |   An exact synonym for 'Named entity recognition' would be 'Entity identification'. |                                                                                                     |                                                                                                     |
| description         | Description of the task | Task: "Cross-Lingual Natural Language Inference", Description: "Using data and models available for one language for which ample such resources are available (e.g., English) to solve a natural language inference task in another, commonly more low-resource, language."                                                                                                        |
| seeAlso             | Further references such as Wikipedia articles or other sources further describing the respective task, if available.            |
| comment             | General annotation comments                                                                                                     |
| refactor_comment    | Classes that we have marked for refactoring include a refactoring comment                                                                 |


## Relationship fields

| Field      | Description                             | Example |
|------------|-----------------------------------------| --- | 
| has_input  | Data class serving as input to the task | Task: 'Sentence embedding', Input data class: 'Sentence' |
| has_output | Output data class of the task | Task: 'Sentence embedding', Output data class: 'Vector' |