using System;

class Program
{
    static void Main()
    {
        int[] grades = { 75, 60, 78, 90, 77,
                         90, 82, 89, 82, 97,
                         90, 91, 78, 81, 88 };

        Console.WriteLine("Grades:");
        DisplayGrades(grades);

        Console.WriteLine("\nGrade for Each Student:");
        DisplayStudentAverages(grades);

        Console.WriteLine("\nHighest Grade for Each Subject:");
        DisplayHighestGrades(grades);

        Console.WriteLine("\nHonor Students:");
        DisplayHonorStudents(grades);
    }

    static void DisplayGrades(int[] grades)
    {
        for (int i = 0; i < grades.Length; i++)
        {
            Console.Write(grades[i] + " ");
            if ((i + 1) % 3 == 0) Console.WriteLine();
        }
    }

    static void DisplayStudentAverages(int[] grades)
    {
        for (int i = 0; i < grades.Length; i += 3)
        {
            int sum = grades[i] + grades[i + 1] + grades[i + 2];
            int average = sum / 3;
            double norsuGrade = ConvertToNorsuGrade(average);
            string status = (norsuGrade <= 3.0) ? "Passed" : "Failed";
            Console.WriteLine($"Student {(i / 3) + 1}: Average = {average}, NORSU Grade = {norsuGrade}, Status: {status}");
        }
    }

    static void DisplayHighestGrades(int[] grades)
    {
        for (int j = 0; j < 3; j++)
        {
            int highest = grades[j];
            for (int i = j; i < grades.Length; i += 3)
            {
                if (grades[i] > highest) highest = grades[i];
            }
            Console.WriteLine($"Subject {j + 1}: {highest}");
        }
    }

    static void DisplayHonorStudents(int[] grades)
    {
        for (int i = 0; i < grades.Length; i += 3)
        {
            int sum = grades[i] + grades[i + 1] + grades[i + 2];
            int average = sum / 3;
            double norsuGrade = ConvertToNorsuGrade(average);
            if (norsuGrade <= 1.75)
            {
                Console.WriteLine($"Student {(i / 3) + 1}: Average = {average}, NORSU Grade = {norsuGrade}, Status: Honor Student");
            }
        }
    }

    static double ConvertToNorsuGrade(int grade)
    {
        if (grade >= 96) return 1.0;
        if (grade >= 93) return 1.25;
        if (grade >= 90) return 1.5;
        if (grade >= 87) return 1.75;
        if (grade >= 84) return 2.0;
        if (grade >= 81) return 2.25;
        if (grade >= 78) return 2.5;
        if (grade >= 75) return 2.75;
        return 5.0;
    }
}
