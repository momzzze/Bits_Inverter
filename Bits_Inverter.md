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
            int count = 0, count2 = 7;
            List<int> New = new List<int>();
            List<int> Combination = new List<int>();
            List<int> Numbers = new List<int>();
            List<int> Boring = new List<int>();
            List<int> SeparatingTheList = new List<int>();
            List<int> SeparatingInOneList = new List<int>();
            for (int i = 0; i < Howmanynumber; i++)
			{
			 number=int.Parse(Console.ReadLine());
             Numbers.Add(number);
            
			}
            
            for (int i = 0; i < Numbers.Count; i++)
            {
                int[] array = ConvertToBinary(Numbers[i]);
                New = ConvertArryaToList(array);
                Combination.AddRange(New);
                

            }
            
            Boring = Inverte(Combination, step);
            
            for (int i = count; i < Boring.Count; i++)
            {
                while (count2 < Boring.Count)
                {
                    SeparatingInOneList=SeparatedList(SeparatingTheList, count, count2, Boring);
                    SeparatingInOneList.Reverse();
                    ConvertToDecimal(SeparatingInOneList);
                    count += 8;
                    count2 = count + 7;
                }
                
            }
        
        
        }
        static int[] ConvertToBinary(int numb)
        {
            int newnumb = 0;
            int[] zero = new int[] { 0, 0, 0, 0, 0, 0, 0, 0, };
            int[] m = new int[zero.Length];
            for (int i = 0; i < zero.Length ; i++)
            {

                newnumb = numb % 2;
                m[i] = newnumb;
                numb = numb / 2;

            }
            Array.Reverse(m);
            return m;
        }
        static List<int> ConvertArryaToList(int[] m)
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
        static List<int> SeparatedList(List<int> ojas,int count,int count2,List<int> Boring)
        {
            List<int> Separated = new List<int>();
            for (int i = count; i < Boring.Count; i++)
            {
                Separated.Add(Boring[i]);
                if (i == count2)
                {
                    
                    break;
                }

            } return Separated;
        }
        static void ConvertToDecimal(List<int> SeparatingInOneList)
        {
            int number=0;
            int sum=0;
           for (int i = 0; i<SeparatingInOneList.Count; i++)       
            {
                if (SeparatingInOneList[i] != 0)
                {
                    number = Grade(SeparatingInOneList[i] * 2, i);
                }
                else
                {
                    number = 0;
                }
                sum += number;
            }
            Console.WriteLine(sum);
            
        }
        static int Grade(int n, int grades)
        {
            int counter = 1;
            for (int i = 1; i <= grades; i++)
            {

                counter *= n;
            }
            return counter;
        }
        
       
    }
}
