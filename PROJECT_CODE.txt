class Student:
    def __init__(self, roll_no, name, age, department, marks):
        self.roll_no = roll_no
        self.name = name
        self.age = age
        self.department = department
        self.marks = marks

    def grade(self):
        if self.marks >= 90:
            return "A+"
        elif self.marks >= 80:
            return "A"
        elif self.marks >= 70:
            return "B"
        elif self.marks >= 60:
            return "C"
        elif self.marks >= 50:
            return "D"
        return "F"

    def display(self):
        print("-" * 50)
        print(f"Roll No    : {self.roll_no}")
        print(f"Name       : {self.name}")
        print(f"Age        : {self.age}")
        print(f"Department : {self.department}")
        print(f"Marks      : {self.marks}")
        print(f"Grade      : {self.grade()}")
        print("-" * 50)


class StudentManagementSystem:
    def __init__(self):
        self.students = []

    def add_student(self):
        roll_no = input("Enter Roll No: ")

        for student in self.students:
            if student.roll_no == roll_no:
                print("Student already exists.")
                return

        name = input("Enter Name: ")
        age = int(input("Enter Age: "))
        department = input("Enter Department: ")
        marks = float(input("Enter Marks: "))

        student = Student(
            roll_no,
            name,
            age,
            department,
            marks
        )

        self.students.append(student)

        print("Student added successfully.")

    def view_students(self):
        if not self.students:
            print("No students found.")
            return

        print("\nSTUDENT RECORDS")
        print("=" * 70)

        for student in self.students:
            print(
                f"{student.roll_no:<10}"
                f"{student.name:<20}"
                f"{student.department:<15}"
                f"{student.marks:<10}"
                f"{student.grade()}"
            )

    def search_student(self):
        roll_no = input("Enter Roll No: ")

        for student in self.students:
            if student.roll_no == roll_no:
                student.display()
                return

        print("Student not found.")

    def update_student(self):
        roll_no = input("Enter Roll No to update: ")

        for student in self.students:
            if student.roll_no == roll_no:
                student.name = input("New Name: ")
                student.age = int(input("New Age: "))
                student.department = input("New Department: ")
                student.marks = float(input("New Marks: "))

                print("Student updated successfully.")
                return

        print("Student not found.")

    def delete_student(self):
        roll_no = input("Enter Roll No to delete: ")

        for student in self.students:
            if student.roll_no == roll_no:
                self.students.remove(student)
                print("Student deleted successfully.")
                return

        print("Student not found.")

    def statistics(self):
        if not self.students:
            print("No student data available.")
            return

        total = len(self.students)

        marks_list = [student.marks for student in self.students]

        average = sum(marks_list) / total
        highest = max(marks_list)
        lowest = min(marks_list)

        print("\nSTATISTICS")
        print("=" * 30)
        print(f"Total Students : {total}")
        print(f"Average Marks  : {average:.2f}")
        print(f"Highest Marks  : {highest}")
        print(f"Lowest Marks   : {lowest}")

    def run(self):
        while True:
            print("\n")
            print("=" * 40)
            print(" STUDENT MANAGEMENT SYSTEM ")
            print("=" * 40)
            print("1. Add Student")
            print("2. View Students")
            print("3. Search Student")
            print("4. Update Student")
            print("5. Delete Student")
            print("6. Statistics")
            print("7. Exit")

            choice = input("Enter your choice: ")

            if choice == "1":
                self.add_student()

            elif choice == "2":
                self.view_students()

            elif choice == "3":
                self.search_student()

            elif choice == "4":
                self.update_student()

            elif choice == "5":
                self.delete_student()

            elif choice == "6":
                self.statistics()

            elif choice == "7":
                print("Thank you.")
                break

            else:
                print("Invalid choice.")


if __name__ == "__main__":
    sms = StudentManagementSystem()
    sms.run()
