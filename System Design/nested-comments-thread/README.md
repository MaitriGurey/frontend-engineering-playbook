# 💬 System Design: Nested Comment / Reply System

**The Challenge:** Design and architect a high-performance, hierarchical comment system similar to Reddit or Hacker News. The system must support deep nesting, real-time-like interactions (voting, editing), and thread management (collapsing/expanding).

## 🎯 Requirements & Scope

### Functional Requirements

- **Hierarchy:** Support for infinite (or deeply nested) levels of replies.
- **Core Actions:** Users can create, edit, and delete comments.
- **Interactions:** Upvoting/Downvoting and collapsing/expanding entire threads.
- **Sorting:** Support for sorting by "Top" (votes), "New" (timestamp), and "Old".

### Non-Functional Requirements

- **Performance:** Ensure that voting or editing a single comment does not trigger a re-render of the entire 1,000+ comment thread.
- **Scalability:** Handle massive threads (e.g., AMA style) without crashing the browser DOM.
- **UX/Accessibility:** Maintain readable indentation on mobile (avoid the "Staircase Effect") and ensure keyboard navigability for thread collapsing.

---

## 🏗️ Technical Challenges to Solve

### 1. The Recursion Problem

Unlike a simple flat list, a comment thread is a **Tree**. We need to design a component that can render itself and handle state propagation across multiple levels of nesting.

### 2. State Management Strategy

Should the data be stored as a deeply nested object or a flat, normalized map?

- **Nested:** Easier for initial render, but $O(N)$ updates.
- **Normalized:** More complex to "rehydrate" but $O(1)$ updates—crucial for SDE 2 performance standards.

### 3. DOM Bloat

Deeply nested threads can lead to thousands of DOM nodes. We need to explore strategies like **Virtualization** and **Thread Flattening** to keep the browser responsive.

---

## 🚀 Key Learning Points in this Module

- Implementation of **Recursive Components** in React.
- Deep dive into **State Normalization** using the ID-to-Object pattern.
- Optimization techniques using `React.memo` and `useCallback`.
- Handling "Deleted" states while preserving tree structure.

---
