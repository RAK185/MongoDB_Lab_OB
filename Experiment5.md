# Experiment 5: Filtering and Projection

## Aim
To perform filtering and projection operations in MongoDB.

## Steps
1. Open Mongo shell using `mongosh`.
2. Switch to the required database using `use studentdb`.
3. Ensure the `students` collection contains documents.
4. Apply a filter condition to retrieve students whose age is greater than 15.
5. Use projection to display only the `name` and `age` fields.
6. Exclude the `_id` field from the output.
7. Execute the query and verify the result.

## Command
```javascript
use studentdb

db.students.find(
  { age: { $gt: 15 } },
  { name: 1, age: 1, _id: 0 }
)
```

## Expected Output
Displays only the student name and age for documents where age is greater than 15.
