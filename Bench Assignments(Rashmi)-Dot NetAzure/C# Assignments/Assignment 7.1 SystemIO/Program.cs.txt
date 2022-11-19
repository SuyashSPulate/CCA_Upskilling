using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_7._1_SystemIO
{
    internal class Program
    {
        static void Main(string[] args)
        {
                       
            /***** Create Directory *****/
            DirectoryInfo dataDir = new DirectoryInfo(@"C:\Users\PULATE\source\repos\C# Assigmnets\Test");
            dataDir.Create();

            /***** Create read and write file *****/
            Console.WriteLine("Enter number of lines you want to write");
            int q = Convert.ToInt32(Console.ReadLine());
            string[] data = new string[q];
            Console.WriteLine("\nEnter Data");
            for (int i = 0; i < q; i++)
            {
                data[i] = Console.ReadLine();
            }

            string textFilePath = @"C:\Users\PULATE\source\repos\C# Assigmnets\SystemIO.txt";

            File.WriteAllLines(textFilePath,data);

            string text = System.IO.File.ReadAllText(@textFilePath);

            System.Console.WriteLine("\nContents of SystemIO.txt = \n{0}", text);

            /***** Get File Description *****/
            DirectoryInfo dereksDir = new DirectoryInfo(@"C:\Users\PULATE\source\repos\C# Assigmnets\SystemIO");
            Console.WriteLine("\nInformation about file is-");
            Console.WriteLine(dereksDir.FullName);
            Console.WriteLine(dereksDir.Name);
            Console.WriteLine(dereksDir.Parent);
            Console.WriteLine(dereksDir.Attributes);
            Console.WriteLine(dereksDir.CreationTime);


            /***** Get Directories in the folder *****/
            Console.WriteLine("\n\nDirectory present in the current folder are-");
            string rootPath = @"C:\Users\PULATE\source\repos\C# Assigmnets";
            string[] dirs = Directory.GetDirectories(rootPath, "*", SearchOption.TopDirectoryOnly);

            foreach (string dir in dirs)
            {
                Console.WriteLine(dir);
            }
            Console.ReadLine();

        }
    }
}
