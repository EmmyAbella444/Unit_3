# QUIZ 036

![Screen Shot 2023-01-19 at 10 54 53](https://user-images.githubusercontent.com/111819437/213337317-976ac217-cd6c-4127-b0ec-f4741648f022.png)


## CODE
```.py


class Person:
    def __init__(self,name,age):
        self.name = name
        self.age = age

    def get_age(self):
        return self.age

    def get_name(self):
        return self.name

class Classroom:
    def __init__(self):
        self.student = []

    def add_student(self,student):
        self.student.append(student)

    def remove_student(self,student):
        self.student.remove(student)

    def get_average(self):
        sum_total = 0
        for student in self.student:
            sum_total = sum_total + student.get_grade()
        average = sum_total / len(self.student)
        return average


class Student(Person):
    def __init__(self,grade,name ,age):
        self.grade = grade
        super().__init__(name,age)

    def get_grade(self):
        return self.grade


```

## EVIDENCE

```.py
from QUIZ_036 import Person, Classroom, Student
import pytest

def test_get_age():
    student = Student(name="BOB", age=18,grade=7)
    assert student.get_age() == 18
    assert student.get_name() == "BOB"
    assert student.get_grade() == 7

def test_average():
    Bob = Student(name="BOB", age=18,grade=7)
    Alice = Student(name="ALICE", age=17,grade=3)

    KAC3 = Classroom()
    KAC3.add_student(Alice)
    KAC3.add_student(Bob)

    assert KAC3.get_average() == 5

```

![Screen Shot 2023-01-19 at 22 56 01](https://user-images.githubusercontent.com/111819437/213460821-a08fc1f8-b488-47f4-af6c-2666129edcf3.png)

## UML DIAGRAM
![Screen Shot 2023-02-06 at 11 18 38](https://user-images.githubusercontent.com/111819437/216868154-48c1ab9b-b23e-48b9-91e9-3f5030692817.png)


