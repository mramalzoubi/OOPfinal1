# OOPfinal1
# Exercise 1

// See https://aka.ms/new-console-template for more information
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;

class GenericList<T>
{
    private List<T> items = new List<T>();

    public void AddElement(T element)
    {
        items.Add(element);
    }

    public void DisplayFirstElement()
    {
        if (items.Count > 0)
        {
            Console.WriteLine($"First element: {items[0]}");
        }
        else
        {
            Console.WriteLine("The list is empty.");
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        GenericList<int> intList = new GenericList<int>();
        intList.AddElement(10);
        intList.AddElement(20);
        intList.DisplayFirstElement();

        GenericList<string> stringList = new GenericList<string>();
        stringList.AddElement("Hello");
        stringList.AddElement("World");
        stringList.DisplayFirstElement();
    }
}
///////////////////////////////////////////////////////////////////////////
# OOPfinal2
# Exercise 2
using System;
using System.IO;
using System.Linq;

class Program
{
    static void Main(string[] args)
    {
        string file1 = "Text1.txt";
        string file2 = "Text2.txt";

        if (File.Exists(file1) && File.Exists(file2))
        {
            string content1 = File.ReadAllText(file1);

            string content2 = File.ReadAllText(file2);

            string mergedContent = content2 + " " + content1;
            File.WriteAllText(file2, mergedContent);

      
            int wordCount = mergedContent.Split(new[] { ' ', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Count();
            Console.WriteLine($"Total number of words in {file2}: {wordCount}");
        }
        else
        {
            Console.WriteLine("One or both files do not exist.");
        }
    }
}

///////////////////////////////////////////////////////////////////////////
# oopfinal3
# Exercise 3
using System;
using System.Collections.Generic;
using System.Linq;

class City
{
    public string CityName { get; set; }
    public string CityRegion { get; set; }
    public List<School> Schools { get; set; } = new List<School>();
}

class School
{
    public string SchoolName { get; set; }
    public double Space { get; set; }
    public List<Teacher> Teachers { get; set; } = new List<Teacher>();
}

class Teacher
{
    public string TeacherName { get; set; }
    public int TeacherId { get; set; }
}

class Program
{
    static void Main(string[] args)
    {
       
        var city = new City
        {
            CityName = "Amman",
            CityRegion = "Middel",
            Schools = new List<School>
            {
                new School
                {
                    SchoolName = "High School A",
                    Space = 500.5,
                    Teachers = new List<Teacher>
                    {
                        new Teacher { TeacherName = "Mram", TeacherId = 1 },
                        new Teacher { TeacherName = "Manar", TeacherId = 2 }
                    }
                },
                new School
                {
                    SchoolName = "High School B",
                    Space = 300.0,
                    Teachers = new List<Teacher>
                    {
                        new Teacher { TeacherName = "Sarah", TeacherId = 3 }
                    }
                }
            }
        };

        Console.WriteLine($"City: {city.CityName}, Region: {city.CityRegion}");
        foreach (var school in city.Schools)
        {
            Console.WriteLine($"School: {school.SchoolName}, Space: {school.Space}");
            foreach (var teacher in school.Teachers)
            {
                Console.WriteLine($" - Teacher: {teacher.TeacherName}, ID: {teacher.TeacherId}");
            }
        }

        var topSchool = city.Schools.OrderByDescending(s => s.Teachers.Count).First();
        Console.WriteLine($"\nSchool with the highest number of teachers: {topSchool.SchoolName} ({topSchool.Teachers.Count} teachers)");
    }
}


