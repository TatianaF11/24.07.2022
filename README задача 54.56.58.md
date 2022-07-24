/Задача 54: Задайте двумерный массив. Напишите программу, которая упорядочит по убыванию элементы каждой 
//строки двумерного массива.
//Например, задан массив:
//1 4 7 2
//5 9 2 3
//8 4 2 4
//В итоге получается вот такой массив:
//7 2 4 1
//9 5 3 2
//8 4 4 2
//void Zadacha54()
{
    Random random = new Random();
    int rows = random.Next(2, 5);
    int columns = random.Next(3, 6);
    int[,] array = new int[rows, columns];
    CreateIntArray(array);
    PrintArray(array);
    Console.WriteLine("Отсортированный массив");
    SortedArray(array);
    PrintArray(array);
}

int[,] CreateIntArray(int[,] arr)
{
    Random random = new Random();
    int rows = arr.GetLength(0);
    int columns = arr.GetLength(1);
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            arr[i, j] = random.Next(1,10);
        }
    }
    return arr;
}

int[,] PrintArray(int[,] arr)
{
    int rows = arr.GetLength(0);
    int columns = arr.GetLength(1);
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            Console.Write($"{arr[i, j]} ");
        }
    Console.WriteLine();
    }

    return arr;
}

int[,] SortedArray(int[,] arr)
{
    int rows = arr.GetLength(0);
    int columns = arr.GetLength(1);
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns - 1; j++)
        {
            for (int k = 0; k < columns - 1; k++)
            {
                if (arr[i, k] > arr[i, k + 1])
                {
                    (arr[i, k], arr[i, k + 1]) = (arr[i, k + 1], arr[i, k]);
                }
            }
        }
    }
    return arr;
}
//Zadacha54();

Задача 56: Задайте прямоугольный двумерный массив. Напишите программу,
//которая будет находить строку с наименьшей суммой элементов.
// Например, задан массив:
// 1 4 7 2
// 5 9 2 3
// 8 4 2 4
// 5 2 6 7
// Программа считает сумму элементов в каждой строке и выдаёт номер строки с наименьшей
//  суммой элементов: 1 строка
//void Zadacha56()
{
    Random random = new Random();
    int rows = random.Next(3, 5);
    int columns = random.Next(5, 7);
    int[,] array = new int[rows, columns];
    CreateArray(array);
    Console.WriteLine("Двумерный массив:");
    PrintArray(array);
    FillMinSum(array);
    Console.WriteLine("Массив из сумм строк:");
    PrintArrayOnes(FillMinSum(array));
    Console.WriteLine();
    Console.WriteLine("Минимальная сумма строки:");
    int min = MinSum(FillMinSum(array));
    Console.WriteLine(min);
}
int[,] CreateArray(int[,] arr)
{
    Random random = new Random();
    int rows = arr.GetLength(0);
    int columns = arr.GetLength(1);
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            arr[i, j] = random.Next(1,10);
        }
    }
    return arr;
}

int[] PrintArrayOnes(int[] arr)
{
    for (int i = 0; i < arr.Length; i++)
    {
        Console.Write(arr[i] + "\t");
    }
    return arr;
}

int[] FillMinSum(int[,] arr)
{
    int rows = arr.GetLength(0);
    int columns = arr.GetLength(1);
    int[] array = new int[rows];
    int index = 0;
    int sum = 0;
    for (int i = 0; i < rows; i++)
    {
        sum = 0;
        for (int j = 0; j < columns; j++)
        {
            sum += arr[i, j];
        }
        array[index] = sum;
        index++;
    }
    return array;
}

int MinSum(int[] arr)
{
    int min = arr[0];
    for (int i = 0; i < arr.Length; i++)
    {
        if (arr[i] < min)
        {
            min = arr[i];
        }
    }
    return min;
}
//Zadacha56();

/Задача 58. Заполните спирально массив 4 на 4.
// Например, на выходе получается вот такой массив:
// 1  2  3  4
// 12 13 14 5
// 11 16 15 6
// 10  9  8  7
Random random = new Random();
int[,] array = new int[4, 4];
Console.WriteLine("Двумерный массив:");
FillArraySpiral(array);
PrintArray(array);
}
int[,] FillArraySpiral(int[,] array)
{
    int rows = array.GetLength(0);
    int columns = array.GetLength(1);
    for (int i = 0; i < rows; i++)
    {
        int index1 = 1;
        for (int j = 0; j < columns; j++)
        {
            if (i == 0) array[i, j] = index1;
            index1++;
        }
    }
    for (int i = rows; i >= 0; i--)
    {
        int index2 = 6;
        for (int j = columns; j >= 0; j--)
        {
            if (j <= columns - 1 && i == rows - 1) array[i, j] = index2;
            index2++;
        }

    }
    for (int i = rows - 1; i >= 0; i--)
    {
        int index4 = 10;
        for (int j = columns - 1; j >= 0; j--)
        {
            if (j != 0 && i == rows - 4 && j != columns - 1) array[j, i] = index4;
             index4++;
        }
    }

    for (int i = 0; i < rows; i++)
    {
        int index3 = 4;
        for (int j = 0; j < columns; j++)
        {
            if (i == rows - 1 && j <= columns - 1) array[j, i] = index3;
            index3++;
        }
    }
    for (int i = 0; i < rows; i++)
    {
        int index5 = 12;
        for (int j = 0; j < columns; j++)
        {
            if (i == 1 && j != 0 && j != columns - 1) array[i, j] = index5;
             index5++;
        }
    }
    for (int i = rows; i >= 0; i--)
    {
        int index6 = 13;
        for (int j = columns; j >= 0; j--)
        {
            if (j!= 0&&j <= columns - 2 && i == rows - 2) array[i, j] = index6;
            index6++;
        }
    }
    return array;
}
Zadacha58();
