# cgpa-calculator-
# Created by Floriane Djeigo
# This program calculates both Semester GPA and Cumulative GPA using student input.

def get_grade_point(letter):
    # Convert letter grades to GPA points
    grade_scale = {
        'A': 4.0,
        'B': 3.0,
        'C': 2.0,
        'D': 1.0,
        'F': 0.0
    }
    return grade_scale.get(letter.upper(), -1)


def calculate_gpa(courses):  # Fix: function name was misspelled
    total_points = 0  # Fix: no semicolon and no space in variable name
    total_credits = 0
    for course in courses:
        grade_point = get_grade_point(course['grade'])
        if grade_point == -1:
            print(f"Invalid grade '{course['grade']}' entered for {course['name']}. Skipping.")
            continue
        total_points += grade_point * course['credits']
        total_credits += course['credits']
    
    return round(total_points / total_credits, 2) if total_credits > 0 else 0.0  # Fix: misplaced characters and indentation


def input_courses():
    courses = []
    n = int(input("Enter number of courses: "))
    for i in range(n):
        print(f"Course {i+1}:")
        name = input("  Course name: ")
        grade = input("  Grade received (A/B/C/D/F): ")
        credits = int(input("  Credit hours: "))
        courses.append({'name': name, 'grade': grade, 'credits': credits})
    return courses


def main():
    print("==== CGPA Calculator ====")
    student_name = input("Enter your name: ")
    print(f"Welcome, {student_name}! Let's calculate your GPA.")

    courses = input_courses()
    gpa = calculate_gpa(courses)
    print(f"Hi {student_name}, your GPA for this semester is: {gpa}")


if __name__ == "__main__":
    main()
