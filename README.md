# CodeAlpha_Student_Grade_Tracker

import java.util.ArrayList;
import java.util.Scanner;

public class StudentGradeTracker {
    private ArrayList<Double> grades;

    public StudentGradeTracker() {
        grades = new ArrayList<>();
    }

    public void addGrade(double grade) {
        grades.add(grade);
    }

    public double computeAverage() {
        double sum = 0;
        for (double grade : grades) {
            sum += grade;
        }
        return sum / grades.size();
    }

    public double getHighestGrade() {
        double highest = grades.get(0);
        for (double grade : grades) {
            if (grade > highest) {
                highest = grade;
            }
        }
        return highest;
    }

    public double getLowestGrade() {
        double lowest = grades.get(0);
        for (double grade : grades) {
            if (grade < lowest) {
                lowest = grade;
            }
        }
        return lowest;
    }

    public void displayGrades() {
        System.out.println("Grades:");
        for (double grade : grades) {
            System.out.println(grade);
        }
    }

    public static void main(String[] args) {
        StudentGradeTracker tracker = new StudentGradeTracker();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Enter a grade (or 'q' to quit):");
            String input = scanner.nextLine();
            if (input.equalsIgnoreCase("q")) {
                break;
            }
            try {
                double grade = Double.parseDouble(input);
                tracker.addGrade(grade);
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a number.");
            }
        }

        System.out.println("Average grade: " + tracker.computeAverage());
        System.out.println("Highest grade: " + tracker.getHighestGrade());
        System.out.println("Lowest grade: " + tracker.getLowestGrade());
        tracker.displayGrades();
    }
}
