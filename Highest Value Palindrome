using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Collections;
using System.ComponentModel;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using System.IO;
using System.Linq;
using System.Reflection;
using System.Runtime.Serialization;
using System.Text.RegularExpressions;
using System.Text;
using System;

class Result
{

    /*
     * Complete the 'highestValuePalindrome' function below.
     *
     * The function is expected to return a STRING.
     * The function accepts following parameters:
     *  1. STRING s
     *  2. INTEGER n
     *  3. INTEGER k
     */

    public static string highestValuePalindrome(string s, int n, int k)
    {
        char[] arr = s.ToCharArray();
        bool[] changed = new bool[n];

        int left = 0, right = n - 1;
        // Pass 1: make palindrome with minimal changes
        while (left < right)
        {
            if (arr[left] != arr[right])
            {
                char bigger = arr[left] > arr[right] ? arr[left] : arr[right];
                arr[left] = arr[right] = bigger;
                changed[left] = changed[right] = true;
                k -= 1;
                if (k < 0) return "-1";
            }
            left++;
            right--;
        }

        // Pass 2: maximize by turning digits to '9'
        left = 0; right = n - 1;
        while (left <= right && k > 0)
        {
            if (left == right)
            {
                // middle element in odd-length string
                if (k > 0) arr[left] = '9';
            }
            else
            {
                if (arr[left] != '9')
                {
                    // cost is 1 if either side was changed in pass1, else 2
                    int cost = (changed[left] || changed[right]) ? 1 : 2;
                    if (k >= cost)
                    {
                        arr[left] = arr[right] = '9';
                        k -= cost;
                    }
                }
            }
            left++;
            right--;
        }

        return new string(arr);
    }
}

class Solution
{
    public static void Main(string[] args)
    {
        TextWriter textWriter = new StreamWriter(@System.Environment.GetEnvironmentVariable("OUTPUT_PATH"), true);

        string[] firstMultipleInput = Console.ReadLine().TrimEnd().Split(' ');

        int n = Convert.ToInt32(firstMultipleInput[0]);

        int k = Convert.ToInt32(firstMultipleInput[1]);

        string s = Console.ReadLine();

        string result = Result.highestValuePalindrome(s, n, k);

        textWriter.WriteLine(result);

        textWriter.Flush();
        textWriter.Close();
    }
}
