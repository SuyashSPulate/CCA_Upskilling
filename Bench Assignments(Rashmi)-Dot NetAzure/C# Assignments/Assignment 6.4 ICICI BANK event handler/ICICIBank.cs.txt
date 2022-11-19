using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment_6._4_ICICI_BANK_event_handler
{
    internal class ICICIBank
    {
        public event displaymsg UnderBalance;
        public event displaymsg BalanceZero;

        public int ICICIBank_number;
        public string customer_name;
        public double balance;


        public ICICIBank(int accno, string name, double bal)
        {
            ICICIBank_number = accno;
            customer_name = name;
            balance = bal;
        }

        public void validate(double amt)
        {

            if (balance == 0)
            {
                BalanceZero();
            }
            else if (balance < amt)
            {
                UnderBalance();
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
