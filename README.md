
## Authors

- [@DevJLeon](https://github.com/DevJLeon)







##
## Fibonacci Sequence
- [Repository](https://github.com/DevJLeon/FibonacciConsoleApp)


### CalcFibonacci Function

This function calculates the Fibonacci number at a given position 'k' in the Fibonacci sequence.

Input: An integer 'k' representing the position in the sequence.
Output: Returns the 'k'-th Fibonacci number.

How it Works:
For 'k' equal to 0 or 1, it directly returns 'k'.
For 'k' greater than 1, it recursively calculates the Fibonacci number at position 'k' by adding the numbers at positions 'k - 1' and 'k - 2'.

Handles negative inputs by returning -1, indicating an invalid input for the sequence.
This function employs recursion to efficiently find the desired Fibonacci number based on the given position 'k'.

```c♯
static int CalcFibonacci(int k)
    {
        if (k == 0 || k == 1)
        {
            return k;
        }
        else if (k >= 2)
        {
            return CalcFibonacci(k - 1) + CalcFibonacci(k - 2);
        }
        else
        {
            return -1;
        }
    }
```
### CalcIfFibo Function

Checks if a given number 'k' is a Fibonacci number.

Input: An integer 'k'.
Output: Returns true if 'k' is in the Fibonacci sequence; otherwise, returns false.

How it Works:
Iterates through the Fibonacci sequence using CalcFibonacci until it finds or surpasses 'k'.

If it discovers 'k' among the Fibonacci numbers, it returns true.

If 'k' isn't found in the sequence, it returns false.
This function quickly identifies whether a given number 'k' is a part of the Fibonacci sequence or not by searching the sequence up to 'k'.

```c♯
static bool CalcIfFibo(int k)
    {
        for (int n = 0; CalcFibonacci(n) <= k; n++)
        {
            if (CalcFibonacci(n) == k)
            {
                return true;
            }
        }
        return false;
    }
```
### Displaying Fibonacci Numbers
Generates and prints the first 'n' Fibonacci numbers.

- Input: User provides an integer 'n'.

- Output: Prints the initial 'n' Fibonacci numbers.

How it Works:

Takes user input 'n' for the count of numbers to display.
Iterates 'i' from 0 to 'n-1' and prints each Fibonacci number.
Displays the sequence in a space-separated format.

```c♯
Console.Write("Input n value: ");
    int y = Convert.ToInt32(Console.ReadLine());
    Console.Write($"The first {y} numbers of Fibonacci are: ");
    for (int i = 0; i < y; i++)
        {
            Console.Write($"{CalcFibonacci(i)} ");
        }
```

## 
## Russian Multiplication
- [Repository](https://github.com/DevJLeon/RussianMultiplication)

Performs multiplication using the Russian peasant algorithm.

Inputs: Two integers 'x' and 'y' to be multiplied.
Output: Returns the product of 'x' and 'y'.

How it Works:


We start with 'sum' as 0.
While 'x' isn't 1:
Checks if 'x' is odd; if so, adds 'y' to 'sum'.
Divides 'x' by 2 and doubles 'y'.
Adds the final value of 'y' to 'sum'.
Returns the sum of the correspondent odd multipliers product.

```c♯
    static int RussianMultiplication(int x, int y)
    {
        int sum = 0;

        while (x != 1)
        {
            if ((x % 2) > 0)
            {
                sum += y;
            }
            x = x / 2;
            y *= 2;
        }
        sum += y;
        return sum;
    }
```
## 
## Friendly numbers
- [Repository](https://github.com/DevJLeon/FriendlyNumber)

Finding Friendly Numbers
This algorithm aims to discover pairs of "friendly" numbers under 1500 by examining their divisors.

Variables:
temp: Tracks divisors count for 'x'.

x: Represents the second number in the pair.

Execution:
Iterates through values under 1500 to identify friendly number pairs.

Computes divisors sum for 'y' and 'x'.

Condition Check:
If the sum of divisors for 'x' matches 'y':
Returns 'x' and 'y' as a pair of friendly numbers 🤓.
```c♯
static int[] FriendlyNumber()
    {
        for (int y = 1500; y > 0; y--)
        {
            int temp = 1;
            int x = 1;

            for (int i = 2; i < y; i++)
            {
                if (y % i == 0)
                {
                    x += y / i;
                }
            }

            for (int j = 2; j < x; j++)
            {
                if (x % j == 0)
                {
                    temp += x / j;
                }
            }

            if (temp == y && y > x)
            {
                return new int[] { x, y };
            }
        }

        return Array.Empty<int>();
    }
```


## 
## Calculate Required Days
- [Repository](https://github.com/DevJLeon/CalculateDaysConsoleApp)

Counting Exercise Days


Well, here, there's not much to explain, hehe. 🤓

'a' is the number of exercises that Sam does per day, 'b' is Kim's exercises per day, and 'c' is the difference.

'p1' has an advance, so we add 'c' to 'p1'. Then, we initialize 'days' as 0, our counter.

The program returns the amount of days required for 'p2' to have completed more exercises than 'p1'.

```c♯
public static int CalculateDays(int a, int b, int c)
{
    int p1 = 0 + c;
    int p2 = 0;
    int days = 0;

    for (int i = 1; p1 + 1 > p2; i++)
    {
        p1 += a;
        p2 += b;
        days = i;
    }

    return days;
}

```

## 
## The largest subsequence of an Array
- [Repository](https://github.com/DevJLeon/LongestSubArrayConsoleApp)
```c♯
public static int Subsequences(int n)
    {
        List<int> mainArray = new List<int>();

        for (int i = 0; i < n; i++)
        {
            Console.Write($"Number {i + 1}: ");
            mainArray.Add(Convert.ToInt32(Console.ReadLine()));
        }

        mainArray.Sort();
        int result = LongestSubsequence(mainArray);
        return result;
    }
```
```c♯
public static int LongestSubsequence(List<int> mainArray)
    {
        int n = mainArray.Count;
        int largest = 0;
        
        for (int i = 0; i < n; i++)
        {
            for (int j = i + 1; j <= n; j++)
            {
                List<int> subArray = mainArray.Skip(i).Take(j - i).ToList();

                bool sum = IsValid(subArray);

                if (sum)
                {
                    int length = subArray.Count;
                    if (length > largest)
                    {
                        largest = length; 
                    } 
                }
            }
        }
        return largest;
    }
```
```c♯
public static bool IsValid(List<int> subArray)
    {
        int sumOfDiff = 0;
        for (int j = 1; j < subArray.Count; j++)
        {
            int difference = subArray[j] - subArray[j - 1];
            sumOfDiff += difference;
        }
        return sumOfDiff % 2 == 0;
    }
```