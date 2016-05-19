using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
namespace ConsoleMagicSquare
{
  class MagicSquare
{
static void Main(string[] args)
{
  //magic puzzle numbers square
  int num = int.Parse(Console.ReadLine());
  int[,] mat = new int[num,num];
  SolveMagicSquare(mat, num);
  if (test1(mat, num) == false) { Console.WriteLine("FAILED!!!");}
  else Console.WriteLine("SUCCESS!!!");
  //for printing the squre,but since you can 'input' large numbers   , you dont need this
  //for (int i = 0; i < mat.GetLength(0); i++)
 //{
   // for (int j = 0; j < mat.GetLength(1); j++)
   // {
      // Console.Write(mat[i, j]);
      // Console.Write(" ");
      // Console.Write(" ");
   // }
   // Console.WriteLine(" ");
   // Console.WriteLine(" ");
  //}
}
//****************************************************************
public static bool SolveMagicSquare(int[,] mat, int num)
{
  if (num <= 0)
  {
    return false;
  }
  for (int i = 0; i < mat.GetLength(0); i++)
  for (int j = 0; j < mat.GetLength(1); j++) mat[i, j] = 0;
//i = line , j= column
  mat[0, mat.GetLength(1) / 2] = 1;
  for (int i = 0, j = mat.GetLength(1) / 2, process = 2; process <    = num * num; process++)
  {
    if ((i - 1) > 0 && j + 1 < mat.GetLength(1) && mat[i - 1, j +          1] == 0)
    {
       i = i - 1; j = j + 1;
       mat[i, j] = process;
    }
    else if ((i - 1) > 0 && j + 1 < mat.GetLength(1) && mat[i - 1,               j + 1] != 0)
   {
      i = i + 1;
      mat[i, j] = process;
   }
   else if (i == 0 && j == num - 1)
   {
     i = 1; j = num - 1;
     mat[i, j] = process;
   }
   else
   {
     if ((i - 1) < 0 && j + 1 < mat.GetLength(1))
     {
        i = num - 1; j = j + 1;
        mat[i, j] = process;
     }
   else if ((j + 1) == mat.GetLength(1) && (i - 1) > 0 && (i - 1)              < mat.GetLength(0))
   {
      i = i - 1; j = 0;
      mat[i, j] = process;
   }
   else if ((j + 1) == mat.GetLength(1) && (i - 1) == 0)
   {
     i = 0; j = 0;
     mat[i, j] = process;
   }
   else if ((j + 1) == mat.GetLength(1) && (i - 1) < 0)
   {
      i = i - 1; j = 0;
      mat[i, j] = process;
   }
   else if (i - 1 < mat.GetLength(0) && j + 1 < mat.GetLength(1) &             &mat[i - 1, j + 1] != 0)
   {
       i = i + 1; mat[i, j] = process;
   }
   else if ((i - 1) == 0 && j + 1 < mat.GetLength(1) && mat[i - 1,              j +1] == 0)
   {
      i = i - 1; j = j + 1;
      mat[i, j ] = process;
   }
  }
}
 return true;
 }
//**************************************************************** //input: magic squre
 //output: if the fillings are correct(sum of lines= sum of column          s = sum of crossings) output=true => sucess, else=>fail.
 static bool test1(int[,] mat, int num)
 {
   int sum = 0;
   for (int i = 0; i < num; i++)
   {
     sum += mat[0, i];
   }
   int temp = 0;
   for (int i = 0; i < num; i++)
   {
      temp = 0;
      for (int j = 0; j < num;j++)
      {
        temp += mat[i, j];
      }
      if (temp != sum) return false;
   }
   temp = 0;
   for (int i = 0; i < num; i++)
   {
     temp = 0;
     for (int j = 0; j < num; j++)
   {
   temp += mat[j, i];
  }
  if (temp != sum) return false;
  }
 temp = 0;
 for (int i = 0; i < num; i++)
 {
    temp += mat[i, i];
 }
 if (temp != sum) return false;
 return true;
 }
 }
 }
