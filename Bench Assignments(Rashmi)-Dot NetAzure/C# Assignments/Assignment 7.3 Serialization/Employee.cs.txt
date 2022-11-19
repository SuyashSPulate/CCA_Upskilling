using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_7._3_Serialization
{
    [Serializable]
    internal class Employee
    {
        protected static int count;
        public int Id;
        public string Name;
        public double NetSalary, Pf, GrossSalary, BasicSalary;
        public Employee()
        {
            count++;
            Id = count;
            Name = "unknown";
            BasicSalary = 00;
        }

        public Employee(string name, double basicsalary)
        {
            count++;
            this.Id = count;
            this.Name = name;
            this.BasicSalary = basicsalary;
        }
        public virtual void salarycalculation()
        {

            Pf = BasicSalary * 0.10;
            GrossSalary = BasicSalary;
            NetSalary = GrossSalary - Pf;

        }

        public void Display()
        {
            Console.WriteLine("\n\nEmplyee Id : " + Id + "\nEmployee Name : " + Name +
                "\nGrossSalary : " + GrossSalary + "\nNetSalary : " + NetSalary);
        }
    }
}
