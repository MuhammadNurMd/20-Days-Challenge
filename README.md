# 20-Days-Challenge

<details><summary><b>Day 1</b></summary>
<p>

# 1. Count Digits in an Integer

## Summary of Methods

### Method 1: Iterative Method

### Description: Loop to divide the number by 10 until it becomes 0, counting iterations.

```cpp
int countDigits(int n) {
    int cnt = 0;
    while (n > 0) {
        cnt++;
        n /= 10;
    }
    return cnt;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

## Method 2: Logarithmic Method

Description: Use logarithm base 10 to calculate the number of digits.

```cpp
int countDigitsTwo(int n) {
    int cnt = (int)(log10(n) + 1);
    return cnt;
}
```

- Time Complexity: O(1)
- Space Complexity: O(1)

## Method 3: String Conversion Method

Description: Convert the integer to a string and count the length.

```cpp
int countDigitsString(int n) {
    string numStr = to_string(n);
    return numStr.length();
}
```

- Time Complexity: O(N) where N is the number of digits.
- Space Complexity: O(N)

## Method 4: Recursive Method

Description: Use recursion to count digits by dividing the number by 10 in each call.

```cpp
int countDigitsRecursive(int n) {
    if (n == 0) return 0;
    return 1 + countDigitsRecursive(n / 10);
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(log10(N) + 1)

## Method 5: Mathematical Iterative Method

Description: Use a mathematical approach similar to the logarithmic method.

```cpp
int countDigitsMath(int n) {
    if (n == 0) return 1;
    return floor(log10(n) + 1);
}
```
- Time Complexity: O(1)
- Space Complexity: O(1)

## Key Points
* Logarithmic Method: Efficient with constant time complexity.
* Iterative Method: Simple implementation, higher time complexity.
* String Conversion Method: Easy but higher space complexity.
* Recursive Method: Elegant but higher space complexity due to recursion stack.
* Mathematical Iterative Method: Efficient and uses mathematical properties.


# 2. Reverse a Number
## Summary of Methods
## Method 1: Iterative Method
### Description: Loop to reverse the digits by extracting the last digit and appending it to a new number.

```cpp
int reverse(int n) {
    long long revN = 0;
    while (n > 0) {
        int lastDigit = n % 10;
        revN = (revN * 10) + lastDigit;
        n /= 10;
    }
    return revN;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

## Method 2: Handling Negative Numbers and Edge Cases

### Description: Handle negative numbers and potential overflow.

```cpp
long long reverse(long long n) {
    bool isNegative = n < 0;
    n = abs(n);
    long long revN = 0;

    while (n > 0) {
        int lastDigit = n % 10;
        revN = (revN * 10) + lastDigit;
        n /= 10;
    }

    return isNegative ? -revN : revN;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

## Method 3: Recursive Method

### Description: Use recursion to reverse the digits.

```cpp
int reverseRecursiveHelper(int n, int revN) {
    if (n == 0) return revN;
    return reverseRecursiveHelper(n / 10, revN * 10 + n % 10);
}

int reverseRecursive(int n) {
    return reverseRecursiveHelper(n, 0);
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(log10(N) + 1) due to recursion stack.

## Method 4: Using String Manipulation

### Description: Convert the number to a string, reverse the string, and convert it back to an integer.

```cpp
int reverseStringMethod(int n) {
    bool isNegative = n < 0;
    string numStr = to_string(abs(n));
    reverse(numStr.begin(), numStr.end());
    int revN = stoi(numStr);
    return isNegative ? -revN : revN;
}
```

- Time Complexity: O(N) where N is the number of digits.
- Space Complexity: O(N) due to string storage.

## Key Points

- Iterative Method: Simple implementation, works efficiently.
- Handling Negative Numbers: Takes care of negative values and edge cases.
- Recursive Method: Elegant but has higher space complexity due to recursion stack.
- String Manipulation: Easy to understand but less efficient due to string operations.


# 3. Check Palindrome
## Summary of Methods
# Method 1: Reverse and Compare
## Description: Reverse the digits of the number and compare it with the original number.

```cpp
bool palindrome(int x) {
    if ((x < 0) || (x % 10 == 0 && x != 0)) {
        return false;
    }

    int dup = x;
    long long rev = 0;
    while (x) {
        int ld = x % 10;
        x /= 10;
        rev = (rev * 10) + ld;
    }

    return dup == rev;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

# Method 2: Reverse and Compare with Comments

## Description: This method is similar to Method 1 but includes detailed comments for better understanding.

```cpp
bool palindrome(int n) {
    // Initialize a variable to store the reverse of the number
    int revNum = 0;
    // Create a duplicate variable to store the original number
    int dup = n;
    // Iterate through each digit of the number until it becomes 0
    while (n > 0) {
        // Extract the last digit of the number
        int ld = n % 10;
        // Build the reverse number by appending the last digit
        revNum = (revNum * 10) + ld;
        // Remove the last digit from the original number
        n = n / 10;
    }
    // Check if the original number is equal to its reverse
    return dup == revNum;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

# Method 3: Half Reverse Method

## Description: Reverse half of the number and compare it with the other half to determine if it's a palindrome.

```cpp
bool palindromeHalfReverse(int x) {
    // If x is negative or if x ends with 0 (but is not 0), it cannot be a palindrome
    if (x < 0 || (x % 10 == 0 && x != 0)) {
        return false;
    }

    int rev = 0;
    while (x > rev) {
        int ld = x % 10;
        x /= 10;
        rev = rev * 10 + ld;
    }

    // Check if the number is palindrome
    return x == rev || x == rev / 10;
}
```

- Time Complexity: O(log10(N) + 1)
- Space Complexity: O(1)

# Method 4: Using String Conversion

## Description: Convert the number to a string, reverse the string, and compare it with the original string.

```cpp
bool palindromeStringMethod(int x) {
    if (x < 0) return false;

    std::string numStr = std::to_string(x);
    std::string revStr = numStr;
    std::reverse(revStr.begin(), revStr.end());

    return numStr == revStr;
}
```

- Time Complexity: O(N) where N is the number of digits.
- Space Complexity: O(N) due to string storage.

## Key Points

- Reverse and Compare Method: Simple implementation, works efficiently but requires reversing the entire number.
- Half Reverse Method: More efficient for large numbers as it reduces the number of operations by half.
- String Conversion Method: Easy to understand but less efficient due to string operations.

# 4. Armstrong Number

# Problem

## An Armstrong number (also known as a narcissistic number or plenary number) is a number that is equal to the sum of its own digits each raised to the power of the number of digits. For example, 153 is an Armstrong number because:

# Solution Methods

## Method 1: Brute Force Method

## Description: Calculate the sum of each digit raised to the power of the number of digits, and compare it with the original number.

```cpp
bool isArmstrong(int x) {
    int sum = 0, dup = x;
    int k = to_string(x).length();

    while (x) {
        int ld = x % 10;
        sum += pow(ld, k);
        x /= 10;
    }

    return sum == dup;
}
```

## Key Points:

- Simple and straightforward implementation.
- Involves repeated exponentiation operations for each digit.
- Requires calculating the length of the number's digits.
- Time Complexity: O(log10 (N))
- Space Complexity: O(1)

## Method 2: Using Exponentiation

## Description: Calculate the sum of each digit raised to the power of the number of digits using the pow function.

```cpp
bool isArmstrong(int x) {
    int sum = 0, dup = x;
    int k = to_string(x).length();

    while (x) {
        int ld = x % 10;
        sum += pow(ld, k);
        x /= 10;
    }

    return sum == dup;
}
```

## Key Points:

- Utilizes the pow function for exponentiation, making the code concise.
- May involve additional overhead due to function calls for exponentiation.
- Similar in concept to the brute force## method but uses library function for exponentiation.
- Time Complexity: O(log10 (N))
- Space Complexity: O(1)

## Method 3: Using Recursion

## Description: Use recursion to calculate the sum of digits raised to the power of the number of digits.

```cpp
int calculateSumOfPowers(int x, int k) {
    if (x == 0) return 0;
    return pow(x % 10, k) + calculateSumOfPowers(x / 10, k);
}

bool isArmstrong(int x) {
    int k = to_string(x).length();
    return x == calculateSumOfPowers(x, k);
}
```

## Key Points:

- Elegant solution using recursion to calculate the sum of powers.
- Recursive approach may lead to increased space complexity due to function call stack.
- Avoids the need for loop iterations to calculate the sum of powers.
- Time Complexity: O(log10 (N))
- Space Complexity: O(1)

## Method 4: Precompute Powers

## Description: Precompute the powers of each digit up to a certain maximum and store them in an array for efficient lookup.

```cpp
bool isArmstrong(int x) {
    int sum = 0, dup = x;
    int k = to_string(x).length();

    vector<int> powers = {0, 1, 8, 27, 64, 125, 216, 343, 512, 729}; // Precomputed powers up to 9^k

    while (x) {
        int ld = x % 10;
        sum += powers[ld];
        x /= 10;
    }

    return sum == dup;
}
```

## Key Points:

- Offers a trade-off between memory and computation by precomputing powers.
- Reduces the number of exponentiation operations during runtime.
- Suitable for scenarios where the range of numbers is limited and precomputation overhead is acceptable.
- Time Complexity: O(log10 (N))
- Space Complexity: O(1)


# 5. Print All Divisors
# Problem Statement: Given an integer N, return all divisors of N.

## A divisor of an integer N is a positive integer that divides N without leaving a remainder. In other words, if N is divisible by another integer without any remainder, then that integer is considered a divisor of N.

```cpp
// Brute Force Approach
// Example 1:
// Input:N = 36
// Output:[1, 2, 3, 4, 6, 9, 12, 18, 36]
// Explanation: The divisors of 36 are 1, 2, 3, 4, 6, 9, 12, 18, 36.

int* printDivisors(int n, int &size) {
    // Allocate memory for
    // the array of divisors
    int *divisors = new int[n]; 
     // Initialize the count of divisors
    int count = 0;

    for(int i = 1; i <= n; i++) {
        if(n % i == 0) {
            // Add the divisor to the array
            divisors[count++] = i; 
        }
    }
    // Update the size parameter
    // with the count of divisors
    size = count; 
    // Return the array of divisors
    return divisors; 
}
// Time Complexity: O(N) where N is the input number. The algorithm iterates through each number from 1 to n once to check if it is a divisor.

// Space Complexity : O(N) where N is the input number. The algorithm iterates through each number from 1 to n once to check if it is a divisor.

// Optimal Approach
vector<int> findDivisors(int n)
{
    vector<int> ls;
    for (int i = 1; i <= sqrt(n); i++)
    {
        if (n % i == 0)
        {
            ls.push_back(i);

            if (i != n / i)
            {
                ls.push_back(n / i);
            }
        }
    }
    sort(ls.begin(), ls.end());
    return ls;
}
// Time Complexity: O(sqrt(N)) where N is the input number. The algorithm iterates through each number from 1 to the square root of N once to check if it is a divisor.

// Space Complexity : O(2*sqrt(N))where N is the input number. This approach allocates memory for an array to hold all the divisors. The size of this array could go to be 2*(sqrt(N)).
```

# 6. Check for Prime
### Problem Statement: Given an integer N, check whether it is prime or not. A prime number is a number that is only divisible by 1 and itself and the total number of divisors is 2.

```cpp
// Example 1:
// Input:N = 2
// Output:True
// Explanation: 2 is a prime number because it has two divisors: 1 and 2 (the number itself).
bool checkPrime(int x)
{
    int cnt = 0;
    for (int i = 1; i <= x; i++)
    {
        if (x % i == 0)
        {
            cnt++;
        }
    }
    if (cnt == 2)
    {
        return true;
    }
    else
    {
        return false;
    }
}
// Time Complexity: O(N) where N is the input number as we iterate from 1 to N performing constant-time operation for each iteration.

// Space Complexity : O(1) as the space used by the algorithm does not increase with the size of the input.

bool checkPrimeTwo(int x)
{
    int cnt = 0;
    for (int i = 1; i <= sqrt(x); i++)
    {
        if (x % i == 0)
        {
            cnt++;
            if (i != x / i)
            {
                cnt++;
            }
        }
    }
    if (cnt == 2)
    {
        return true;
    }
    else
    {
        return false;
    }
    return cnt;
}
// Time Complexity: O(sqrt(N))where N is the input number. The loop iterates up to the square root of n performing constant time operations at each step.

// Space Complexity : O(1) as the space complexity remains constant and independent of the input size. Only a fixed amount of memory is required to store the integer variables.
```

# 7. GCD || LCM || HCF

# Brute Force 

```cpp
int findGcd(int n1, int n2) {
    // Initialize gcd to 1
    int gcd = 1;

    // Iterate from 1 up to
    // the minimum of n1 and n2
    for(int i = 1; i <= min(n1, n2); i++) {
        // Check if i is a common
        // factor of both n1 and n2
        if(n1 % i == 0 && n2 % i == 0) {
            // Update gcd to the
            // current common factor i
            gcd = i;
        }
    }

    // Return the greatest
    // common divisor (gcd)
    return gcd;
}
```
- Time Complexity: O(min(N1, N2)) where N1 and N2 is the input number. The algorithm iterates from 1 to the minimum of N1 and N2 and each iteration checks whether both the numbers are divisible by the current number (constant time operations).

- Space Complexity: O(1)as the space complexity remains constant and independent of the input size. Only a fixed amount of memory is required to store the integer variables.


# Better Approach
```cpp
int findGcd(int n1, int n2) {
    // Iterate from the minimum of
    // n1 and n2 down to 1
    // Start from the minimum of n1 and n2
    // because the GCD cannot
    // exceed the smaller number
    
    for(int i = min(n1, n2); i > 0; i--) {
        // Check if i is a common
        // factor of both n1 and n2
        if(n1 % i == 0 && n2 % i == 0) {
            // If i is a common factor,
            // return it as the GCD
            return i;
        }
    }
    // If no common factors are found,
    // return 1 (as 1 is always a
    // divisor of any number)
    return 1;
}
```
- Time Complexity: O(min(N1, N2)) where N1 and N2 is the input number. The algorithm iterates from the minimum of N1 and N2 to 1 and each iteration checks whether both the numbers are divisible by the current number (constant time operations).

- Space Complexity: O(1) as the space complexity remains constant and independent of the input size. Only a fixed amount of memory is required to store the integer variables.

# Optimal Approach
```cpp

int findGcd(int a, int b) {
    // Continue loop as long as both
    // a and b are greater than 0
    while(a > 0 && b > 0) {
        // If a is greater than b,
        // subtract b from a and update a
        if(a > b) {
             // Update a to the remainder
             // of a divided by b
            a = a % b;
        }
        // If b is greater than or equal
        // to a, subtract a from b and update b
        else {
            // Update b to the remainder
            // of b divided by a
            b = b % a; 
        }
    }
    // Check if a becomes 0,
    // if so, return b as the GCD
    if(a == 0) {
        return b;
    }
    // If a is not 0,
    // return a as the GCD
    return a;
}
```
- Time Complexity: O(min(N1, N2)) where N1 and N2 is the input number. The algorithm iterates from the minimum of N1 and N2 to 1 and each iteration checks whether both the numbers are divisible by the current number (constant time operations).

- Space Complexity: O(1) as the space complexity remains constant and independent of the input size. Only a fixed amount of memory is required to store the integer variable

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


<details><summary><b>Day 3</b></summary>
<p>

#### Basic Hashing and STL

</p>
</details>
