# Experiment 4: Applying CRUD (Scenarios)

## Scenario 1: Task Management

### Commands
```mongodb
use taskdb

db.createCollection("tasks")

db.tasks.insertOne({
  task: "frontend development",
  assigned_to: "alice",
  status: "in progress",
  deadline: "2025-03-01"
})

db.tasks.updateOne(
  {task: "frontend development"},
  {$set: {status: "completed"}}
)

db.tasks.updateOne(
  {task: "frontend development"},
  {$set: {deadline: "2025-04-01"}}
)

db.tasks.updateOne(
  {task: "frontend development"},
  {$set: {assigned_to: "bob"}}
)

db.tasks.find({
  assigned_to: "alice",
  status: "in progress"
})

db.tasks.deleteOne({task: "frontend development"})
```

### Result
Task document inserted, updated, queried, and deleted successfully.

## Scenario 2: Testing Team

### Commands
```mongodb
use testdb

db.createCollection("testers")
db.createCollection("testcases")

db.testers.insertOne({
  name: "alice",
  role: "QA Engineer"
})

db.testcases.insertOne({
  name: "Login Test",
  status: "in progress",
  assigned_to: "alice",
  priority: "high"
})

db.testcases.updateOne(
  {name: "Login Test"},
  {$set: {status: "passed"}}
)

db.testcases.insertOne({
  name: "Signup Test",
  status: "failed",
  assigned_to: "bob"
})

db.testers.updateOne(
  {name: "alice"},
  {$set: {role: "Senior QA Engineer"}}
)

db.testcases.find(
  {assigned_to: "alice"},
  {name: 1, status: 1, priority: 1}
)

db.testcases.deleteOne({name: "Signup Test"})
```

### Result
Tester and testcase records were inserted, updated, queried, and deleted successfully.

## Scenario 3: Student Management

### Commands
```mongodb
use studentdb

db.createCollection("students")

db.students.insertMany([
  {
    name: "Alice Johnson",
    age: 16,
    grade: "10th",
    courses: ["Math", "Science", "English"]
  },
  {
    name: "Bob Smith",
    age: 15,
    grade: "9th",
    courses: ["History", "Math", "Geography"]
  }
])

db.students.updateOne(
  {name: "Alice Johnson"},
  {$set: {grade: "11th"}}
)

db.students.updateOne(
  {name: "Alice Johnson"},
  {$push: {courses: "History"}}
)

db.students.updateOne(
  {name: "Bob Smith"},
  {$set: {age: 16}}
)

db.students.find({courses: "Math"})
db.students.find({grade: "10th"})
db.students.find({age: {$gt: 15}})

db.students.deleteOne({name: "Bob Smith"})

db.students.updateOne(
  {name: "Bob Smith"},
  {$pull: {courses: "Geography"}}
)
```

### Result
Student records were created, updated, filtered, and deleted successfully.

## Scenario 4: Hospital Management

### Commands
```mongodb
use HospitalDB

db.createCollection("patients")

db.patients.insertMany([
  {
    patient_id: 1,
    name: "John",
    age: 45,
    diagnosis: "Diabetes",
    treatment_plan: "Insulin"
  },
  {
    patient_id: 2,
    name: "Mary",
    age: 50,
    diagnosis: "Hypertension",
    treatment_plan: "Medication"
  }
])

db.patients.find({diagnosis: "Diabetes"})

db.patients.find(
  {diagnosis: "Diabetes"},
  {name: 1, treatment_plan: 1, _id: 0}
)

db.patients.deleteMany({})
```

### Result
Hospital patient data was inserted, queried with projection, and deleted successfully.

## Scenario 5: Course Registration

### Commands
```mongodb
use university

db.createCollection("courses")

db.courses.insertMany([
  {
    course_id: "CS101",
    course_name: "DBMS",
    instructor: "Dr. Smith",
    enrolled_students: []
  },
  {
    course_id: "CS102",
    course_name: "OS",
    instructor: "Dr. John",
    enrolled_students: []
  },
  {
    course_id: "CS103",
    course_name: "AI",
    instructor: "Dr. Smith",
    enrolled_students: []
  }
])

db.courses.updateOne(
  {course_id: "CS101"},
  {$push: {enrolled_students: {$each: ["S1001","S1002","S1003"]}}}
)

db.courses.find(
  {instructor: "Dr. Smith"},
  {course_name: 1, enrolled_students: 1, _id: 0}
)

db.courses.deleteMany({enrolled_students: {$size: 0}})
```

### Result
Course documents were inserted, student enrollment was updated, records were queried, and empty courses were deleted successfully.Experiment4.md
