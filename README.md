# Leetcode_Day90
# Day 90 – Implement Stack using Queues

**LeetCode Problem:** [225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)

**Difficulty:** Easy  
**Topic:** Stack, Queue, Data Structures  
**Language:** Java

## Problem Overview

Implement a Stack (LIFO – Last In, First Out) using only two Queues (FIFO – First In, First Out).

The stack should support four operations:
- `push(x)` – Insert an element.
- `pop()` – Remove and return the top element.
- `top()` – Return the top element.
- `empty()` – Check whether the stack is empty.

## Approach: Using Two Queues

I used two queues, `q1` and `q2`, to implement stack operations.

1. **Push:** Insert the new element into `q2`.
2. Move all elements from `q1` into `q2`.
3. Swap `q1` and `q2` so the newest element always stays at the front.
4. **Pop:** Remove and return the front element of `q1`.
5. **Top:** Return the front element without removing it.
6. **Empty:** Check whether `q1` is empty.

This approach maintains LIFO order using FIFO queues.

## Java Solution

```java
import java.util.Queue;
import java.util.LinkedList;

class MyStack {
    Queue<Integer> q1 = new LinkedList<>();
    Queue<Integer> q2 = new LinkedList<>();

    public MyStack() {
    }

    public void push(int x) {
        q2.offer(x);

        while (!q1.isEmpty()) {
            q2.offer(q1.poll());
        }

        Queue<Integer> temp = q1;
        q1 = q2;
        q2 = temp;
    }

    public int pop() {
        return q1.poll();
    }

    public int top() {
        return q1.peek();
    }

    public boolean empty() {
        return q1.isEmpty();
    }
}
```

## Complexity Analysis

| Operation | Time Complexity |
|---|---|
| Push | O(n) |
| Pop | O(1) |
| Top | O(1) |
| Empty | O(1) |

**Space Complexity:** O(n)

## What I Learned

- Difference between Stack (LIFO) and Queue (FIFO).
- How two queues can be used to implement stack behavior.
- How swapping queue references helps maintain the required order.
- How choosing a different approach can make some operations more efficient.

## Takeaway

Sometimes, solving a problem isn't about using a data structure in the usual way. It's about understanding its behavior and finding a way to make it work differently.

**Day 90 completed! One more concept understood, one more step forward.**
