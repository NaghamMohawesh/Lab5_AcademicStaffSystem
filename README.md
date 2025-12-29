using System;

namespace AcademicStaffSystem
{
    class Staff
    {
        public string Name { get; set; }
        public string Department { get; set; }
        public double BaseSalary { get; set; }

        public Staff(string name, string department, double baseSalary)
        {
            Name = name;
            Department = department;
            BaseSalary = baseSalary;
        }

        public virtual double CalculateSalary()
        {
            return BaseSalary;
        }
    }

    class Lecturer : Staff
    {
        public Lecturer(string name, string department, double baseSalary)
            : base(name, department, baseSalary) { }

        public override double CalculateSalary()
        {
            return BaseSalary * 1.2;
        }
    }

    class Administrator : Staff
    {
        public Administrator(string name, string department, double baseSalary)
            : base(name, department, baseSalary) { }

        public override double CalculateSalary()
        {
            return BaseSalary + 300;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Staff lecturer1 = new Lecturer("Ayman", "CS", 1000);
            Staff lecturer2 = new Lecturer("Ihab", "SE", 1200);
            Staff admin1 = new Administrator("Yasser", "IT", 900);
            Staff admin2 = new Administrator("Alice", "HR", 950);

            PrintStaff(lecturer1);
            PrintStaff(lecturer2);
            PrintStaff(admin1);
            PrintStaff(admin2);
        }

        static void PrintStaff(Staff s)
        {
            Console.WriteLine($"{s.Name} ({s.Department}) => Total Salary: {s.CalculateSalary()}");
        }
    }
}
