# C04: Translate a MedDRA concept into a SNOMED-CT concept

This query accepts a MedDRA concept ID as input and returns details of the equivalent SNOMED-CT concepts.

The existing relationships in the vocabulary associate MedDRA 'Preferred Term' to SNOMED-CT 'clinical findings'. The respective hierarchy for MedDRA and SNOMED-CT can be used to traverse up and down the hierarchy of each of these individual vocabularies.

## Sample query

The following is a sample run of the query to list all MedDRA concepts that have SNOMED-CT equivalents. Sample parameter substitution is highlighted.

```sql
SELECT
  d.concept_id         AS meddra_concept_id,
  d.concept_name       AS meddra_concept_name,
  d.concept_code       AS meddra_concept_code,
  d.concept_class_id   AS meddra_concept_class,
  cr.relationship_id   AS relationship_id,
  a.concept_id         AS snomed_concept_id,
  a.concept_name       AS snomed_concept_name,
  a.concept_code       AS snomed_concept_code,
  a.concept_class_id   AS snomed_concept_class
FROM concept_relationship AS cr
  JOIN concept AS d ON cr.concept_id_1 = d.concept_id
  JOIN concept AS a ON cr.concept_id_2 = a.concept_id
WHERE cr.relationship_id = 'MedDRA - SNOMED eq'
      AND cr.concept_id_1 = 35205180 -- PARAMETER
      AND current_date BETWEEN cr.valid_start_date AND cr.valid_end_date -- PARAMETER
;
```

### Input

|  Parameter |  Example |  Mandatory |  Notes |
| --- | --- | --- | --- |
|  MedDRA Concept ID |  35205180 |  Yes | Concept Identifier for 'Acute myocardial infarction' |
|  As of date |  Sysdate |  No | Valid record as of specific date. Current date – sysdate is a default |

### Output

#### Output field list

|  Field |  Description |
| --- | --- |
|  MedDRA_Concept_ID |  Concept ID of MedDRA concept entered as input |
|  MedDRA_Concept_Name |  Concept name of MedDRA concept |
|  MedDRA_Concept_Code |  Concept code of MedDRA concept |
|  MedDRA_Concept_Class |  Concept class of MedDRA concept |
|  Relationship_ID |  Identifier for the type of relationship |
|  SNOMED-CT_Concept_ID |  Concept ID of matching SNOMED-CT concept |
|  SNOMED-CT_Concept_Name |  Name of matching SNOMED-CT concept |
|  SNOMED-CT_Concept_Code |  Concept Code of matching SNOMED-CT concept |
|  SNOMED-CT_Concept_Class |  Concept class of matching SNOMED-CT concept |

#### Sample output record

|  Field |  Value |
| --- | --- |
|  MedDRA_Concept_ID |  35205180 |
|  MedDRA_Concept_Name |  Acute myocardial infarction |
|  MedDRA_Concept_Code |  10000891 |
|  MedDRA_Concept_Class |  Preferred Term |
|  Relationship_ID |  MedDRA - SNOMED eq |
|  SNOMED-CT_Concept_ID |  312327 |
|  SNOMED-CT_Concept_Name |  Acute myocardial infarction |
|  SNOMED-CT_Concept_Code |  57054005 |
|  SNOMED-CT_Concept_Class |  Clinical finding |


## Documentation
https://github.com/OHDSI/CommonDataModel/wiki/CONCEPT_RELATIONSHIP