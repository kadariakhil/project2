 namespace ProjectBank

    {
        class Account
        {
            private double balance = 100000;


            public double bal
            {
                get { return balance; }
                set { balance = value; }
            }
            public string name;
            public double account, final_Amt;
            public double withdraw, dep, total;

            public void credit()
            {
                Console.WriteLine("Enter Name of the depositor :");
                name = Console.ReadLine();
                Console.WriteLine("Enter Account Number  :");
                account = Convert.ToInt32(Console.ReadLine());
                Console.WriteLine("Enter Credit Amount :");
                dep = Convert.ToDouble(Console.ReadLine());
                total = bal + dep;

                Console.WriteLine("------------------------------\n");
                Console.WriteLine("Name of the depositor : " + name);
                Console.WriteLine("Account Number: " + account);
                Console.WriteLine("Total Balance amount in the account  : " + total);

            }
            public void debit()
            {
                Console.WriteLine("Enter Account Name :");
                name = Console.ReadLine();
                Console.WriteLine("Enter Account Number  :");
                account = Convert.ToInt32(Console.ReadLine());
                Console.WriteLine("Enter Withdraw Amount :");
                withdraw = Convert.ToDouble(Console.ReadLine());
                if (withdraw <= bal)
                {
                    total = bal - withdraw;
                    Console.WriteLine("------------------------------\n");
                    Console.WriteLine("Account Name : " + name);
                    Console.WriteLine("Account Number: " + account);
                    Console.WriteLine("After Withdraw balnace Amount is : " + total);
                }
                else
                    Console.WriteLine("\n\nWithdraw Amount does not Exist your Account.");
            }

        }
        class Saving_Account : Account
        {
            double interest_rate, rate;
            public void calculateintrest()
            {
                interest_rate = 0.02;
               
                rate = total * (interest_rate / 100);
                final_Amt = total + rate;
                Console.WriteLine("Total Balance Amount with Interest : " + final_Amt);
            }

        }
        class CheckingAccount : Saving_Account
        {
            double fee_per = 15;
            public void fee()
            {
                Console.WriteLine("Balance After Transection Charges : " + (total - fee_per));
            }

        }
        class Program
        {
            static void Main(string[] args)
            {
                string agn;
                do
                {
                    CheckingAccount i = new CheckingAccount();
                    int num;
                    Console.WriteLine("Please Select Any Function.");
                    Console.WriteLine("\nPress 1 for Credit an Amount. \nPress 2 for debit an Amount.");
                    num = Convert.ToInt32(Console.ReadLine());
                    switch (num)
                    {
                        case 1:
                            i.credit();
                            i.calculateintrest();
                            break;
                        case 2:
                            i.debit();
                            i.fee();
                            break;
                        default:
                            Console.WriteLine("Invalid Selection!!!");
                            break;
                    }
                    Console.WriteLine("\nDo you want to continue this program? (yes/no)");
                    agn = Console.ReadLine();

                } while (agn == "yes");
                Console.ReadKey();
            }
        }
    }
}
