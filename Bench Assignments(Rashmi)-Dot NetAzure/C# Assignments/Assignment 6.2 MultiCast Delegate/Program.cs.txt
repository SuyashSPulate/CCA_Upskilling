using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_5._2_MultiCast_Delegate
{
    delegate void EmployeeDelegate();
    internal class Program
    {
        static void Main(string[] args)
        {
            Employee e1 = new Employee("Suresh", 30000);
            e1.salarycalculation();
            
            Manager e2 = new Manager("Ramesh", 45000);
            e2.salarycalculation();

            MarketingExecutive e3 = new MarketingExecutive("Mahesh", 35000,90);
            e3.salarycalculation();

            // MULTICAST DELEGATE
            EmployeeDelegate d = new EmployeeDelegate(e1.Display);
            d += e2.Display;
            d += e3.Display;
            d();
        }
    }
}
