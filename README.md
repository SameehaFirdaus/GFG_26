# GFG_26
---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Greedy
  - Sorting
---

# 🚀 _Day 26. Non-overlapping Intervals_ 🧠

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/non-overlapping-intervals)

## 💡 **Problem Description:**

Given a 2D array `intervals[][]` where `intervals[i] = [starti, endi]` represents an interval, return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

## 🔍 **Example Walkthrough:**

**Input:**  
`intervals[][] = [[1, 2], [2, 3], [3, 4], [1, 3]]`  
**Output:**  
`1`

**Explanation:**  
Removing `[1, 3]` makes the rest of the intervals non-overlapping.



**Input:**  
`intervals[][] = [[1, 3], [1, 3], [1, 3]]`  
**Output:**  
`2`

**Explanation:**  
You need to remove two `[1, 3]` intervals to make the rest non-overlapping.



**Input:**  
`intervals[][] = [[1, 2], [5, 10], [18, 35], [40, 45]]`  
**Output:**  
`0`

**Explanation:**  
All intervals are already non-overlapping.



### Constraints

- `1 ≤ intervals.size() ≤ 10^5`
- `|intervals[i]| == 2`
- `0 ≤ starti < endi ≤ 5 × 10^4`



## 🎯 **My Approach:**

1. **Sort Intervals by Start Time**:  
   - Sort the intervals by their start time to process them in order. This ensures that overlapping intervals can be easily identified.

2. **Iterate Through Intervals**:  
   - Use a variable `prevEnd` to track the end of the last interval.  
   - For each interval, check if the current interval's start time is less than `prevEnd`.  
   - If overlapping, increment the removal count and update `prevEnd` to the smaller of the two end times (to minimize further overlaps).  
   - Otherwise, update `prevEnd` to the current interval's end time.

3. **Return the Count of Removals**:  
   - The final count will represent the minimum number of intervals to remove.



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n log n), where `n` is the size of the `intervals` array. Sorting the intervals dominates the computation.  
- **Expected Auxiliary Space Complexity:** O(1), as only a constant amount of extra space is used for variables.


## 📝 **Solution Code**
## Code (Python)

```python
class Solution:
    def minRemoval(self, intervals):
        intervals.sort(key=lambda x: x[0])
        count, prevEnd = 0, intervals[0][1]
        
        for i in range(1, len(intervals)):
            if intervals[i][0] < prevEnd:
                count += 1
                prevEnd = min(prevEnd, intervals[i][1])
            else:
                prevEnd = intervals[i][1]
        
        return count
```
