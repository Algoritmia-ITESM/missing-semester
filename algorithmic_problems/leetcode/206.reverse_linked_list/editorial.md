# 206. Reverse Linked List — Editorial

**Problem.** Given the head of a singly linked list, reverse the list and return
the new head.

## Iterative (two-pointer) approach

Walk the list with `curr`, keeping `prev` as the already-reversed prefix.\
On each step, save `curr.next` in `nxt`, redirect `curr.next = prev`, then
advance both pointers.

**Correctness.** Every edge from the original list is reversed exactly once, and
`prev` always points to a correctly reversed prefix. When `curr` reaches `None`,
`prev` is the new head.

**Complexity.** Time `O(n)`, extra space `O(1)`.

## Recursive approach

Recurse to the tail; when the call stack unwinds, flip the pointer:
`head.next.next = head` and set `head.next = None` to avoid cycles.

**Correctness.** The recursive call returns the head of the reversed suffix.
Rewiring attaches `head` to the end of that suffix.

**Complexity.** Time `O(n)`, extra space `O(n)` due to recursion stack (Python
has no TCO).

**Notes.** Prefer the iterative version in Python for large lists to avoid
recursion depth limits.
