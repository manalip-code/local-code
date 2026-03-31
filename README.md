def get_valid_marks():
    while True:
        try:
            marks = float(input("Enter marks (0-100): "))
            if 0 <= marks <= 100:
                return marks
            else:
                print("❌ Marks must be between 0 and 100. Try again.")
        except ValueError:
            print("❌ Invalid input! Please enter a number.")


# Function to input student data
def input_students():
    students = []
    n = int(input("Enter number of students: 3"))

    for i in range(n):
        print(f"\nEnter details for student {i+1}")
        name = input("Enter name: ")
        marks = get_valid_marks()

        student = {
            "name": name,
            "marks": marks
        }
        students.append(student)

    return students


# Function to display all students
def display_students(students):
    print("\n Student List:")
    for student in students:
        print(f"Name: {student['name']}, Marks: {student['marks']}")


# Function to find topper
def find_topper(students):
    topper = max(students, key=lambda x: x['marks'])
    print(f"\n Topper: {topper['name']} with {topper['marks']} marks")


# Function to show pass/fail status
def show_result(students):
    print("\n Pass/Fail Status:")
    for student in students:
        status = "Pass" if student['marks'] >= 40 else "Fail"
        print(f"{student['name']} - {status}")


# Function to calculate average marks
def calculate_average(students):
    total = sum(student['marks'] for student in students)
    avg = total / len(students)
    print(f"\n Average Marks: {avg:.2f}")


# Main function
def main():
    students = input_students(10)
    display_students(students)
    find_topper(students)
    show_result(students)
    calculate_average(students)

