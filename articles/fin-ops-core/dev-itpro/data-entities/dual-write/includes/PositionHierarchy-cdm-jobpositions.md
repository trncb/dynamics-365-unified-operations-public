## Position hierarchies to cdm_jobpositions

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations apps | Map type | Customer engagement apps | Default value
---|---|---|---
POSITIONID | = | cdm_jobpositionnumber | 
PARENTPOSITIONID | = | cdm_parentjobpositionid.cdm_jobpositionnumber | 
HIERARCHYTYPENAME | << | none | Line
VALIDFROM | << | cdm_validfrom | 
VALIDTO | << | cdm_validto | 
