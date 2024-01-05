[[OOP]]
---
 - [ ] TODO: Check if reviewed.
# Object Composition
## Association
Relationship of data. Think of how database schemas function.
```csharp
// Student class
public class Student
{
    public int StudentId { get; set; }
    public string Name { get; set; }
    // Other student properties and methods
}

// Course class
public class Course
{
    public int CourseId { get; set; }
    public string Title { get; set; }
    // Other course properties and methods
}

// Association class representing the enrollment
public class Enrollment
{
    public Student Student { get; set; }
    public Course Course { get; set; }
    public DateTime EnrollmentDate { get; set; }
    public string Grade { get; set; }
    // Other properties related to enrollment

    // Constructor
    public Enrollment(Student student, Course course, DateTime enrollmentDate, string grade)
    {
        Student = student;
        Course = course;
        EnrollmentDate = enrollmentDate;
        Grade = grade;
    }
 // Other methods related to enrollment
}
 ```

The above code establishes various data in `Student`, `Course`, and `Enrollment`. Following this, we establish relationships
```csharp
Student student1 = new Student { StudentId = 1, Name = "John Doe" };
Course course1 = new Course { CourseId = 101, Title = "Computer Science" };
DateTime enrollmentDate = DateTime.Now;
string grade = "A";

Enrollment enrollment1 = new Enrollment(student1, course1, enrollmentDate, grade);
// You can access the associated objects and their properties:
Console.WriteLine($"Student: {enrollment1.Student.Name}, Course: {enrollment1.Course.Title}, Grade: {enrollment1.Grade}");
 ```

## Aggregation
A specialized version of `Association` where all objects have their own lifecycle but there is ownership. The child object cannot belong to another parent object.

```csharp
public class University {
    public List<Department> Departments { get; set; }
    // Other university properties and methods
}

public class Department {
    public string Name { get; set; }
    public List<Professor> Professors { get; set; }
    // Other department properties and methods
}

public class Professor {
    public string Name { get; set; }
    // Other professor properties and methods
}

```

- **University** has multiple **Departments**.
- Each **Department** has multiple **Professors**.
 Here, the relationship between University and Departments, and between Departments and Professors, demonstrates aggregation. Departments exist independently and can exist without the University. Professors are associated with Departments but can exist outside a specific department or even the university.

## Composition
A specialized version of `Aggregation` where child objects do not have lifecycles without parent objects. If parent objects are deleted, child objects are also deleted.

```csharp
public class Computer {
    public CPU Cpu { get; set; }
    public RAM Ram { get; set; }
    public HardDrive HDD { get; set; }
    // Other computer properties and methods
}

public class CPU {
    // CPU properties and methods
}

public class RAM {
    // RAM properties and methods
}

public class HardDrive {
    // Hard Drive properties and methods
}

```

- A **Computer** consists of a **CPU**, **RAM**, and **Hard Drive**.
- If the computer is destroyed, its components (CPU, RAM, Hard Drive) also cease to exist as a functional part of that computer.
