# Quick Sort Algorithm

> **Purpose:** Understand Quick Sort by reading and following its rules, not by memorizing code.

Quick Sort works because it does the same simple thing again and again.  
Each step follows fixed instructions, and the algorithm succeeds by never breaking them.

---

## The Single Action That Drives Everything
Quick Sort is built around one action:

**Choose one element and put it where it belongs.**
Once an element reaches its correct position, it is never touched again.  
The entire algorithm is just this action repeated on smaller and smaller sections.

---

## Working Area: What the Algorithm Focuses On
Quick Sort never thinks about the whole array after the first step.  
It always works on a specific portion of the array:

`array[low ... high]`

Everything outside this range is already handled or irrelevant.

This focus keeps the logic simple and controlled.

---

## How Decisions Are Made Inside a Step
Within the current range, Quick Sort selects a **pivot**.  
The pivot is used as a reference point to decide where other elements belong.

Each element is checked once and classified:
- Smaller than pivot → goes left  
- Larger than pivot → goes right  
There are no exceptions to this rule.

---

## Rearranging Without Losing Track
As the array is scanned, Quick Sort keeps a boundary that separates confirmed smaller elements from the rest.

Whenever an element is found that belongs on the left side, it is moved across the boundary.  
Elements that belong on the right side are left untouched.

This continues until the entire range has been scanned exactly once.

---

## The Moment an Element Becomes Final
After scanning is complete, the pivot is placed between the two groups.

At this moment:
- All smaller elements are on the left
- All larger elements are on the right
- The pivot is in its **final position**

This position will never change again.

This is the most important moment in Quick Sort.

---

## Shrinking the Problem Space
Once the pivot is fixed, the array splits into two independent parts:
- Left of the pivot
- Right of the pivot

Quick Sort now repeats the same process on each part.  
No new rules are introduced — only smaller ranges.

---

## When the Process Naturally Stops
As the ranges shrink, they eventually contain:
- No elements, or
- A single element

Such ranges are already sorted, so Quick Sort stops automatically.  
No special stopping logic is required.

---

## Why This Method Is Fast in Practice
Quick Sort performs well because:
- It minimizes unnecessary swaps
- It works directly inside the array
- It reduces the problem size quickly when pivots are reasonable

However, repeated poor pivot choices can slow it down.  
The algorithm itself is simple — performance depends on how evenly the array is divided.

---

## Mistakes That Break the Algorithm
Most Quick Sort errors come from:
- Placing the pivot too early
- Forgetting to reduce the range
- Mixing different partition rules
- Mishandling index boundaries

The algorithm fails not because it is complex, but because its rules were not followed exactly.

---

## How to Think About Quick Sort
Do not think of Quick Sort as “sorting.”  
Think of it as **locking elements into place**.
Each step locks one element permanently.  
When all elements are locked, the array is sorted.

---

## Key Takeaway
Quick Sort succeeds because it follows a disciplined, repeatable process:  
focus on a range, apply simple rules, fix one element, and repeat.

If you respect the rules, the algorithm works every time.

## Example Structure: Quick Sort as a Process
```cpp
// Step 1: Select a pivot
int pivot = arr[high];

// Step 2: Prepare a boundary for smaller elements
int i = low - 1;

// Step 3: Scan the current range
for (int j = low; j < high; j++) {
    // Step 4: Apply the rule
    if (arr[j] < pivot) {
        i++;
        swap(arr[i], arr[j]);
    }
}

// Step 5: Place the pivot in its final position
swap(arr[i + 1], arr[high]);
int pivotIndex = i + 1;

// Step 6: Repeat the same process on smaller ranges
quickSort(arr, low, pivotIndex - 1);
quickSort(arr, pivotIndex + 1, high);
```
