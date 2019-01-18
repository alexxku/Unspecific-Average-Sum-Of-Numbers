# Unspecific-Average-Sum-Of-Numbers
Using C# console application, the program will accept a number test scores (as calculated by the number of scores actually entered) and average them.

using System;


namespace NonSpecificSumofNumAverage
{

    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter scores from 0 to 100. Enter q at anytime to exit. ");
            //Call method
            continousAverage();
            Console.WriteLine("\nGrades have been update.");
            Console.ReadLine();
        }

        //Add values 
        static void continousAverage()
        {
            //Variables declaration and assignment for sumValue()
            string num;
            int count = 0;
            double sum;
            double average;
            double total = 0;

            //Repeat value entry 10 times
            while(1==1)
            {
                //Test number increment
                count++;
                //Label reference
                Start:
                Console.Write($"\nTest Score {count}: ");
                //Exception handler. Going to try the following block of code.
                try
                {
                    num = Console.ReadLine();

                    //If num is equal to q...break the while loop
                    if (num == "q")
                    {
                        break;
                    }
                    //Convert string into number
                    sum = Convert.ToDouble(num);
                    //Sum assignment with user input and sum arguements.
                    sum = repeatV(sum, count);
                    //If sum by passes condition...break the while loop
                    if (sum < 0 || sum > 100)
                    {
                        break;
                    }
                    //total assignment with increasing input sum for every loop
                    total += sum;
                }
                //Catches error
                catch (Exception error)
                {
                    Console.WriteLine($"\n{error.Message.ToString()}");

                    //Goes to reference label
                    goto Start;
                }
                //Calculates average with total and increment count
                average = Math.Round((total / count),1);
                Console.WriteLine($"\nTotal Score Average: {average}");
                //Calls the letterGrade conditions
                letterGrade(average);
            }
        }

        //Looping negative and large numbers with two parameters for sum and count
        static double repeatV(double x, int y)
        {
            string z;
            //Loop conditions
            while (x < 0 || x > 100)
            {
                Console.WriteLine("\nInvalid Score.");
                Console.Write($"\nTest Score {y}: ");
                z = Console.ReadLine();
                //If z is equal to z...break the while loop
                if (z == "q")
                {
                    break;
                }
                //Converts string into a double
                x = Convert.ToDouble(z);
            }

            //Return x...NOTE: Large or negative numbers are by passed when loop breaks
            return x;
        }

        //Conditions for letter grade
        static void letterGrade(double average)
        {
            if (average < 60)
            {
                Console.WriteLine("\nGrade: F");
            }
            else if (average < 70)
            {
                Console.WriteLine("\nGrade: D");
            }
            else if (average < 80)
            {
                Console.WriteLine("\nGrade: C");
            }
            else if (average < 90)
            {
                Console.WriteLine("\nGrade: B");
            }
            else if (average <= 100)
            {
                Console.WriteLine("\nGrade: A");
            }

        }

    }
}
