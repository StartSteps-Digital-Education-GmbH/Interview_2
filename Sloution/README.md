### Solution Implementation

```typescript
type Job = [number, number, number]; // [jobId, deadline, profit]

function jobScheduling(jobs: Job[]): [number, number] {
    // Step 1: Sort jobs based on profit in descending order
    jobs.sort((a, b) => b[2] - a[2]); // Sort by profit

    const n = jobs.length;
    const maxDeadline = Math.max(...jobs.map(job => job[1])); // Find the maximum deadline
    const slots: (number | null)[] = new Array(maxDeadline).fill(null); // Create an array to track free time slots
    let totalProfit = 0;
    let jobCount = 0;

    // Step 2: Iterate through the sorted jobs
    for (const job of jobs) {
        const [jobId, deadline, profit] = job;

        // Step 3: Find a free slot for this job (from its deadline to the start)
        for (let j = Math.min(deadline, maxDeadline) - 1; j >= 0; j--) {
            if (slots[j] === null) { // If the slot is free
                slots[j] = jobId; // Assign the job to this slot
                totalProfit += profit; // Add profit
                jobCount++; // Increment job count
                break; // Break out of the loop once the job is scheduled
            }
        }
    }

    return [jobCount, totalProfit]; // Return the total number of jobs and total profit
}

// Example usage
const jobs = [
    [1, 4, 20],
    [2, 1, 1],
    [3, 1, 40],
    [4, 1, 30]
];
console.log(jobScheduling(jobs)); // Output: [2, 60]
```

### Explanation of Steps

1. **Sorting Jobs**: The first step is to sort the jobs based on their profit in descending order. This allows us to prioritize jobs that yield higher profits, which is crucial for maximizing total profit.

2. **Finding Maximum Deadline**: We determine the maximum deadline from the jobs to know how many slots we need to manage. This helps in creating an array that tracks which time slots are occupied.

3. **Creating Slots**: We create an array `slots` initialized with `null` values, representing free time slots. The length of this array is equal to the maximum deadline.

4. **Scheduling Jobs**: For each job, we check from its deadline down to the first time slot (0). If we find a free slot, we assign the job to that slot, add its profit to `totalProfit`, and increment the `jobCount`.

5. **Returning Results**: Finally, we return an array containing the total number of jobs completed and the total profit earned.

### Tips for Candidates

1. **Understand the Problem**: Before jumping into coding, take a moment to fully understand the problem statement. Clarify any doubts with the interviewer.

2. **Plan Your Approach**: Outline your approach on paper or verbally before coding. This helps in organizing your thoughts and reduces the chances of errors.

3. **Optimize Your Solution**: Think about the time complexity of your solution. In this case, sorting the jobs takes O(n log n), and scheduling takes O(n * m) in the worst case, where m is the maximum deadline. Aim for efficient solutions.

4. **Test Edge Cases**: Consider edge cases such as:
   - All jobs having the same deadline.
   - Jobs with zero profit.
   - Jobs with deadlines greater than the number of jobs.

5. **Communicate Clearly**: As you code, explain your thought process to the interviewer. This shows your problem-solving skills and helps the interviewer understand your approach.

6. **Practice**: Regularly practice coding problems on platforms like LeetCode, HackerRank, or CodeSignal to improve your skills and speed.


