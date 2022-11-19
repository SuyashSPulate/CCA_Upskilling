using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_6._5_HDFCBank_EventHandler
{
    internal class HDFCBank
    {
        public event displaymsg UnderBalance;
        public event displaymsg BalanceZero;
        public event displaymsg LimitReached;

        public int HDFCBank_number;
        public string customer_name;
        public double balance;


        public HDFCBank(int accno, string name, double bal)
        {
            HDFCBank_number = accno;
            customer_name = name;
            balance = bal;
        }

        public void validate(double amt)
        {
            double temp = balance - amt;
            if (balance == 0)
            {
                BalanceZero();
            }
            else if (balance < amt)
            {
                UnderBalance();
            }
            else if(temp<=1000)
            {
                LimitReached();
            }
            else
            {
                Withdraw(amt);
            }
        }
        public void Withdraw(double val)
        {
            balance = balance - val;
            Console.WriteLine("\nAmount withdrawn is :" + val + "\nCurrent balance is :" + balance + "\n");
        }
        public void Deposit(double val)
        {
            balance = balance + val;
            Console.WriteLine("\nAmount deposited is :" + val + "\nCurrent balance is :" + balance + "\n");
        }
    }
}
