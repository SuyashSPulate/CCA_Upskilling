using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_6._3_Application_for_banking_domain
{
    public delegate void displaymsg();
    internal class Program
    {
        static void errormsg()
        {
            Console.WriteLine("\nTransaction cannot be continued as balance is zero in Account\n");
        }
        static void errormsg2()
        {
            Console.WriteLine("\nTransaction cannot be continued as balance is insufficient in Account\n");
        }
        static void Main(string[] args)
        {

            int q;
            Account[] acc1 = new Account[5];
            acc1[0] = new Account(12345, "Ramesh", 0);
            acc1[1] = new Account(54895, "Mahesh", 50000);
            acc1[2] = new Account(78146, "Suresh", 670000);
            acc1[3] = new Account(36478, "Mukesh", 1000000);
            acc1[4] = new Account(19785, "Rakesh", 5000);
            do
            {
                Console.WriteLine("Select to perform\n1.Withdraw amount\n2.Deposit\n3.exit\n");
                q = Convert.ToInt32(Console.ReadLine());

                switch (q)
                {
                    case 1:
                        int count=0;
                        Console.WriteLine("Enter account number\n");
                        int temp = Convert.ToInt32(Console.ReadLine());
                        for (int i = 0; i < 5; i++)
                        {
                            if (acc1[i].account_number == temp)
                            {
                                Console.WriteLine("Enter Amount to be withdrawn\n");
                                double temp2 = Convert.ToDouble(Console.ReadLine());
                                
                                acc1[i].BalanceZero += new displaymsg(errormsg);
                                acc1[i].UnderBalance += new displaymsg(errormsg2);
                                acc1[i].validate(temp2);
                                count = 1;
                            }
                            
                        }
                        if(count== 0)
                        Console.WriteLine("\nWrong number");
                        break;

                    case 2:
                        Console.WriteLine("Enter account number\n");
                        int temp3 = Convert.ToInt32(Console.ReadLine());
                        for (int i = 0; i < 5; i++)
                        {
                            if (acc1[i].account_number == temp3)
                            {
                                Console.WriteLine("Enter Amount to be Deposited\n");
                                double temp2 = Convert.ToDouble(Console.ReadLine());
                                acc1[i].Deposit(temp2);
                               
                            }
                        }
                        break;

                    case 3:
                        break;

                     default:
                        Console.WriteLine("\nInvalid!!!!!\n");
                        break;


                }
            }
            while (q != 3);
        }
    }
}
