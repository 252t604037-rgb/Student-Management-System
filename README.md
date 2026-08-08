# ==========================================
#       STUDENT MANAGEMENT SYSTEM
# ==========================================

students = []


# ------------------------------------------
# Add Student
# ------------------------------------------
def add_student():
    print("\n========== ADD STUDENT ==========")

    student_id = input("Enter Student ID: ")

    # Check duplicate ID
    for student in students:
        if student["id"] == student_id:
            print("Student ID already exists!")
            return

    name = input("Enter Student Name: ")
    age = int(input("Enter Age: "))
    branch = input("Enter Branch: ")
    year = input("Enter Year: ")

    student = {
        "id": student_id,
        "name": name,
        "age": age,
        "branch": branch,
        "year": year,
        "marks": 0,
        "grade": "Not Assigned"
    }

    students.append(student)

    print("\nStudent added successfully!")


# ------------------------------------------
# Display Students
# ------------------------------------------
def display_students():
    print("\n========== STUDENT LIST ==========")

    if len(students) == 0:
        print("No students available.")
        return

    for student in students:
        print("----------------------------------")
        print("Student ID :", student["id"])
        print("Name       :", student["name"])
        print("Age        :", student["age"])
        print("Branch     :", student["branch"])
        print("Year       :", student["year"])
        print("Marks      :", student["marks"])
        print("Grade      :", student["grade"])

    print("----------------------------------")


# ------------------------------------------
# Search Student
# ------------------------------------------
def search_student():
    print("\n========== SEARCH STUDENT ==========")

    student_id = input("Enter Student ID: ")

    for student in students:
        if student["id"] == student_id:
            print("\nStudent Found!")
            print("----------------------------------")
            print("Student ID :", student["id"])
            print("Name       :", student["name"])
            print("Age        :", student["age"])
            print("Branch     :", student["branch"])
            print("Year       :", student["year"])
            print("Marks      :", student["marks"])
            print("Grade      :", student["grade"])
            print("----------------------------------")
            return

    print("Student not found!")


# ------------------------------------------
# Update Student
# ------------------------------------------
def update_student():
    print("\n========== UPDATE STUDENT ==========")

    student_id = input("Enter Student ID: ")

    for student in students:
        if student["id"] == student_id:

            print("\nEnter new details:")

            student["name"] = input("Enter Name: ")
            student["age"] = int(input("Enter Age: "))
            student["branch"] = input("Enter Branch: ")
            student["year"] = input("Enter Year: ")

            print("\nStudent details updated successfully!")
            return

    print("Student not found!")


# ------------------------------------------
# Delete Student
# ------------------------------------------
def delete_student():
    print("\n========== DELETE STUDENT ==========")

    student_id = input("Enter Student ID: ")

    for student in students:
        if student["id"] == student_id:
            students.remove(student)
            print("\nStudent deleted successfully!")
            return

    print("Student not found!")


# ------------------------------------------
# Add / Update Marks
# ------------------------------------------
def update_marks():
    print("\n========== UPDATE MARKS ==========")

    student_id = input("Enter Student ID: ")

    for student in students:

        if student["id"] == student_id:

            marks = float(input("Enter Marks (0-100): "))

            if marks < 0 or marks > 100:
                print("Marks must be between 0 and 100.")
                return

            student["marks"] = marks

            # Calculate Grade
            if marks >= 90:
                student["grade"] = "A+"
            elif marks >= 80:
                student["grade"] = "A"
            elif marks >= 70:
                student["grade"] = "B"
            elif marks >= 60:
                student["grade"] = "C"
            elif marks >= 50:
                student["grade"] = "D"
            else:
                student["grade"] = "F"

            print("\nMarks updated successfully!")
            print("Grade:", student["grade"])
            return

    print("Student not found!")


# ------------------------------------------
# Display Top Student
# ------------------------------------------
def top_student():
    print("\n========== TOP STUDENT ==========")

    if len(students) == 0:
        print("No students available.")
        return

    student = max(students, key=lambda x: x["marks"])

    print("Student ID :", student["id"])
    print("Name       :", student["name"])
    print("Branch     :", student["branch"])
    print("Marks      :", student["marks"])
    print("Grade      :", student["grade"])


# ------------------------------------------
# Main Menu
# ------------------------------------------
def main():

    while True:

        print("\n")
        print("==========================================")
        print("       STUDENT MANAGEMENT SYSTEM")
        print("==========================================")
        print("1. Add Student")
        print("2. Display Students")
        print("3. Search Student")
        print("4. Update Student")
        print("5. Delete Student")
        print("6. Update Marks & Grade")
        print("7. Display Top Student")
        print("8. Exit")
        print("==========================================")

        choice = input("Enter your choice: ")

        if choice == "1":
            add_student()

        elif choice == "2":
            display_students()

        elif choice == "3":
            search_student()

        elif choice == "4":
            update_student()

        elif choice == "5":
            delete_student()

        elif choice == "6":
            update_marks()

        elif choice == "7":
            top_student()

        elif choice == "8":
            print("\nThank you for using Student Management System!")
            break

        else:
            print("\nInvalid choice. Please try again.")


# ------------------------------------------
# Program Starting Point
# ------------------------------------------
if __name__ == "__main__":
    main()
