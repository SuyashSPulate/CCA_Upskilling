using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_6._1_UniCast_Delegate
{
    delegate void EmployeeDelegate();
    internal class Program
    {
        static void Main(string[] args)
        {
           

            Employee e1 = new Employee("Suresh", 30000);
            EmployeeDelegate d1 = e1.Display;
            e1.salarycalculation();
            d1();

            Employee e2 = new Employee("Ramesh", 33000);
            EmployeeDelegate d2 = e2.Display;
            e2.salarycalculation();
            d2();

        }
    }
}
