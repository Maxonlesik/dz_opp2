class Student:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.finished_courses = []
        self.courses_in_progress = []
        self.grades = {}
    
    def srgr(self):
        grades_count=0
        if not self.grades:
            return 0
        spisok=[]
        for k in self.grades:
             grades_count += len(self.grades[k])
             spisok.extent(k)
        return float(sum(spisok)/max(len(spisok), 1))
    def rate_hw(self, lecturer, course, grade):
        if isinstance(lecturer,Lecturer) and course in self.courses_in_progress and course in lecturer.courses_attached:
           if course in lecturer.grades:
               lecturer.grades[course] += [grade]
           else:
               lecturer.grades[course] = [grade]
        else:
            return'Ошибка'  
class Mentor:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.courses_attached = []
    
class Lecturer(Mentor):
    def __init__(self, name, surname):
        super().__init__(name, surname)
        self.grades = {}
        self.srgr = float()
        
    def srgr(self):
        grades_count=0
        if not self.grades:
            return 0
        spisok=[]
        for k in self.grades.values():
           grades_count += len(self.grades[k])
           spisok.extent(k)
        return round(sum(spisok)/len(spisok), 2)
   
class Reviewer(Mentor):
    def __init__(self, name, surname):
        super().__init__(name, surname)
    
    def rate_hw(self, student, course, grade):
        if isinstance(student, Student) and course in self.courses_attached and course in student.courses_in_progress:
            if course in student.grades:
                student.grades[course] += [grade]
            else:
                student.grades[course] = [grade]
        else:
            return 'Ошибка'
