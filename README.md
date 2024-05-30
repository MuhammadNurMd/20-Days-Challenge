# 20-Days-Challenge

<details><summary><b>Day 1</b></summary>
<p>

#### Count Digit

</p>
</details>

<details><summary><b>Day 2</b></summary>
<p>
# Recursion Overview

## What is Recursion?

Recursion is a phenomenon where a function calls itself until a specified condition is fulfilled.

## What is Stack Overflow in Recursion?

When recursion calls are executed, they’re stored in a recursion stack. If there is no base condition to terminate the recursion, it results in a stack overflow, exceeding the memory limit and causing the program to terminate with an error.

## Base Condition

A base condition is a condition in a recursive function that allows the function to terminate and not run infinitely. After encountering the base condition, the function returns control to its parent function.

## Recursive Tree

A recursive tree is a representation of recursion showing how functions are called and returned as a series of events.


## Summary

- **Recursion**: A function calling itself.
- **Base Condition**: A condition to stop the recursion.
- **Stack Overflow**: Occurs when there's no base condition, leading to infinite recursion and memory overflow.
- **Recursive Tree**: Visual representation of recursive calls.

## 1. Recursion

```cpp
int cnt = 0;
void recursion()
{
    // Base Case
    if (cnt == 5)
        return;
    cout << cnt << endl;
    cnt++;
    recursion();
}
/*
    Problem: Print numbers from 1 to N without the help of loops.
    Input: N = 10
    Output: 1 2 3 4 5 6 7 8 9 10
*/
int num = 1;
void printNum(int x)
{
    // Base Condition
    if (num == x + 1)
        return;
    cout << num << " ";
    num++;
    printNum(x);
}
```

- Time Complexity: O(1)
- Space Complexity: O(1)

## 2. Print N times using Recursion

```cpp
/*
Problem: Print your Name N times using recursion
Input: 5
Output: GFG GFG GFG GFG GFG
*/
int cnt = 0;
void printGfg(int N)
{
    // Code here
    if (cnt == N)
        return;
    cout << "GFG" << " ";
    cnt++;
    printGfg(N);
}

void printNames(int i, int n){
    if(i > n) return;
    cout << "Nur" << endl;
    printNames(i+1, n);
}
```

- Time Complexity: O(N)
- Space Complexity: O(N)

## 3. 1 to N using Recursion

```cpp
void func(int i, int x)
{
    if (i > x)
        return;
    cout << i << " ";
    func(i + 1, x);
}

// Backtracking
void funcTwo(int i, int x)
{
    if (i < 1)
        return;
    funcTwo(i - 1, x);
    cout << i << " ";
}
```

- Time Complexity: O(N)
- Space Complexity: O(N)

## 4. Problem: Print from N to 1 using Recursion

```cpp
/*
Print numbers from N to 1 (space separated) without the help of loops.
Input: N = 10
Output: 10 9 8 7 6 5 4 3 2 1

*/
void func(int n)
{
    if (n < 1)
        return;
    cout << n << " ";
    func(n - 1);
}

void funcTwo(int i, int n)
{
    if (i < 1)
        return;
    cout << i << " ";
    funcTwo(i - 1, n);
}

// Backtracking
void funcThree(int i, int n){
    if(i > n) return;
    funcThree(i+1, n);
    cout << i << " ";
}
```

- Time Complexity: O(N)
- Space Complexity: O(N)

## 5. Sum of First N Numbers

```cpp
/*
Intuition: We can use the formula for the sum of N numbers, i.e N(N+1)/2.
*/

void sumNumbers(int N)
{
    int sum = N * (N + 1) / 2;
    cout << "The sum of the first " << N << " numbers is: " << sum << endl;
}
Time Complexity: O(1)
Space Complexity: O(1)

void sumNumbers(int n)
{
    int sum = 0;
    for (int i = 0; i <= n; i++)
    {
        sum += i;
    }
    cout << sum << endl;
}

// 1. Parameterized way
void sumNumbers(int i, int sum)
{
    if (i < 1)
    {
        cout << sum << endl;
        return;
    }
    sumNumbers(i - 1, sum + i);
}

// 2. Functional way
int sumFormula(int n)
{
    if (n == 0)
    {
        return 0;
    }

    return n + sumFormula(n - 1);
}

/*
    Given an integer n, calculate the sum of series 1^3 + 2^3 + 3^3 + 4^3 + … till n-th term.
    Input: n=5
    Output: 225
    Explanation:  1^3 + 2^3 + 3^3 + 4^3 +5^3 = 225
*/
long long sumOfSeries(long long n) {
        // code here
        // long long sum = 0;
        // for(long long i=1; i<=n; i++){
        //     sum += pow(i *  i * i);
        // }
        long long sum = (n * (n+1)/2) * (n * (n+1)/2);
        return sum;
    }
```

## 6. Factorial of N Numbers

