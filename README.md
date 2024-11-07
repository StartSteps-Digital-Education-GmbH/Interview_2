# Interview 2: Job Sequencing Problem

**Problem Statement**:
You are tasked with implementing a function named `jobScheduling` in TypeScript. This function should take an array of jobs, where each job is represented as a tuple containing a job ID, a deadline, and a profit. The goal is to determine the maximum number of jobs that can be completed by their respective deadlines and the maximum profit that can be earned from those jobs.

**Requirements**:
- Input: An array of tuples, where each tuple is of the form `[jobId: number, deadline: number, profit: number]`.
- Output: An array of two numbers: the first number is the maximum number of jobs that can be completed, and the second number is the maximum profit that can be earned.
- Input types: `Array<[number, number, number]>` representing an array of jobs.

**Example**:
```typescript
const jobs = [
  [1, 4, 20],
  [2, 1, 1],
  [3, 1, 40],
  [4, 1, 30]
];
console.log(jobScheduling(jobs)); // Output: [2, 60]

const jobs2 = [
  [1, 2, 100],
  [2, 1, 19],
  [3, 2, 27],
  [4, 1, 25],
  [5, 1, 15]
];
console.log(jobScheduling(jobs2)); // Output: [2, 127]
```

**Constraints**:
- The number of jobs will be between `1` and `100,000` (1 <= jobs.size <= 10^5).
- The job ID and deadline will be between `1` and the size of the jobs array (1 <= deadline, jobId <= jobs.size).
- The profit for each job will be between `1` and `500` (1 <= profit <= 500).

**Expected Solution**:
The candidate should create a function that:
1. Sorts the jobs based on profit in descending order.
2. Uses a greedy approach to select jobs that can be completed by their deadlines.
3. Keeps track of the maximum number of jobs completed and the total profit earned.

**Expected Timeline**:
Estimated time to complete: **40 minutes**.

# Output Format
The output of the function should match:
- If called with `jobScheduling([[1, 4, 20], [2, 1, 1], [3, 1, 40], [4, 1, 30]])`, it should return `[2, 60]`.

# Notes
- The challenge tests the candidate's ability to implement sorting and greedy algorithms, as well as their understanding of TypeScript types and array manipulation.
- Candidates should be able to explain their approach and discuss the time complexity of their solution.
