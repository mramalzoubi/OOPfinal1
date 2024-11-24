# OOPfinal1
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
