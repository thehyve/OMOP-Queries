# PE02: Number of patients of specific gender in the dataset

Use this query to determine the number of women and men in an a databse. The gender concept code for women is 8532 and for men is 8507. There are also unknown gender (8551), other (8521) and ambiguous (8570).

## Sample query

```sql
SELECT COUNT(person_id) AS num_persons_count
FROM person
WHERE gender_concept_id = 8532 -- PARAMETER
```
### Input

| Parameter |  Example |  Mandatory |  Notes |
| --- | --- | --- | --- |
| Gender Concept ID | 8532 | Yes | Concept Identifier for 'female' |

### Output

| Field |  Description |
| --- | --- |
| num_persons_count | Number of patients in the dataset of specific gender |

### Sample output record

|  Field |  Value |
| --- | --- |
| num_persons_count | 2859298 |


## Documentation
https://github.com/OHDSI/CommonDataModel/wiki/PERSON