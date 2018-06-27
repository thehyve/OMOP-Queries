# PE09: Number of patients by gender, stratified by year of birth

Count the genders (gender_concept_id) across all person records, arrange into groups by year of birth. All possible values for gender concepts stratified by year of birth are summarized.

## Sample query

```sql
SELECT
  gender_concept_id,
  concept_name     AS gender_name,
  year_of_birth,
  COUNT(*) AS num_persons
FROM person p
  JOIN concept c ON p.gender_concept_id = c.concept_id
GROUP BY gender_concept_id, concept_name, year_of_birth
ORDER BY concept_name, year_of_birth
;
```
### Input

None

### Output

|  Field |  Description |
| --- | --- |
|  gender_concept_id |  CDM vocabulary concept identifier |
|  gender_name |  Gender name as defined in CDM vocabulary |
|  year_of_birth |  Stratification by year of birth |
|  num_persons |  Number of patients in the dataset of specific gender / year of birth |

### Sample output record

|  Field |  Value |
| --- | --- |
|  gender_concept_id |  8507 |
|  gender_name |  MALE |
|  year_of_birth |  1950 |
|  num_persons |  169002 |

## Documentation
https://github.com/OHDSI/CommonDataModel/wiki/PERSON