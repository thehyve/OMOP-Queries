# CO16: Counts of number of distinct conditions persons have

This query is used to count the number of different distinct conditions (condition_concept_id) of all persons. The input to the query is a value for a concept identifier.

## Sample query
```sql
SELECT count(c.condition_concept_id) conditions_count, c.person_id
FROM condition_occurrence c
WHERE condition_concept_id = 201820
GROUP BY c.person_id
ORDER BY 1
DESC;
```

### Input

|  Parameter |  Example |  Mandatory |  Notes |
| --- | --- | --- | --- |
| condition_concept_id | 201820 | Yes | Condition concept identifier for 'Diabetes mellitus' |

### Output

|  Field |  Description |
| --- | --- |
| conditions_count | Number of conditions recorded for the person |
| person_id | Person identifier |

### Sample output record

|  Field |  Description |
| --- | --- |
| conditions_count |  39 |
| person_id |  20017834818 |


## Documentation
https://github.com/OHDSI/CommonDataModel/wiki/