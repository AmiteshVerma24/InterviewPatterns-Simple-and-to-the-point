# Sliding Window Algorithm

## Introduction
The **Sliding Window** technique is an optimized approach for solving problems that involve processing contiguous subsets of data efficiently. Instead of recalculating results from scratch every time, the window "slides" over the data structure, updating the result incrementally. This leads to significant performance improvements over brute-force approaches.

---

## How It Works
The sliding window pattern involves maintaining a dynamic window that adjusts its boundaries to track relevant elements. The window slides through an array or string, processing elements efficiently. It can be implemented in two ways:

1. **Fixed-size window:** The window maintains a constant size while sliding.
2. **Variable-size window:** The window expands or shrinks dynamically based on the problem's requirements.

### Analogy
Imagine walking down a long hallway filled with paintings while looking through a small window. As you move, new paintings come into view while others disappear. This is similar to how the sliding window works over an array or string.

---

## Why Use Sliding Window?
### Efficiency
Many brute-force solutions require **O(kn)** time complexity, as they recompute values for each subarray. The sliding window technique allows updates in **O(1)** time, reducing the overall complexity to **O(n)**.

#### Example Problem: Find the maximum sum of `k` consecutive elements
**Naive approach:** Compute the sum for every possible subarray of size `k`.
- **Time Complexity:** O(kn)

**Sliding Window approach:**
- Compute the sum for the first `k` elements.
- Slide the window by subtracting the element exiting the window and adding the new element entering.
- **Time Complexity:** O(n)

### Java Implementation
```java
public class SlidingWindowMaxSum {
    public static int maxSum(int[] arr, int k) {
        if (arr.length < k) return -1;
        
        int maxSum = 0, windowSum = 0;
        
        // Compute sum of first k elements
        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }
        maxSum = windowSum;
        
        // Slide the window
        for (int i = k; i < arr.length; i++) {
            windowSum += arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }
        
        return maxSum;
    }
    
    public static void main(String[] args) {
        int[] arr = {2, 1, 5, 1, 3, 2};
        int k = 3;
        System.out.println("Maximum sum of subarray of size " + k + " is: " + maxSum(arr, k));
    }
}
```

---

## Problems Solved with Sliding Window
### 1. Maximum Sum Subarray of Size K (Fixed Window)
**Problem:** Given an array of integers and an integer `k`, find the maximum sum of any contiguous subarray of size `k`.

- **Example Input:** `[2, 1, 5, 1, 3, 2]`, `k = 3`
- **Output:** `9`

### 2. Longest Substring Without Repeating Characters (Variable Window)
**Problem:** Given a string, find the length of the longest substring without repeating characters.

**Java Implementation:**
```java
import java.util.HashSet;

public class LongestUniqueSubstring {
    public static int longestUniqueSubstr(String s) {
        int left = 0, maxLength = 0;
        HashSet<Character> set = new HashSet<>();
        
        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }
        return maxLength;
    }
    
    public static void main(String[] args) {
        String s = "abcabcbb";
        System.out.println("Longest substring without repeating characters: " + longestUniqueSubstr(s));
    }
}
```

### 3. Smallest Subarray with Given Sum (Variable Window)
**Problem:** Given an array of positive integers and a target sum, find the length of the smallest contiguous subarray whose sum is greater than or equal to the target.

**Java Implementation:**
```java
public class SmallestSubarraySum {
    public static int minSubArrayLen(int target, int[] nums) {
        int left = 0, sum = 0, minLength = Integer.MAX_VALUE;
        
        for (int right = 0; right < nums.length; right++) {
            sum += nums[right];
            while (sum >= target) {
                minLength = Math.min(minLength, right - left + 1);
                sum -= nums[left];
                left++;
            }
        }
        return minLength == Integer.MAX_VALUE ? 0 : minLength;
    }
    
    public static void main(String[] args) {
        int[] nums = {2, 3, 1, 2, 4, 3};
        int target = 7;
        System.out.println("Smallest subarray length: " + minSubArrayLen(target, nums));
    }
}
```

---

## When to Use Sliding Window
Use the **Sliding Window** pattern if your problem satisfies these conditions:
- **Contiguous Data:** The input is an array or string.
- **Subset Processing:** You need to perform repeated calculations on subsets (subarrays or substrings).
- **Optimized Computation:** The solution can be updated efficiently in O(1) or minimal time.

---

## Real-World Applications
- **Network Analysis:** Finding the maximum number of users in a `k`-millisecond interval.
- **Video Streaming:** Calculating the median number of buffering events per minute.
- **Social Media Mining:** Identifying the shortest sequence of posts that cover all topics discussed by another user.

---

## Conclusion
The **Sliding Window** technique is a powerful optimization strategy used to solve problems involving contiguous data efficiently. By avoiding redundant calculations, it reduces time complexity from **O(kn) to O(n)**, making it a preferred approach in many coding interviews and real-world scenarios.