```cpp

// Recursive way
int factorial(int n)
{
    if (n == 0 || n == 1)
    {
        return 1;
    }

    return n * factorial(n - 1);
}
Time Complexity: O(n)
Space Complexity: O(n)

// Iterative Way
int factorialTwo(int n)
{
    int ans = 1;
    for (int i = 1; i <= n; i++)
    {
        ans *= i;
    }
    return ans;
}
Time Complexity: O(n)
Space Complexity: O(1)

/*
    Find all factorial numbers less than or equal to N
    A number N is called a factorial number if it is the factorial of a positive integer. For example, the first few factorial numbers are 1, 2, 6, 24, 120,
    Given a number N, the task is to return the list/vector of the factorial numbers smaller than or equal to N.

    Input: N = 3
    Output: 1 2
    Explanation: The first factorial number is 1 which is less than equal to N. The second number is 2 which is less than equal to N,but the third factorial number is 6 which is greater than N. So we print only 1 and 2.
*/
long long factorial(int x){
        if (x==0)
            return 1;
        return x*factorial(x-1);
    }

    vector<long long> factorialNumbers(long long N)
    {
        vector<long long> ans;
        for(int i=1; i<=N; i++){
            if(factorial(i) <= N){
                ans.push_back(factorial(i));
            }else{
                break;
            }
        }
        return ans;
    }
Expected Time Complexity: O(K), Where K is the number of factorial numbers.
Expected Auxiliary Space: O(1)
```

## 7. Reverse on Array

```cpp
//Function to print array
void printArray(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }
}

// Solution 1: Using an extra array.
void reverseArray(int arr[], int n)
{
    int ans[n];
    for (int i = n - 1; i >= 0; i--)
    {
        ans[n - i - 1] = arr[i];
    }

    printArray(ans, n);
}
// Time Complexity: O(n), single-pass for reversing array.
// Space Complexity: O(n), for the extra array used.

// Solution 2: Space-optimized iterative method
void reverseArray(int arr[], int n)
{
    int p1 = 0, p2 = n - 1;
    while (p1 < p2)
    {
        swap(arr[p1], arr[p2]);
        p1++;
        p2--;
    }
    printArray(arr, n);
}
Time Complexity: O(n), single-pass involved.
Space Complexity: O(1)

// Solution 3: Recursive method
void reverseArray(int arr[], int start, int end)
{
    if (start < end)
    {
        swap(arr[start], arr[end]);
        reverseArray(arr, start + 1, end - 1);
    }
}
// Time Complexity: O(n)
// Space Complexity: O(1)

// Solution 4: Using library function (New Approach)
// Reverse array using library function
void reverseArray(int arr[], int n)
{
    // Reversing elements from index 0 to n-1
    reverse(arr, arr + n);
}
Time Complexity: O(n)
Space Complexity: O(1)
```

## 8. Palindrome Check String

### Problem: A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

### Given a string s, return true if it is a palindrome, or false otherwise.

```cpp

bool isPalindrome(string s)
{
    int left = 0, right = s.length() - 1;
    while (left < right)
    {
        if (!isalnum(s[left]))
            left++;
        else if (!isalnum(s[right]))
            right--;
        else if (tolower(s[left]) != tolower(s[right]))
            return false;
        else
        {
            left++;
            right--;
        }
    }
    return true;
}
Time Complexity:  O(N)
Space Complexity: O(1)

// Recursive Approach:
bool palindrome(int i, string &s)
{

    // Base Condition
    // If i exceeds half of the string means all the elements
    // are compared, we return true.
    if (i >= s.length() / 2)
        return true;

    // If the start is not equal to the end, not the palindrome.
    if (s[i] != s[s.length() - i - 1])
        return false;

    // If both characters are the same, increment i and check start+1 and end-1.
    return palindrome(i + 1, s);
}
Time Complexity: O(N) { Precisely, O(N/2) as we compare the elements N/2 times and swap them}.
Space Complexity: O(1) { The elements of the given array are swapped in place so no extra space is required}.

// Beats 100.00% of users with C++

class Solution {
public:
    bool isPalindrome(string s) {
        // Preprocess the string
        string cleanedString = preprocessString(s);
        // Start the recursive check
        return isPalindromeHelper(0, cleanedString);
    }

private:
    string preprocessString(const string& s) {
        string result;
        for (char c : s) {
            if (isalnum(c)) {
                result += tolower(c);
            }
        }
        return result;
    }

    bool isPalindromeHelper(int i, const string& s) {
        // Base condition: If i exceeds half of the string length, return true
        if (i >= s.length() / 2)
            return true;

        // If the characters at index i and its corresponding index from the end
        // are not equal, return false
        if (s[i] != s[s.length() - i - 1])
            return false;

        // Recursive call with the next index
        return isPalindromeHelper(i + 1, s);
    }
};

```

## 9. Fibonacci Number
### Problem: The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

- F(0) = 0, F(1) = 1
- F(n) = F(n - 1) + F(n - 2), for n > 1.
- Given n, calculate F(n).

Input: n = 2

Output: 1

Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.

```cpp

int fibonacci(int N)
{
    // Base Condition.
    if (N <= 1)
    {
        return N;
    }

    // Problem broken down into 2 functional calls
    // and their results combined and returned.
    int last = fibonacci(N - 1);
    int slast = fibonacci(N - 2);

    return last + slast;
    return fibonacci(N - 1) + fibonacci(N - 2);
}
// Time Complexity: O(2^N) { This problem involves two function calls for each iteration which further expands to 4 function calls and so on which makes worst-case time complexity to be exponential in nature }.

// Space Complexity: O(N) { At maximum there could be N function calls waiting in the recursion stack since we need to calculate the Nth Fibonacci number for which we also need to calculate (N-1) Fibonacci numbers before it }.
```


</p>
</details>

