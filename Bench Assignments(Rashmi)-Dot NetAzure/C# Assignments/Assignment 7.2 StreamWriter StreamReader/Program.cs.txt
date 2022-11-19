using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_7._2_StreamWriter_StreamReader
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Account[] acc1 = new Account[5];
            acc1[0] = new Account(12345, "Ramesh", 0);
            acc1[1] = new Account(54895, "Mahesh", 50000);
            acc1[2] = new Account(78146, "Suresh", 670000);
            acc1[3] = new Account(36478, "Mukesh", 1000000);
            acc1[4] = new Account(19785, "Rakesh", 5000);

            string Path = @"C:\Users\PULATE\source\repos\C# Assigmnets\AccountData.txt";

            
            StreamWriter sw = File.CreateText(Path);

            for (int i = 0; i < acc1.Length; i++)
            {

                sw.WriteLine(acc1[i].account_number);
                sw.WriteLine(acc1[i].customer_name);
                sw.WriteLine(acc1[i].balance);
                sw.WriteLine("\n");
            }
            sw.WriteLine("\n");

           
            sw.Close();

         
            StreamReader sr = File.OpenText(Path);

            Console.WriteLine("All the account data : \n{0}",sr.ReadToEnd());

            sr.Close();
        }
    }
}
