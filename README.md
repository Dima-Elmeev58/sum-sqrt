# sum-sqrt
internal class Program
{
    private static void Main(string[] args)
    {
        Random rand = new Random();
        Console.WriteLine("Введите количество элементов (до 10000):");

        if (!int.TryParse(Console.ReadLine(), out int n) || n < 1 || n > 10000)
        {
            Console.WriteLine("Количество элементов должно быть от 1 до 10000.");
            return;
        }

        int[] mass = new int[n];
        for (int i = 0; i < n; i++)
        {
            mass[i] = rand.Next(1, 101);
        }

        long maxSumOfSquares = 0; // Изменено на long для предотвращения переполнения
        for (int i = 0; i < n; i++)
        {
            for (int j = i + 10; j < n; j++)
            {
                long sum = (long)mass[i] * mass[i] + (long)mass[j] * mass[j]; // Преобразование в long для предотвращения переполнения

                if (sum > maxSumOfSquares)
                {
                    maxSumOfSquares = sum;
                }
            }
        }

        Console.WriteLine($"Максимальная сумма квадратов = {maxSumOfSquares}");
    }
}
