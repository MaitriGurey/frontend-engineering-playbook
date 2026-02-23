# 🏗️ Frontend System Design

This section of the playbook is dedicated to architectural challenges. It contains a mix of real-world problems I've encountered in interviews and industry-standard patterns for building scalable web applications.

## 🧠 My Design Framework

When tackling these problems, I don't just jump into coding. I follow a structured approach to ensure all Senior-level concerns are met:

1.  **Requirement Clarification:** Defining functional (user-facing) and non-functional (performance, scale) goals.
2.  **State & Data Modeling:** Deciding between Normalized vs. Nested state and choosing the right sync strategy (SWR/React Query).
3.  **Component Architecture:** Designing for reusability using patterns like Composition and Higher-Order Components.
4.  **Performance & Optimization:** Addressing Core Web Vitals, Virtualization, and Code-Splitting.
5.  **Reliability:** Planning for error boundaries, offline support, and E2E testing.

---

## 📂 Featured Case Studies

| Problem                                                      | Key Focus Areas                                            | Level  |
| :----------------------------------------------------------- | :--------------------------------------------------------- | :----- |
| [**Generic Dashboard Filters**](./generic-dashboard-filters) | Config-driven UI, Cursor Pagination, Jotai vs. React Query | SDE 2  |
| [**Nested Comment System**](./nested-comments-thread)        | Recursive UI, State Normalization, Tree Traversal          | Senior |
| _More coming soon..._                                        | _Design Systems, Image Galleries, Real-time Chat..._       | --     |

---

## 🛠️ Global Principles I Follow

- **A11y First:** Every design must be keyboard navigable and screen-reader friendly.
- **Type Safety:** Using TypeScript to define strict API contracts and component interfaces.
- **Zero-Duplicate Data:** Prioritizing normalized state to avoid UI inconsistencies.
- **Lighthouse 90+:** Ensuring architectural choices (like SSR vs. CSR) favor performance metrics.

---

_This playbook is updated every time I encounter a new architectural challenge or learn a better way to solve an old one._
