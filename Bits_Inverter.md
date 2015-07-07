using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


namespace Bits_Inverter
{
    class BitsInverter
    {
        
        static void Main()
        {
            int Howmanynumber=int.Parse(Console.ReadLine());
            int step=int.Parse(Console.ReadLine());
            int number=0;
            List<int> New = new List<int>();
            List<int> Combination = new List<int>();
            List<int> Numbers = new List<int>();
            List<int> Boring = new List<int>();
            for (int i = 0; i < Howmanynumber; i++)
			{
			 number=int.Parse(Console.ReadLine());
             Numbers.Add(number);
            
			}
            Console.WriteLine(string.Join(",",Numbers));
            for (int i = 0; i < Numbers.Count; i++)
            {
                int[] array = ConvertToBinary(Numbers[i]);
                New = ConvertAndAddArryaToList(array);
                Combination.AddRange(New);

            }
            Console.WriteLine(string.Join(",", Combination));
            Boring=Inverte(Combination,step);
            Console.WriteLine(string.Join(",", Boring));
        
        
        }
        static int[] ConvertToBinary(int numb)
        {
            int newnumb = 0;
            int[] zero = new int[] { 0, 0, 0, 0, 0, 0, 0, 0, };
            int[] m = new int[zero.Length];
            for (int i = 0; i < zero.Length - 1; i++)
            {

                newnumb = numb % 2;
                m[i] = newnumb;
                numb = numb / 2;

            }
            Array.Reverse(m);
            return m;
        }
        static List<int> ConvertAndAddArryaToList(int[] m)
        {
            List<int> New = new List<int>();
            for (int i = 0; i < m.Length ; i++)
            {
                New.Add(m[i]);
            }
            return New;
        }
        static List<int> Inverte(List<int> Combination,int step)
        {
                        
            for (int i = 0; i < Combination.Count; i+=step)
            {
                if (Combination[i] == 0)
                {
                    Combination[i] = 1;
                }
                else if (Combination[i] == 1)
                {
                    Combination[i] = 0;
                } 
            }
            return Combination;
        }

    }
}

