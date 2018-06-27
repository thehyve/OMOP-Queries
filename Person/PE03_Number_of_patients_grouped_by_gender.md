# PE03: Number of patients grouped by gender

This query is similar to PE02, but it lists all available genders (male, female, unknown, ambiguous, other) across all person records. The input to the query is a value (or a comma-separated list of values) of a gender_concept_id. If the input is omitted, all possible values for gender_concept_id are summarized.

## Sample query

```sql
SELECT
  person.gender_concept_id,
  concept.concept_name    AS gender_name,
  COUNT(person.person_id) AS num_persons_count
FROM person
  JOIN concept ON person.gender_concept_id = concept.concept_id
GROUP BY person.gender_concept_id, concept.concept_name
;
```
### Input

None

### Output

|  Field |  Description |
| --- | --- |
| Gender_concept_ID |  Gender concept ID as defined in CDM vocabulary |
| Gender_Name | Gender name as defined in CDM vocabulary |
| Num_Persons_count | Count of patients with specific gender ID |

### Sample output record

|  Field |  Value |
| --- | --- |
| Gender_concept_ID | 8507 |
| Gender_Name | Male |
| Num_Persons_count | 1607473 |


## Documentation
https://github.com/OHDSI/CommonDataModel/wiki/PERSON