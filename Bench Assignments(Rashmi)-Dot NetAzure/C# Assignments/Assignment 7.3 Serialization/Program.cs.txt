using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Runtime.Serialization.Formatters.Binary;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_7._3_Serialization
{
    internal class Program
    {
        static void Main(string[] args)
        {

            Manager e2 = new Manager("Ramesh", 50000);
            e2.salarycalculation();

            /***** Serialzation *****/

            string path = @"C:\Users\PULATE\source\repos\C# Assigmnets\EmployeeInfo.txt";


            FileStream stream = new FileStream(path, FileMode.OpenOrCreate);

            BinaryFormatter formater = new BinaryFormatter();

            formater.Serialize(stream, e2);

            stream.Close();

            Console.WriteLine("File saved in " + path);



            /***** Deserialzation *****/
            string path2 = @"C:\Users\PULATE\source\repos\C# Assigmnets\EmployeeInfo.txt";

            FileStream stream2 = new FileStream(path2, FileMode.OpenOrCreate);

            BinaryFormatter formater2 = new BinaryFormatter();

            Manager e3 = (Manager)formater2.Deserialize(stream2);

            

            Console.WriteLine("\nId :" + e3.Id);

            Console.WriteLine("Name :" + e3.Name);

           
        }
    }
}
