# Two Pointers Pattern

## Introduction
The **Two Pointers** pattern is a versatile technique used in problem-solving to efficiently traverse or manipulate sequential data structures, such as arrays or linked lists. As the name suggests, it involves maintaining two pointers that traverse the data structure in a coordinated manner, typically starting from different positions or moving in opposite directions.

These pointers dynamically adjust based on specific conditions or criteria, allowing for the efficient exploration of the data and enabling solutions with optimal time and space complexity. Whenever there’s a requirement to find two data elements in an array that satisfy a certain condition, the **Two Pointers** pattern should be the first strategy to consider.

## Why Use Two Pointers?
The naive approach to solving many problems involving pairs of elements would be using **nested loops**, which often results in a time complexity of **O(n²)**. However, by leveraging two pointers, we can often reduce the time complexity to **O(n)**. This is particularly useful when dealing with:

- **Sorted arrays or strings**
- **Palindrome verification**
- **Finding pairs in arrays**
- **Merging sorted arrays**
- **Reversing sequences**

## Examples
### 1. Reversing an Array
Given an array of integers, we can reverse it **in-place** using two pointers:

- One pointer starts from the **beginning** of the array.
- The other pointer starts from the **end**.
- Swap the elements at these pointers and move them towards each other until they meet in the middle.

#### Code Example (Java)
```java
public class ReverseArray {
    public static void reverseArray(int[] arr) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        reverseArray(arr);
        System.out.println(Arrays.toString(arr)); // Output: [5, 4, 3, 2, 1]
    }
}
```

### 2. Checking If a String is a Palindrome
A palindrome reads the same forward and backward. We can check this using two pointers:

- One pointer starts at the **beginning** of the string.
- The other pointer starts at the **end**.
- Compare characters at both pointers and move them inward.

#### Code Example (Java)
```java
public class PalindromeCheck {
    public static boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
    public static void main(String[] args) {
        System.out.println(isPalindrome("racecar")); // Output: true
        System.out.println(isPalindrome("hello"));   // Output: false
    }
}
```

### 3. Finding a Pair with a Given Sum in a Sorted Array
Given a **sorted array** and a target sum, find two numbers that add up to the sum:

- Start with one pointer at the **beginning** and another at the **end**.
- If the sum of the two numbers is **less than** the target, move the left pointer **right**.
- If the sum is **greater**, move the right pointer **left**.
- Stop when the target sum is found.

#### Code Example (Java)
```java
public class PairWithSum {
    public static int[] findPairWithSum(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int currentSum = arr[left] + arr[right];
            if (currentSum == target) {
                return new int[]{arr[left], arr[right]};
            } else if (currentSum < target) {
                left++;
            } else {
                right--;
            }
        }
        return new int[]{}; // Return empty array if no pair is found
    }
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 6};
        int target = 6;
        int[] result = findPairWithSum(arr, target);
        System.out.println(Arrays.toString(result)); // Output: [2, 4]
    }
}
```

## When to Use the Two Pointers Pattern
You should consider using the Two Pointers technique if all the following conditions are met:

1. **Linear Data Structure** - The input data can be traversed sequentially (e.g., arrays, linked lists, strings).
2. **Processing Pairs** - The problem involves comparing or processing elements at two different positions.
3. **Dynamic Pointer Movement** - The movement of the pointers depends on the current conditions, making it efficient compared to brute-force solutions.

## Real-World Applications
### Memory Management
The **Two Pointers** pattern is widely used in memory allocation and deallocation:
- The **start pointer** marks the beginning of the available memory block.
- The **end pointer** marks the end of the allocated memory.
- As new memory is allocated, the **start pointer** moves forward.
- As memory is freed, the **start pointer** moves backward.
- The **end pointer** remains fixed to prevent overlapping allocations.

This efficient memory management system is used in operating systems and embedded systems for optimal memory utilization.

## Conclusion
The **Two Pointers** pattern is a powerful and efficient approach to solving problems related to searching, pairing, and reversing elements in sequential data structures. By leveraging **optimized pointer movement**, we can significantly reduce time complexity and enhance performance. It is a must-know technique for coding interviews and real-world applications.

### Key Takeaways
- Reduces **O(n²)** time complexity to **O(n)** in many problems.
- Works best for **linear data structures**.
- Used in **string processing, searching, and memory management**.

Mastering the **Two Pointers** pattern will help you efficiently tackle many algorithmic challenges!